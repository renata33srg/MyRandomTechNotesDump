# Terraform

## Estrutura do template

<details>
<summary> Exemplo da criação de uma EC2 </summary>
  
```yaml
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
  
```yaml
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

No bloco **provider** é onde se configura o nome do provedor do recurso criado, isto é, quem é responsável por criar e gerenciar os recursos. O **provider** é um plugin que o Terraform usa para "traduzir" as interações da API com o serviço, sendo responsável por entender as interações e expor recursos.  
Pela versatilidade em interagir com quaisquer API's, é possível representar praticamente todo tipo de infraestrutura ou serviço como um recurso no Terraform. Por isso, é possível configurar múltiplos blocos de **provider** para utilizar recursos de provedores diferentes na mesma pipeline.  
Para configurar o **provider**, é necessário informar alguns parâmetros:  
- O *profile* é um atributo que define quais são as credenciais que serão usadas para a interação com o **provider**. No caso da AWS, o profile 'default' usa as credenciais armazenadas no arquivo %USERPROFILE%/.aws/credentials (criado no momento da configuração do CLI em caso de operações locais), ou usa as credenciais IAM do perfil da instância (em caso de operações na AWS).  
- A *region* é um atributo que define de/em qual região serão feitas as operações nos recursos.  
  
No bloco **resource** é onde se define o tipo de recurso que se deseja criar e qual será o seu nome de referência. O **resource** pode ser qualquer componente de infraestrutura (físico ou lógico) oferecido pelo provider e suportado pelo Terraform.  
No primeiro exemplo do bloco acima, o tipo de recurso é uma instância aws (aws_instance) cujo nome será "exemplo-ec2". O prefixo contido no tipo do recurso é um mapeamento para o provider que criará o recurso (o tipo aws_instance informa ao Terraform que o provider usado é o "aws").  
Para configurar corretamente os atributos necessários para a criação de cada recurso específico é necessário consultar a documentação dos providers. No exemplo usado, configurou-se a *ami* (Amazon Machine Image como Ubuntu) e o *instance_type* (t2.micro).  
  
 
  
