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
>  **provider = hashicorp-http**
>  #...
> }
>
> ```


  
No bloco **provider** é onde se configura o nome local do provedor do recurso criado, isto é, quem é responsável por criar e gerenciar os recursos. O **provider** é um plugin que o Terraform usa para "traduzir" as interações da API com o serviço, sendo responsável por entender as interações e expor recursos.  
Pela versatilidade em interagir com quaisquer API's, é possível representar praticamente todo tipo de infraestrutura ou serviço como um recurso no Terraform. Por isso, é possível configurar múltiplos blocos de **provider** para utilizar recursos de provedores diferentes na mesma pipeline.  
Para configurar o **provider**, é necessário informar alguns parâmetros:  
- O *profile* é um atributo que define quais são as credenciais que serão usadas para a interação com o **provider**. No caso da AWS, o profile 'default' usa as credenciais armazenadas no arquivo %USERPROFILE%/.aws/credentials (criado no momento da configuração do CLI em caso de operações locais), ou usa as credenciais IAM do perfil da instância (em caso de operações na AWS).  
- A *region* é um atributo que define de/em qual região serão feitas as operações nos recursos.  
  
No bloco **resource** é onde se define o tipo de recurso que se deseja criar e qual será o seu nome de referência. O **resource** pode ser qualquer componente de infraestrutura (físico ou lógico) oferecido pelo provider e suportado pelo Terraform.  
No primeiro exemplo do bloco acima, o tipo de recurso é uma instância aws (aws_instance) cujo nome será "exemplo-ec2". O prefixo contido no tipo do recurso é um mapeamento para o provider que criará o recurso (o tipo aws_instance informa ao Terraform que o provider usado é o "aws").  
Para configurar corretamente os atributos necessários para a criação de cada recurso específico é necessário consultar a documentação dos providers. No exemplo usado, configurou-se a *ami* (Amazon Machine Image como Ubuntu) e o *instance_type* (t2.micro).  
  
---

## Informações sobre providers

A página [Terraform Registry](https://registry.terraform.io/), em *Browse Providers*, contém a relação de todos os providers suportados pelo Terraform: os desenvolvidos e mantidos pela Hashicorp; os verificados e os desenvolvidos pela comunidade.  
Nesta mesma página, em *Browse Modules*, é possível encontrar módulos prontos para a criação de recursos com configurações específicas.  

---

## Etapas da criação do recurso com Terraform

*terraform plan*  
- 
One of the stages of a run, in which Terraform compares the managed infrastructure's real state to the configuration and variables, determines which changes are necessary to make the real state match the desired state, and presents a human-readable summary to the user. The counterpart of an apply.

In Terraform's CLI, plans are performed by all of the following commands:

terraform plan, which only performs a plan. It can optionally output a plan file, which terraform apply can use to perform that exact set of planned changes.
terraform apply, which performs a plan and then, if a user approves, immediately applies it.
terraform destroy, which is similar to terraform apply but uses a desired state in which none of the managed resources exist; if the plan is approved, those resources are destroyed.
In Terraform Cloud, plans are performed by committing changes to a workspace's configuration, running terraform plan or terraform apply with the remote backend enabled, manually queueing a plan, or uploading a configuration via the API.

Terraform Cloud's workflow always creates a plan file, which can be auto-applied or can wait for a user's approval. Terraform Cloud also supports speculative plans, which are for informational purposes only and cannot be applied.
