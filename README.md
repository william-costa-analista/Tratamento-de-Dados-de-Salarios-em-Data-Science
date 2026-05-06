# 📊 Tratamento de Dados de Salários em Data Science

<div align="center">
  <img src="Dashboard_Visao_Geral.png" alt="Dashboard Visão Geral" width="60%">
</div>

---

## 1. 📝 Introdução
Este projeto tem como objetivo realizar o processo de **ETL (Extração, Transformação e Carga)** em um dataset público do Kaggle contendo informações salariais na área de Ciência de Dados. O foco principal foi a limpeza, conversão monetária e melhoria da legibilidade das categorias de experiência para futuras análises em ferramentas de BI.

## 2. 💻 Tecnologias Utilizadas
* **Python:** Linguagem principal.
* **Pandas:** Manipulação e tratamento dos dados.
* **PandasQL:** Execução de queries SQL sobre DataFrames.
* **Jupyter Notebook / Google Colab:** Ambiente de desenvolvimento.

## 3. ⚙️ Processo de ETL Passo a Passo

### 🗺️ Arquitetura e Fluxo de Dados
Abaixo apresentamos o diagrama do fluxo de dados que demonstra, de ponta a ponta, todo o processo de construção e execução do projeto, desde a coleta nas fontes até a visualização final:

```mermaid
graph TD
    %% Estilização
    classDef source fill:#191c22,stroke:#75ff9e,stroke-width:2px,color:#fff;
    classDef transform fill:#2563eb,stroke:#fff,stroke-width:2px,color:#fff;
    classDef load fill:#10b981,stroke:#fff,stroke-width:2px,color:#fff;
    classDef dashboard fill:#059669,stroke:#fff,stroke-width:3px,color:#fff;

    %% Fontes de Dados
    A[(Kaggle: CSV Dataset)]:::source
    B[Wikipedia: Tabela ISO 3166-1]:::source

    %% Transformação em Python
    subgraph Python [Transformação em Python / Pandas]
        C[Limpeza de Colunas]:::transform
        D[Tratamento de Nulos & Tipagem]:::transform
        E[Conversão Dólar/Rúpia]:::transform
        F[Padronização de Senioridade]:::transform
    end

    %% Integração e BI
    G[(Exportação: CSV Tratado)]:::load
    H[Power BI: Carga & Modelagem]:::load
    I{Dashboard Interativo}:::dashboard

    %% Conexões
    A --> C
    C --> D
    D --> E
    E --> F
    F --> G
    
    B -.->|Conexão Web| H
    G -->|Importação| H
    H --> I
```

### 3.1. 📥 Extração (Extract)
A fase de extração envolveu a coleta de dados de duas fontes distintas para compor o modelo final do dashboard:

1. **Dataset Principal:** Carregado a partir do arquivo `Data_Science_Fields_Salary_Categorization.csv`.
   * **Fonte:** Kaggle.
   * **Formato:** CSV.
   
2. **Dados Geográficos (Web Scraping):** Foi extraída uma tabela diretamente da página da **Wikipedia** contendo os códigos dos países no padrão **ISO 3166-1**. Esses dados foram puxados diretamente para o Power BI para permitir a correta identificação das localidades e a criação de visualizações interativas em mapas.

**Etapas de Inserção e Navegação Inicial:**
<p align="center">
  <img src="/001-Inserir%20Dados.png" width="25%" />
  <img src="002-Inserir%20Dados.png" width="48%" />
</p>

### 3.2. 🔄 Transformação (Transform)
Nesta etapa, aplicamos diversas transformações críticas para garantir a qualidade da análise e a correta formatação dos dados.

**Navegando e Explorando os Dados:**
<p align="center">
  <img src="003-Navegador.png" width="35%" />
  <img src="004-Navegador.png" width="70%" />
</p>

**Passos Realizados:**

1. **Mantendo Apenas as Colunas Necessárias:** Selecionamos exclusivamente as colunas relevantes para a análise final, otimizando o dataset.
   <br/><br/>
   <img src="005-Mantendo%20Colunas%20Necessarias.png" width="80%" />
   <br/><br/>

2. **Remoção de Nulos (NaN):** Identificação e tratamento de valores ausentes para evitar distorções nas métricas.
   <br/><br/>
   <img src="005-Removendo%20os%20Nulos.png" width="80%" />
   <br/><br/>

3. **Limpeza e Tipagem:** A coluna `Salary_In_Rupees` continha caracteres de texto (como vírgulas), que foram removidos para converter o campo corretamente em um tipo numérico (float).

4. **Conversão de Moeda:** Foi criada a coluna `Salary_In_Dollars` para converter os valores de Rúpias Indianas para Dólares Americanos, utilizando a taxa de câmbio definida no dia do projeto.
    * **Fórmula:** `Salário em Dólar = Salário em Rúpias / 90.60`

5. **Padronização de Senioridade:** Para facilitar a compreensão do usuário final no Dashboard, as siglas de experiência foram mapeadas para nomes descritivos:

| Sigla | Descrição (Senioridade) |
| :---: | :--- |
| **EN** | Junior |
| **MI** | Pleno |
| **SE** | Senior |
| **EX** | Executive |

**Modelagem e Estruturação Final:**
<p align="center">
  <img src="007-Modelando.png" width="80%" />
</p>

### 3.3. 📤 Carga (Load)
Após o tratamento, os dados limpos e transformados foram exportados para um novo arquivo, pronto para ser consumido por ferramentas como Power BI ou Tableau.

* **Arquivo Gerado:** `Data_Science_Salary.csv`

**Amostra do Resultado Final dos Dados:**
<p align="center">
  <img src="006-Resultado%20Final.png" width="80%" />
</p>

---

## 📌 Base de Dados Utilizada
🔗 [Data Science Fields Salary Categorization - Kaggle](https://www.kaggle.com/datasets/whenamancodes/data-science-fields-salary-categorization)

## 🎥 Demonstração do Projeto
![Demonstração do Dashboard](https://github.com/willcosta29/Tratamento-de-Dados-de-Salarios-em-Data-Science/blob/53c5516f66794dca7e59703e4c96dc5e0cd29b62/gif%20dash.gif?raw=true)
