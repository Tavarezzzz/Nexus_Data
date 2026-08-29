<div align="center">
  
# Nexus Data: Plataforma Preditiva de Equidade em Saúde

![Python](https://img.shields.io/badge/Python-141414?style=for-the-badge&logo=python)
![Apache Airflow](https://img.shields.io/badge/Apache_Airflow-141414?style=for-the-badge&logo=apacheairflow&logoColor=FFA500)
![DuckDB](https://img.shields.io/badge/DuckDB-141414?style=for-the-badge&logo=duckdb)
![PostgreSQL](https://img.shields.io/badge/NeonDB_(Postgres)-141414?style=for-the-badge&logo=postgresql)
![Machine Learning](https://img.shields.io/badge/Machine_Learning-141414?style=for-the-badge&logo=scikitlearn)

</div>

## 📌 O Contexto
A rede de saúde do Recife, composta por 8 Distritos Sanitários e 141 Unidades de Saúde da Família, registra seus atendimentos no sistema PEC/e-SUS APS. O grande desafio atual é a extração manual desses dados e a falta de padronização nos marcadores de equidade (raça/cor, identidade de gênero, orientação sexual e deficiência). Isso inviabiliza análises contínuas, dificultando o acompanhamento longitudinal e a prevenção da evasão de grupos vulnerabilizados nas consultas agendadas.

## 🎯 A Solução
Nossa missão é transformar o sistema de saúde de passivo para preventivo. A **Nexus Data** é uma plataforma baseada em uma arquitetura ELT que visa eliminar o esforço manual da equipe técnica.

Além de estruturar os dados, integramos um modelo preditivo de Machine Learning que calcula o risco de evasão (no-show) de pacientes. O resultado é entregue em uma interface interativa dividida em abas, gerando uma **Fila de Prioridade** limpa e acionável para que as equipes de saúde realizem a busca ativa de forma direcionada, sem sobrecarga visual.

## 🏗️ Arquitetura do Pipeline (ELT & IA)
O fluxo de dados foi desenhado para suportar alto volume e alimentar modelos de inteligência artificial sem onerar os sistemas da prefeitura.

```mermaid
graph TD
    subgraph ELT [⚙️ Camada de Engenharia de Dados]
        direction LR
        A[📥 1. Coleta Bronze<br/>Airflow + DuckDB] --> B[🧹 2. Limpeza Prata<br/>Python]
        B --> C[(🗄️ 3. Armazenamento Ouro<br/>NeonDB / PostgreSQL)]
    end

    subgraph IA [🧠 Inteligência Artificial & Consumo]
        direction LR
        C --> D[⚙️ 4. Treinamento<br/>Machine Learning]
        D --> E[🎯 5. Inferência<br/>Risco e Fila de Prioridade]
        E --> F[💻 6. Dashboard<br/>Painel Gerencial em Abas]
    end
    
    style ELT fill:#141414,stroke:#141414,stroke-width:2px,color:#fff
    style IA fill:#141414,stroke:#141414,stroke-width:2px,color:#fff
