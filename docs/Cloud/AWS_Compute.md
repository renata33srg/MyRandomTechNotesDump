# AWS Compute

## AWS EKS

É um serviço gerenciado que permite a execução e o gerenciamento de clusters do Kubernetes na infraestrutura da AWS.  
Um cluster EKS deve ser criado dentro de uma VPC para que seja possível utilizar a API do Kubernetes para gerenciar as aplicações conteineirizadas. A partir disso, deve-se criar os *node groups*, que são grupos de instâncias EC2 que vão rodar os workers do Kubernetes. Estes grupos podem ser escalados verticalmente de acordo com os requerimentos do workload.   
Uma vez que estejam rodando nos node groups, os workers são registrados junto com cluster do EKS e vão executar os componentes do Kubernetes responsáveis por gerenciar os contêineres e seus workloads.  


Control Plane: EKS manages the Kubernetes control plane, which includes the API server, etcd data store, and other components that are responsible for managing the Kubernetes cluster.

Application Deployment: Finally, users can use Kubernetes APIs to deploy their containerized applications to the EKS cluster. They can use Kubernetes features such as replica sets, deployments, and services to manage their applications, and EKS will ensure that the applications are running on the correct nodes and are highly available.

Overall, AWS EKS provides a managed Kubernetes service that simplifies the deployment and management of containerized applications on AWS infrastructure.