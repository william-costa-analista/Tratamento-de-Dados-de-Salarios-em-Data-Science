# Projeto: Tratamento de Dados de Salários em Data Science

## 1. Introdução
Este projeto tem como objetivo realizar o processo de **ETL (Extração, Transformação e Carga)** em um dataset público do Kaggle contendo informações salariais na área de Ciência de Dados. O foco principal foi a limpeza, conversão monetária e melhoria da legibilidade das categorias de experiência para futuras análises em ferramentas de BI.

## 2. Tecnologias Utilizadas
* **Python:** Linguagem principal.
* **Pandas:** Manipulação e tratamento dos dados.
* **PandasQL:** Execução de queries SQL sobre DataFrames.
* **Jupyter Notebook / Google Colab:** Ambiente de desenvolvimento.

## 3. Processo de ETL

### 3.1. Extração (Extract)
O dataset original foi carregado a partir do arquivo `Data_Science_Fields_Salary_Categorization.csv`.

* **Fonte:** Kaggle.
* **Formato:** CSV.

### 3.2. Transformação (Transform)
Nesta etapa, foram aplicadas três transformações críticas para garantir a qualidade da análise:

* **Limpeza e Tipagem:** A coluna `Salary_In_Rupees` continha caracteres de texto (vírgulas), que foram removidos para converter o campo em um tipo numérico (float).
* **Conversão de Moeda:** Criou-se a coluna `Salary_In_Dollars` convertendo os valores de Rúpias Indianas para Dólares Americanos, utilizando a taxa de câmbio definida no dia do projeto.
    * **Fórmula:** $Salário\ em\ Dólar = Salário\ em\ Rúpias / 90.60$
* **Padronização de Senioridade:** Para facilitar a compreensão do usuário final no Dashboard, as siglas de experiência foram mapeadas para nomes descritivos:

| Sigla | Descrição (Senioridade) |
| :--- | :--- |
| EN | Junior |
| MI | Pleno |
| SE | Senior |
| EX | Executive |

### 3.3. Carga (Load)
Após o tratamento, os dados limpos e transformados foram exportados para um novo arquivo, pronto para ser consumido por ferramentas como Power BI ou Tableau.

* **Arquivo gerado:** `Data_Science_Salary.csv`

## Base de dados utilizada: https://www.kaggle.com/datasets/whenamancodes/data-science-fields-salary-categorization

![gif dash.gif](https://github.com/willcosta29/Tratamento-de-Dados-de-Salarios-em-Data-Science/blob/53c5516f66794dca7e59703e4c96dc5e0cd29b62/gif%20dash.gif)
