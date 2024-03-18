# app-py-postgres-k8s
Laboratório criado com o intuito de praticar e aprimorar habilidades em Kubernetes

### Introdução
O projeto visa subir uma aplicação em Python integrada a um banco de dados PostgreSQL.  Utilizando containers para garantir uma infraestrutura escalável e eficiente, <br/>um container dedicado para o banco de dados e outro para a aplicação, e estabelecer comunicação entre eles.
<br/>Utilizando o Kubernetes, que atuará como orquestrador, gerenciando e coordenando os contêineres de forma automatizada e confiável.

### Requisitos
* Possuir o docker e o minikube instalado;

### Processo 
1. Baixar imagens oficiais do python e do postgres;
2. Realizar a customização das imagens
3. Criar o NameSpace do postgres
4. Configurar NÓ do banco de dados (no NameSpace Postgres)<br/>
    a. Criar e configurar o arquivo de configuração de variáveis de ambiente do postgres (pg-configmap.yaml)<br/>
    b. Criar e configurar o arquivo de deployment, responsável pela criação do container do postgres (pg-deployment.yaml)<br/>
    c. Criar e configurar o arquivo de service do tipo load balancer, responsável por expor a porta e o serviço do postgres (pg-deployment.yaml)<br/>
5. Configurar NÓ da aplicação (no NameSpace Default)<br/>
    a. Criar e configurar o arquivo de deployment, responsável pela criação do container da aplicação (app-deployment.yaml)<br/>
    b. Criar e configurar o arquivo de service do tipo load balancer, responsável por expor a porta da aplicação (pg-deployment.yaml)<br/>
6. Aplicar arquivos yaml com o kubectl, para colocar postgres no ar<br/>
    a. kubectl apply -f pg-configmap.yaml -n postgres → Carregar as variáveis de ambiente no NameSpace do postgres<br/>
    b. kubectl apply -f pg-deployment.yaml -n postgres  → Subir POD do Banco de Dados no NameSpace do postgres<br/>
    c. kubectl apply -f pg-service.yaml -n postgres  → Subir service do BD no NameSpace do postgres<br/>
7. Aplicar arquivos yaml com o kubectl, para colocar aplicação python no ar<br/>
    a. kubectl apply -f app-service.yaml → Subir o service da aplicação<br/>
    b. kubectl apply -f app-service.yaml → Subir o POD da aplicação<br/>
8. Verificar se subiu POD do BD → kubectl get pods -n postgres<br/>
9. Verificar se subiu service do BD → kubectl get services -n postgres
10. Testar conexão via telnet com ip do minikube e porta da aplicação
11. Abrir aplicação no navegador utilizando ip do minikube e porta da aplicação

### Resultado (Aplicação no ar!!!)
![ app-py](.\image\app-py.png )