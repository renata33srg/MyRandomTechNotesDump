# Terraform

## Estrutura do template

<details>
<summary> Exemplo da criação de uma EC2 </summary>
  
```ruby

provider "aws" {
  profile = "default"
  region  = "sa-east-1"
}

resource "aws_instance" "exemplo-ec2" {
  ami           = "ami-12345678"
  instance_type = "t2.micro"
}
```
    
</details>

<details>
<summary> Exemplo da criação de uma VPC</summary>
  
```ruby
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 1.0.4"
    }
  }
}

# Bloco de definição das variáveis
variable "aws_region" {}

variable "base_cidr_block" {
  description = "A /16 CIDR range definition, such as 10.1.0.0/16, that the VPC will use"
  default = "10.1.0.0/16"
}

variable "availability_zones" {
  description = "A list of availability zones in which to create subnets"
  type = list(string)
}

provider "aws" {
  region = var.aws_region
}

resource "aws_vpc" "main" {
  # Referencing the base_cidr_block variable allows the network address
  # to be changed without modifying the configuration.
  cidr_block = var.base_cidr_block
}

resource "aws_subnet" "az" {
  # Create one subnet for each given availability zone.
  count = length(var.availability_zones)

  # For each subnet, use one of the specified availability zones.
  availability_zone = var.availability_zones[count.index]

  # By referencing the aws_vpc.main object, Terraform knows that the subnet
  # must be created only after the VPC is created.
  vpc_id = aws_vpc.main.id

  # Built-in functions and operators can be used for simple transformations of
  # values, such as computing a subnet address. Here we create a /20 prefix for
  # each subnet, using consecutive addresses for each availability zone,
  # such as 10.1.16.0/20 .
  cidr_block = cidrsubnet(aws_vpc.main.cidr_block, 4, count.index+1)
}
```
    
</details>


Todo módulo do Terraform deve, obrigatoriamente, definir um bloco de **required_providers**, que é onde se declara a origem dos providers que serão instalados e utilizados no template. Para configurar o **required_providers**, é necessário informar três parâmetros:  
- O *local_name* é o identificador único do provider dentro do módulo e será usado posteriormente na configuração específica dentro do bloco **provider**  
- O *source* é o endereço de origem global do provider que se deseja usar (exemplo: hashicorp/aws)  
- A *version* é uma restrição para especificar com qual subconjunto de versões disponíveis do provider o módulo será compatível  
  
> Observação  
> Pode-se escolher qualquer nome para o identificador único do provider, porém, cada provider tem um *local_name* preferencial, que é utilizado como prefixo para todos os tipos de recursos associados a ele (exemplo: todos os recursos do provider hashicorp/aws começam com o prefixo `aws`, como aws_instance ou aws_security_group).  
> Sempre que possível, deve-se utilizar o *local_name* preferencial, pois torna a configuração mais legível e permite ocultar meta-informações do provider na maioria dos recursos (se um recurso não específica qual configuração de provider utilizar, o Terraform interpreta a primeira palavra do tipo do recurso como o *local_name* do provider)  
>
>  Em caso de conflito de nomes de providers, é possível criar nomes locais compostos e incluir a referência no recurso desejado. Exemplo:  
>  ```ruby
>  terraform {
>  required_providers {
>    # In the rare situation of using two providers that have the same type name "http" in this example use a compound local name to distinguish them.
>    hashicorp-http = {
>      source  = "hashicorp/http"
>      version = "~> 2.0"
>    }
>    mycorp-http = {
>      source  = "mycorp/http"
>      version = "~> 1.0"
>    }
>  }
>}
>
> # References to these providers elsewhere in the module will use these compound local names.
> provider "mycorp-http" {
>  # ...
> }
>
> data "http" "example" {
>  provider = hashicorp-http
>  #...
> }
>
> ```


  
No bloco **provider** é onde se configura o nome local do provedor do recurso criado, isto é, quem é responsável por criar e gerenciar os recursos. O **provider** é um plugin que o Terraform usa para "traduzir" as interações da API com o serviço, sendo responsável por entender as interações e expor recursos.  
Pela versatilidade em interagir com quaisquer API's, é possível representar praticamente todo tipo de infraestrutura ou serviço como um recurso no Terraform. Por isso, é possível configurar múltiplos blocos de **provider** para utilizar recursos de provedores diferentes na mesma pipeline.  
Para configurar a AWS como **provider**, é necessário informar alguns parâmetros:  
- O *profile* é um atributo que define quais são as credenciais que serão usadas para a interação com o **provider**. No caso da AWS, o profile 'default' usa as credenciais armazenadas no arquivo %USERPROFILE%/.aws/credentials (criado no momento da configuração do CLI em caso de operações locais), ou usa as credenciais IAM do perfil da instância (em caso de operações na AWS).  
- A *region* é um atributo que define de/em qual região serão feitas as operações nos recursos.  

