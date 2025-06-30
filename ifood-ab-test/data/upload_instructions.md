# 🧭 Instruções para Acessar o Databricks Community Edition e Executar o Projeto

Este guia detalha o passo a passo para rodar o projeto `iFood A/B Test` usando o Databricks Community Edition (gratuito).

---

## 📥 Baixar e Preparar os Arquivos de Dados

Antes de fazer o upload no Databricks, é necessário **baixar os arquivos brutos e descompactá-los**. Abaixo estão os links para download e os comandos necessários.

### 🔗 Links de Download

- **Usuários (`consumer.csv`)**  
  https://data-architect-test-source.s3-sa-east-1.amazonaws.com/consumer.csv.gz

- **Restaurantes (`restaurant.csv`)**  
  https://data-architect-test-source.s3-sa-east-1.amazonaws.com/restaurant.csv.gz

- **Participantes do Teste A/B (`ab_test_ref.csv`)**  
  https://data-architect-test-source.s3-sa-east-1.amazonaws.com/ab_test_ref.tar.gz

### 🗜️ Comandos para descompactar

Após baixar os arquivos, execute os seguintes comandos no terminal (Linux, Mac ou WSL):

```bash
gzip -d consumer.csv.gz
gzip -d restaurant.csv.gz
tar -zxvf ab_test_ref.tar.gz

## 1️⃣ Criar Conta no Databricks Community

1. Acesse: [https://community.cloud.databricks.com](https://community.cloud.databricks.com)
2. Clique em **Sign Up** e crie sua conta gratuita

---

## 2️⃣ Criar um Cluster

1. Vá ao menu lateral esquerdo e clique em **Compute**
2. Clique em **Create Cluster**
3. Dê um nome para o cluster (ex: `ifood-cluster`)
4. Selecione:
   - **Single Node**
   - **Databricks Runtime Version**: escolha `11.x LTS (Scala 2.12, Spark 3.x)` ou superior
5. Clique em **Create Cluster**

> ⚠️ Aguarde o cluster ser iniciado (ícone verde)

---

## 3️⃣ Fazer Upload dos Dados

1. No menu lateral, clique em **Data** > **Create** > **Upload File**
**OBS: Necessário descompactar `files.zip` antes de enviar para upload**
2. Clique em `Browse` e selecione os arquivos abaixo (baixados dessa mesma pasta -> data/):

   - `consumer.csv.gz`
   - `restaurant.csv.gz`
   - `ab_test_ref.csv.gz`

3. Em "Destination", use o seguinte diretório já criado anteriormente:

`/Volumes/workspace/default/ifood_data/`

4. Clique em **Upload**

---

## 4️⃣ Importar o Notebook

1. Vá até o menu lateral esquerdo: **Workspace**
2. Clique com o botão direito sobre seu nome ou diretório, e selecione **Import**
3. Escolha o arquivo `ifood_ab_test_analysis.dbc` (da pasta `notebooks/` do repositório)
4. Após importar, clique no notebook para abrir

---

## 5️⃣ Executar o Notebook

1. Conecte ao cluster (ícone de corrente no topo)
2. Clique em **Run All** ou rode célula por célula
3. Perceba que uma das células cria um parquet a partir de um arquivo de dados, e com isso criará em 
`/Volumes/workspace/default/ifood_data/` uma pasta chamada `df.parquet`.
---

## 📁 Estrutura Esperada de Arquivos no Databricks

```
/Volumes/workspace/default/ifood_data/
│
├── df.parquet/
├── consumer.csv
├── restaurant.csv
└── ab_test_ref.csv


---


/Workspace/Users/<seu-email>/ifood/
│
└── ifood-data-analysis-test

```

📌 Em caso de dúvidas, consulte a documentação oficial:  
[https://docs.databricks.com/en/](https://docs.databricks.com/en/)
