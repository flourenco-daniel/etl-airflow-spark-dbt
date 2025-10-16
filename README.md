# ☁️ OpenWeather ETL: Dados Climáticos com Airflow, Spark e dbt 📊

Este projeto implementa um pipeline de **ETL (Extract, Transform, Load)** para coletar dados climáticos da **OpenWeather API**, processá-los e disponibilizá-los para análise. A arquitetura utiliza ferramentas modernas de engenharia de dados para garantir **escalabilidade, confiabilidade e baixo custo** na nuvem.

## 🎯 Objetivo do Projeto

O principal objetivo é demonstrar a construção de um Data Lakehouse simplificado, transformando dados brutos de uma API em insights de negócio acionáveis, utilizando as melhores práticas do mercado.

## 🚀 Arquitetura e Fluxo de Dados

O pipeline é dividido em camadas lógicas, orquestradas pelo Apache Airflow:

1.  **Extração (Raw Layer):**
    *   **Fonte:** OpenWeather API (One Call API).
    *   **Ferramentas:** Python (`requests`, `boto3`).
    *   **Armazenamento:** Amazon S3.
    *   **Formato:** JSON bruto, timestampado e imutável, servindo como a "fonte da verdade" para auditoria e reprocessamento.

2.  **Transformação (Staging Layer):**
    *   **Ferramentas:** Apache Spark (PySpark).
    *   **Processo:** Lê os JSONs da camada Raw, "achata" estruturas aninhadas (arrays e structs), normaliza tipos de dados e aplica transformações básicas.
    *   **Armazenamento:** Amazon S3.
    *   **Formato:** Parquet particionado, otimizado para performance e custo em consultas analíticas.

3.  **Modelagem de Negócio (Analytics/Curated Layer):**
    *   **Ferramentas:** dbt (data build tool) e Amazon Athena.
    *   **Processo:** Constrói modelos de dados SQL sobre as tabelas do Staging (via Athena), criando KPIs, agregações e tabelas prontas para consumo de negócio. Garante qualidade e governança dos dados.
    *   **Armazenamento:** Amazon S3 (tabelas lógicas no Athena).
    *   **Formato:** Parquet particionado, com esquema de negócio claro e documentado.

4.  **Consumo (Business Intelligence):**
    *   **Ferramentas:** Metabase (conectado ao Amazon Athena).
    *   **Processo:** Permite a criação de dashboards e relatórios interativos, fornecendo insights diretos para a tomada de decisões.

## ✨ Benefícios Chave

*   **Confiabilidade:** Dados brutos preservados para auditoria e reprocessamento.
*   **Eficiência:** Uso de Parquet e particionamento para consultas rápidas e de baixo custo na nuvem.
*   **Escalabilidade:** Arquitetura preparada para lidar com volumes crescentes de dados.
*   **Governança:** Modelagem de dados clara e testável com dbt.
*   **Insights Acionáveis:** Transformação de dados técnicos em informações de negócio valiosas.

## 🛠️ Tecnologias Utilizadas

*   **Orquestração:** Apache Airflow
*   **Processamento de Dados:** Apache Spark (PySpark)
*   **Armazenamento:** Amazon S3
*   **Motor de Consulta:** Amazon Athena
*   **Modelagem de Dados:** dbt (data build tool)
*   **Visualização/BI:** Metabase
*   **Linguagem:** Python

---

Esta descrição já te dá uma base sólida para apresentar o projeto!
