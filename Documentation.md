# Documentação do projeto realizado usando a Modern Data Stack

Repositório para armazenar os artefatos do pipeline utilizando AirByte + DBT + Airflow + SnowFlake + Metabase.


## Infraestrutura

- Criação de um gmail para o projeto (https://accounts.google.com/signup)

- Setup do ambiente de desenvolvimento utilizando o Gitpod (https://gitpod.io)

- Setar as permissões do Gitpod ao repositório no Github (https://gitpod.io/integrations)

- Subir o Airbyte via docker compose seguindo a doc - https://docs.airbyte.com/quickstart/deploy-airbyte/ (Realizar fork no repositório original para o meu repo, para poder fazer as alterações necessárias e depois criar uma branch para esse projeto em específico para que as modificações não alterem a branch master e consequetemente, a mesma poderá continuar recebendo atualizações. Após isso, realizar git clone do meu repositório. Fazer "git clone -b modern-data-stack https://github.com/mferreiracosta/airbyte.git". Depois de clonar para o ambiente de dev, retirar o user e senha do .env e entrar na pasta com "cd airbyte" e fazer "docker-compose up")

- Subir o Airflow via docker compose seguindo a doc - https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html (Criar uma pasta no ambiente de dev chamada "airflow" usando mkdir, entrar na mesma com "cd airflow" e fazer download dos arquivos usando "curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.5.1/docker-compose.yaml'". Finalizado o download dos arquivos, setar os seguintes comandos: "mkdir -p ./dags ./logs ./plugins
echo -e "AIRFLOW_UID=$(id -u)" > .env". Agora, usar o comando "docker compose up airflow-init". O user e password são "airflow")

- Criar o arquivo ".gitignore" dentro da pasta airflow. Qualquer coisa que colocar dentro desse arquivo será ignorado e não será levado para o repositório no Github. No primeiro momento iremos ignorar todos arquivos de logs gerados fazendo "logs/*". Após isso, fazer commit e sincronizar.

- Subir o Metabase via docker compose seguindo o seguinte script - https://gist.github.com/eliashussary/379e44a99e2389bd6a8ea6a23c2d5af8 (Cria um diretório metabase e arquivo docker-compose.yaml, dentro desse arquivo remove o postgres e da linha environment para baixo, pois usaremos o snowflake, e altera a porta para 3000. Após isso "cd metabase" e docker-compose up")

- Criar uma conta teste no Snowflake usando o gmail criado no primeiro passo

- Criar o script de execução - script linux para subir containers automaticamente - setup.sh - comando "chmod 777 setup.sh" para transformar o arquivo em executável

- Testar a Execução

### Etapas do Projeto

#### Ambiente de Desenvolvimento:

    - Criar conta no Gitpod utilizando o Github
    - Criar um workspace utilizando o repositório do projeto no Github
    - Setar as permissões do Gitpod ao repositório no Github


#### Banco de Dados DW - Snowflake:
   
    - Criar a Conta no SnowFlake
    - Verificar a existência das tabelas
    - Obter os links de conexão e nome da conta


#### Integração de Dados - Airbyte:

- Extração:

    - Conectar com as origens baseadas nos Csvs
    - Criar as entidades no snowflake através do script base da documentação
    - Conectar o destino no snowflake
    - Criar as conexões do airbyte associando as origens ao destino
    - Testar as conexões


- Preparação (Destination Loading Method):

    - Local Staging (Ambiente de Desenvolvimento)
    - Cloud Staging (Ambiente de Produção)


#### Dbt

- Transformação (Modelagem dos Dados):

    - Criação da Conta
    - Conexão com o Github
    - Criação do Dbt Project
    - Criação do Profile de conexão com o snowflake
    - Criação do Schema
    - Criação dos Modelos Base
    - Criação do Modelo Relacionado
    - Visualização gráfica do modelo
    - Teste de execução
    - Commits, Branches, Pull Requests, Merges no Github
    - Obtenção do link de conexão com o Airbyte


#### Ferramenta de Visualização - Metabase

- Dashboard:

    - Conectar Metabase com o Snowflake 
    - Criar uma Question  
    - Criar um Dashboard 
    - Adicionar uma Question 
    - Visualizar o Resultado  


#### Airflow:

- Orquestração:

    - Criar a dag  
    - Criar a Docker network
    - Incluir nos composes a network criada
    - Setup Up no serviço
    - Testar a conexao entre os containers do airflow e do airbyte
    - Criar as conexões com o Airbyte através do script  
    - Testar a execução do pipeline