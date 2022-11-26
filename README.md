# airbyte-dbt-airflow-snowflake-metabase

Repositório para armazenar os artefatos do Pipeline utilizando Modern Data Stack com AirByte + DBT + Airflow + SnowFlake + Metabase


## Infraestrutura

- Setup do ambiente de desenvolvimento
- Subir o Airbyte via docker
- Subir o Airflow via docker
- Subir o Metabase via docker
- Criar o script de execução
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