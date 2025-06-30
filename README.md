# 📊 iFood A/B Test Analysis on Databricks (Community Edition)

Este repositório contém um notebook Databricks que analisa os resultados de um experimento A/B com cupons no iFood (para fins de avaliação de desafio), utilizando dados fornecidos e processamento com PySpark.

---

## 📁 Estrutura do Repositório:
```
/ifood-ab-test/
│
│ └──notebooks/
│    └── ifood-data-analysis-test.dbc # Notebook exportado do Databricks
│    └── ifood-data-analysis-test.ipynb #Notebook separado apenas como bkp
│
│ └── data/
|    └── upload_instructions.md # Instruções de upload/baixar os arquivos dos dados e dar upload no Databrics Community
|    └── tabela_final.xlsx # Tabela final citada em "relatorio.pdf"
│
│ └──relatorio.pdf # Relatório com análises e conclusões
|
├── README.md # Este arquivo
```

## 🧾 Dados Utilizados

Os dados vêm dos seguintes arquivos públicos:

- `order.json.gz` => `df.parquet/`: dados de pedidos
- `consumer.csv.gz`: dados de usuários  
- `restaurant.csv.gz`: dados de restaurantes  
- `ab_test_ref.csv.gz`: marcação de grupos de teste e controle  

> Todos devem ser enviados para a pasta `/Volumes/workspace/default/ifood_data/` dentro do Databricks.

---

## 🚀 Como Executar no Databricks Community Edition

1. Acesse: https://community.cloud.databricks.com/  
2. Crie uma conta gratuita (se ainda não tiver)  
3. No menu lateral, clique em `Workspace > Import` e envie o notebook `.dbc` contido na pasta `notebooks/`  
4. Crie um cluster:
   - Tipo: `Single Node`
   - Runtime: `Databricks Runtime 11.x` ou superior  
5. Vá até `Data > Create > Upload file` e envie os 4 arquivos para a pasta:
`/Volumes/workspace/default/ifood_data/`
6.  Execute o notebook célula por célula.

---
 
## 📊 Análises Realizadas

- Análise de retenção de usuários por grupo
- Tempo médio até o segundo pedido
- Ticket médio por grupo (target vs control)
- ROI da campanha de cupons
- ROI segmentado por frequência de pedidos e ticket médio
- Heatmaps para análise visual de impacto por segmento
- Visualizações com `matplotlib` e `seaborn`

---


## ✍️ Autoria
Projeto desenvolvido por @ncezar como estudo de A/B Testing, segmentação de usuários e análise de ROI com PySpark e Databricks.
