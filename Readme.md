## Projeto inicial para um primeiro contato com o AWS SAM

Estamos nos aventurando pelo mundo do AWS_SAM por demanda do Labs42_jan23 em parceria com o Itaú.
Projeto feito pela equipe: Welton (wleite), Gabriel (gissao-m) e Maria Clara (maclara-).

### Vamos subir um projeto local usando o AWS SAMlocal

Para isso:
Tenha o docker desktop instalado e aberto

No workspace, inicie o container:
`localstack start -d`

### Passo a passo para a inicialização do Hello_World

Para iniciar um projeto no AWS SAMlocal:
`samlocal init`

Escolhemos usar os templates semi-prontos, para fins didáticos:
`Choice: 1 - AWS Quick Start Templates`

Usaremos um template pronto:
`Template: 1 - Hello World Example `

Não queremos que o projeto seja na versão mais atual do python
`Use the most popular runtime and package type? (Python and zip) [y/N]: N`

Escolha a versão do python que você tem instalada
`Runtime: 16`

Queremos usar o zip:
`Package type: 1`

Como é um projeto simples para teste escolheremos o NÃO:
`Would you like to enable X-Ray tracing on the function(s) in your application?  [y/N]: N`

Como é um projeto simples para teste escolheremos o NÃO:
`Would you like to enable monitoring using CloudWatch Application Insights? For more info, please view https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch-application-insights.html [y/N]: N`

Dê um nome ao seu projeto:
`Project name [sam-app]: Hello_World`


### Entre na pasta do projeto Hello_World

`cd Hello_World`

Agora compile o projeto
`samlocal build`

### Passo a passo para subir o projeto na AWS 
(lembre-se que estamos usando tudo localmente)

Para subir a aplicação, podendo configurar os detalhes
`samlocal deploy --guided`

escolha o nome do projeto, se quiser usar o que já está aí, clique ENTER
`Stack Name [Hello_World]: ENTER`

Para funcionar, você deve usar a região "us-east-1": 
`AWS Region []:  us-east-1`

Como é um projeto para teste podemos deixar como NÃO
`Confirm changes before deploy [Y/n]: N`

Mantenha como está
` Allow SAM CLI IAM role creation [Y/n]:  Y`

Mantenha como está
`Disable rollback [y/N]: N`

Marque como YES
` HelloWorldFunction may not have authorization defined, Is this okay? [y/N]: Y`

Mantenha como está
`Save arguments to configuration file [Y/n]: Y`

Mantenha como está
`SAM configuration file [samconfig.toml]: : ENTER`

Mantenha como está
`SAM configuration environment [default]: ENTER`

#### Espere um momento que seu projeto será criado

........ waiting.........


### Para acessar seu projeto

<p>
CloudFormation outputs from deployed stack
-------------------------------------------------------------------------------------------------------------------
Outputs                                                                                                            
-------------------------------------------------------------------------------------------------------------------
Key                 HelloWorldApi                                                                                               
Description         API Gateway endpoint URL for Prod stage for Hello World function                                            
Value               https://x82e1x8xt5.execute-api.amazonaws.com:4566/Prod/hello/    <--------------

Key                 HelloWorldFunction                                                                                          
Description         Hello World Lambda Function ARN                                                                             
Value               arn:aws:lambda:us-east-1:000000000000:function:Hello_World-HelloWorldFunction-ed93d0c1               

Key                 HelloWorldFunctionIamRole                                                                                   
Description         Implicit IAM Role created for Hello World function                                                          
Value               arn:aws:iam::000000000000:role/Hello_World-HelloWorldFunctionRole-4aaa64bc  
--------------------------------------------------------------------------------------------------------------
<p>


MODIFIQUE ESSE LINK
`https://x82e1x8xt5.execute-api.amazonaws.com:4566/Prod/hello/ `

trocando `amazonaws.com` por `localhost.localstack.cloud`

DE MODO QUE FIQUE ASSIM
`https://x82e1x8xt5.execute-api.localhost.localstack.cloud:4566/Prod/hello/`


Você verá
<p>
{"message": "hello world"}
<p>

#### Seu primeiro projeto na AWS SAM foi realizado com sucesso !!!

ps: o tutorial da Rafaela (rabustam) está bem mais completo:
https://github.dev/rafaelabdm/localstack-tutorial/blob/main/README.md