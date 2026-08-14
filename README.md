IaC Labs — Terraform + AWS





Laboratório prático de Infraestrutura como Código (IaC) criado para estudar Terraform, automação e provisionamento de recursos na AWS.

O repositório faz parte do meu desenvolvimento profissional em Cloud e DevOps e registra, de forma prática e evolutiva, os conceitos aprendidos.

Arquitetura atual

A configuração atual provisiona:

Recurso

Configuração

Provedor

AWS

Região

us-east-1

Recurso Terraform

aws_vpc.main

Bloco CIDR

10.0.0.0/16

Nome da VPC

vinicius-vpc

Neste estágio, o projeto cria somente a VPC. Sub-redes, gateways, tabelas de rotas e outros componentes ainda não fazem parte da infraestrutura.

Pré-requisitos

Antes de executar o projeto, tenha instalado e configurado:

Terraform;

AWS CLI;

uma conta AWS;

credenciais com permissão para criar e remover VPCs.

Verifique a autenticação na AWS:

aws sts get-caller-identity

Como executar

1. Clonar o repositório

git clone https://github.com/vns-brit0/iac-labs.git
cd iac-labs

2. Inicializar o Terraform

terraform init

3. Padronizar e validar o código

terraform fmt
terraform validate

4. Revisar o plano de execução

terraform plan

Confira os recursos que serão criados antes de continuar.

5. Criar a infraestrutura

terraform apply

Digite yes quando o Terraform solicitar a confirmação.

6. Confirmar a criação

Após a execução, acesse o Console da AWS e consulte:

VPC > Your VPCs

A VPC deverá aparecer com o nome vinicius-vpc.

Destruição do ambiente

Para remover os recursos provisionados pelo projeto:

terraform destroy

Revise o plano de destruição e confirme somente se os recursos puderem ser excluídos.

Estrutura do repositório

iac-labs/
├── .gitignore    # Arquivos locais ignorados pelo Git
├── Comentários   # Registro inicial sobre o projeto
├── main.tf       # Provedor AWS e definição da VPC
└── README.md     # Documentação do laboratório

Boas práticas adotadas

infraestrutura versionada com Git;

estado local do Terraform fora do repositório;

separação entre código e credenciais;

validação do código antes do provisionamento;

destruição controlada dos recursos do laboratório.

Nunca armazene chaves de acesso, segredos ou arquivos de estado do Terraform no GitHub. Prefira credenciais temporárias ou AWS IAM Identity Center (SSO).

Próximos passos

Definir versões mínimas do Terraform e do provedor AWS;

criar sub-redes públicas e privadas;

adicionar Internet Gateway e tabelas de rotas;

criar Security Groups;

parametrizar região, CIDR e nomes com variáveis;

adicionar outputs;

configurar backend remoto com Amazon S3 e mecanismo de bloqueio de estado;

organizar a infraestrutura em módulos reutilizáveis;

implementar validações automatizadas em um pipeline de CI/CD.

Autor

Vinicius Brito
Analista de Infraestrutura | Cloud AWS & Azure

LinkedIn · GitHub

Este é um projeto de estudo. Avalie permissões, segurança e custos antes de reutilizá-lo em ambientes de produção.
