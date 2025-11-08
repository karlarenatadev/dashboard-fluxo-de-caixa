# 💰 Dashboard de Fluxo de Caixa | Power BI

Este projeto é um dashboard financeiro focado no controle do fluxo de caixa (cash flow). O objetivo é permitir uma análise clara das entradas, saídas, saldo operacional e, o mais importante, o saldo acumulado ao longo do tempo.

**Arquivo do projeto:** Você pode baixar o arquivo `.pbix` original deste repositório para explorar a modelagem de dados e as complexas fórmulas DAX de inteligência de tempo.

---

## 🎯 Objetivo do Projeto

O dashboard foi projetado para responder a perguntas financeiras essenciais:
* Qual é o nosso Saldo Atual?
* Quanto de receita entrou e quanto saiu este mês?
* Como o nosso saldo se comportou (acumulou) ao longo do ano?
* Quais são nossas principais categorias de despesas?

---

## 🛠️ Ferramentas Utilizadas
* **Power BI Desktop:** Desenvolvimento do dashboard.
* **Power Query (Editor de Consultas):** Para tratamento e categorização dos lançamentos.
* **DAX (Data Analysis Expressions):** Essencial para as métricas de inteligência de tempo (Time Intelligence).

---

## 🔬 O Processo: ETL e Modelagem

1.  **Extração e Transformação (Power Query):**
    * Importei um conjunto de dados simples de lançamentos financeiros (data, descrição, valor).
    * No Power Query, criei uma coluna condicional para classificar os lançamentos em "Entrada" ou "Saída" (baseado no valor positivo ou negativo).

2.  **Modelagem de Dados (Modelo Estrela):**
    * Criei um modelo de dados simples com uma tabela **`dCalendario`** (criada via DAX) e uma tabela **`fLancamentos`**.
    * O relacionamento entre `dCalendario[Data]` e `fLancamentos[Data]` é a base para toda a análise de inteligência de tempo.

3.  **Criação de Métricas (DAX):**
    * Este projeto depende fortemente de DAX para funcionar. A métrica principal é o **Saldo Acumulado**:
    ```DAX
    Saldo Acumulado = 
    CALCULATE(
        SUM(fLancamentos[Valor]),
        FILTER(
            ALLSELECTED(dCalendario),
            dCalendario[Data] <= MAX(dCalendario[Data])
        )
    )
    ```
    * Outras métricas criadas: `Total de Entradas`, `Total de Saídas`, `Saldo do Mês (Resultado)`.

---

## 📊 O Dashboard

### Visão Principal (Dashboard Financeiro)
A tela principal mostra os KPIs mais importantes (Entradas, Saídas, Saldo do Mês) e o gráfico de Saldo Acumulado ao longo do tempo.

![Visão Principal do Dashboard de Fluxo de Caixa](dashboard-1.png)

### Análise Interativa (Filtros)
A imagem abaixo demonstra a interatividade do dashboard. Ao selecionar um **Mês** específico no filtro, todos os cards e gráficos se ajustam para mostrar apenas os dados daquele período, permitindo uma análise detalhada mês a mês.

![Dashboard com Filtro de Mês Aplicado](dashboard-2.png)

---

## 📬 Contato
* **Karla Renata** - [LinkedIn](https://www.linkedin.com/in/karlarenata-rosario/)
* **Portfólio Principal** - [karlarenatadev.github.io/portfolio-karla-renata/](https://karlarenatadev.github.io/portfolio-karla-renata/)