>
> Para utilizar o mesmo provider com configurações diferentes (com especificidades para cada recurso), é possível utilizar um meta-argumento opcional chamado *alias*. > 
> Exemplo:  
> ```ruby
> # The default provider configuration; resources that begin with `aws_` will use it as the default, and it can be referenced as `aws`.
> provider "aws" {
>  region = "us-east-1"
> }
>  
> # Additional provider configuration for west coast region; resources can reference this as `aws.west`.
> provider "aws" {
>  alias  = "west"
>  region = "us-west-2"
> }
>  
>  
> resource "aws_instance" "foo" {
>  provider = aws.west
>  # ...
> }
>
> ```
  
No bloco **resource** é onde se define o tipo de recurso que se deseja criar e qual será o seu nome de referência. O **resource** pode ser qualquer componente de infraestrutura (físico ou lógico) oferecido pelo provider e suportado pelo Terraform.  
No primeiro exemplo do bloco acima, o tipo de recurso é uma instância aws (aws_instance) cujo nome será "exemplo-ec2". O prefixo contido no tipo do recurso é um mapeamento para o provider que criará o recurso (o tipo aws_instance informa ao Terraform que o provider usado é o "aws").  
Para configurar corretamente os atributos necessários para a criação de cada recurso específico é necessário consultar a documentação dos providers. No exemplo usado, configurou-se a *ami* (Amazon Machine Image como Ubuntu) e o *instance_type* (t2.micro).  
  
---

## Informações sobre providers

A página [Terraform Registry](https://registry.terraform.io/), em *Browse Providers*, contém a relação de todos os providers suportados pelo Terraform: os desenvolvidos e mantidos pela Hashicorp; os verificados e os desenvolvidos pela comunidade.  
Nesta mesma página, em *Browse Modules*, é possível encontrar módulos prontos para a criação de recursos com configurações específicas.  

---

## Ciclo de gerenciamento de recurso (básico)  
  
Para realizar o gerenciamento de recursos, a pipeline segue alguns passos para comparar o estado atual das configurações/variáveis da infraestrutura e determinar quais alterações são necessárias para que o estado atual corresponda ao estado desejado (alterações feitas no template).  
  
   *terraform plan*   
>    - Lê o estado atual de quaisquer objetos pré-existentes no Terraform para garantir que o plano está atualizado (não está `stale`);  
>    - Compara a configuração atual no template com o estado prévio dos recursos, registrando qualquer diferença encontrada;  
>    - Propõe um conjunto de alterações que, se aplicadas, farão que os recursos correspondam à configuração sugerida.  
>      
>   Esse comando sozinho não aplicará as alterações propostas, servindo somente para checar se o que foi alterado corresponde ao que era esperado.  
>   Se o Terraform detectar que não há necessidade de alterações nos recursos ou valores de saída, o comando reportará que nenhuma ação precisa ser tomada.   
>   
  
   *terraform apply*   
>    - Executa as alterações propostas no plano criado no comando `terraform plan` (se não existir nenhum plano criado/salvo, o apply cria o seu próprio plano).  
>    - Dependendo da forma como está configurado, pode pedir aprovação manual do usuário.  

   *terraform destroy* (opcional)  
>    - Faz a exclusão de recursos temporários criados para fins de desenvolvimento (ephemeral infrastructure).   
