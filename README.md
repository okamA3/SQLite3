# 🩺 Projeto de Integração e Análise de Dados Clínicos

Este repositório contém um exemplo prático de manipulação, integração e consulta de dados na área da saúde. O projeto simula o cenário de uma clínica médica que gerencia informações provenientes de múltiplas fontes de dados: arquivos estruturados (CSV), dados semiestruturados de prontuários (JSON) e um banco de dados relacional (SQLite).

## 📋 Estrutura do Projeto e Dados

O projeto utiliza três bases de dados principais para simular a consolidação de informações médicas:

1. **Pacientes (`pacientes.csv`)**:
   - Dados cadastrais dos pacientes, importados e manipulados através da biblioteca **Pandas**.

2. **Prontuários e Exames (`prontuarios_exames.json`)**:
   - Informações detalhadas de consultas, dados de triagem (pressão arterial, temperatura e peso) e a lista de exames solicitados (com código, nome, valor e status do resultado).

3. **Banco de Dados Relacional (`clinica.db` / `clinica.sql`)**:
   - Um banco de dados **SQLite** que armazena informações estruturadas de:
     - **Médicos**: Cadastro dos profissionais de saúde da clínica.
     - **Consultas**: Registro de agendamentos e atendimentos.

---

## 🚀 Tecnologias Utilizadas

- **Python 3**
- **Pandas**: Para leitura de arquivos CSV, JSON e integração direta com queries SQL.
- **SQLite3**: Banco de dados relacional leve para armazenamento de tabelas locais.
- **JSON**: Manipulação de dados estruturados e aninhados de triagens e exames.

---

## 🛠️ Como Executar o Projeto

### 1. Clonar o Repositório
```bash
git clone https://github.com/ChiaviniK/dados-medicina-exemplo.git
cd dados-medicina-exemplo
```

### 2. Executar as Etapas de Integração no Python

*   **Leitura de Pacientes (CSV):**
    ```python
    import pandas as pd
    df_pacientes = pd.read_csv("pacientes.csv")
    ```

*   **Leitura de Prontuários (JSON):**
    ```python
    df_prontuarios = pd.read_json("prontuarios_exames.json")
    ```

*   **Criação do Banco de Dados e Queries (SQLite + Pandas):**
    ```python
    import sqlite3
    
    # Conexão e população do banco
    conn = sqlite3.connect("clinica.db")
    with open("clinica.sql", "r", encoding="utf-8") as f:
        conn.executescript(f.read())
    
    # Consulta de médicos
    df_medicos = pd.read_sql_query("SELECT * FROM medicos", conn)
    # Consulta de consultas realizadas
    df_consultas = pd.read_sql_query("SELECT * FROM consultas", conn)
    ```

---

## 🎯 Objetivos de Estudo Aplicados
- **ETL (Extract, Transform, Load)**: Extração de múltiplos formatos (JSON, CSV, SQL) e consolidação em memória.
- **Manipulação de Dados Aninhados**: Tratamento de listas de dicionários no JSON (como a lista de exames e dados de triagem).
- **Integração SQL com Pandas**: Uso do `pd.read_sql_query` para transformar queries relacionais diretamente em DataFrames prontos para análise.
```
