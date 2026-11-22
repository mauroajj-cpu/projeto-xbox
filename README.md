# Dashboard de Vendas de Assinaturas do Xbox 🎮

Projeto de análise de dados em Excel que consolida as vendas de assinaturas do **Xbox**, com tabelas dinâmicas e um dashboard interativo para acompanhar o faturamento.


---

## 1. Sobre o projeto

O objetivo baseia-se em criar um dashboard, organizar dados e responder perguntas de negócio sobre o faturamento das vendas. A planilha segue o fluxo **base de dados → cálculos → dashboard**:

1. Os dados brutos ficam em uma tabela estruturada.
2. Tabelas dinâmicas agregam os valores para cada pergunta de negócio.
3. O dashboard exibe os resultados em cartões (KPIs) e gráficos, com um filtro por tipo de assinatura.

### Perguntas de negócio respondidas

| # | Pergunta | Onde está |
|---|----------|-----------|
| 1 | Qual o faturamento total de vendas de planos anuais (todas as assinaturas agregadas)? | Aba `Cálculos`, tabela dinâmica `tbl_annual_total` |
| 2 | Qual o faturamento dos planos anuais, separado por auto renovação (sim/não)? | Aba `Cálculos`, tabela dinâmica `tbl_annual_total` |
| 3 | Qual o total de vendas de assinaturas do EA Play? | Aba `Cálculos`, tabela dinâmica `tbl_easeasonpass_total` |
| 4 | Qual o total de vendas de assinaturas do Minecraft Season Pass? | Aba `Cálculos`, tabela dinâmica `Tabela dinâmica9` |

---

## 2. Estrutura da planilha

| Aba | Conteúdo |
|-----|----------|
| **Assets** | Paleta de cores do projeto (verde Xbox `#9BC848` e `#22C55E`, tons de menu `#2AE6B1` e `#5BF6A8`, cinza `#E8E6E9` para a zona negativa), logos e ícones usados no dashboard. |
| **Bases** | Base de dados em uma tabela do Excel chamada `Tabela1` (intervalo `A1:M296`, 295 registros e 13 colunas). |
| **Cálculos** | Três tabelas dinâmicas (uma por KPI) e um gráfico de colunas de apoio com o faturamento por auto renovação. |
| **Dashboard** | Painel final com título "XBOX GAME PASS SUBSCRIPTIONS SALES", cartões de KPI, gráficos, segmentação de dados por *Subscription Type* e rodapé com o período de cálculo e a data de atualização. |

---

## 3. Dados utilizados

A base (`Bases` → `Tabela1`) tem **uma linha por assinante**: 295 registros, sem valores nulos e com `Subscriber ID` único (3231 a 3525).

### Dicionário de dados

| Coluna | Tipo | Descrição | Valores observados |
|--------|------|-----------|--------------------|
| `Subscriber ID` | Inteiro | Identificador único do assinante | 3231 a 3525 |
| `Name` | Texto | Nome do assinante | 280 nomes distintos (alguns se repetem) |
| `Plan` | Texto | Plano do Game Pass | `Core`, `Standard`, `Ultimate` |
| `Start Date` | Data | Data de início da assinatura | 01/01/2024 a 16/12/2024 |
| `Auto Renewal` | Texto | Renovação automática ativa | `Yes`, `No` |
| `Subscription Price` | Moeda (R$) | Preço do plano | Core R$ 5, Standard R$ 10, Ultimate R$ 15 |
| `Subscription Type` | Texto | Periodicidade da assinatura | `Monthly`, `Quarterly`, `Annual` |
| `EA Play Season Pass` | Texto | Contratou o EA Play | `Yes`, `No` |
| `EA Play Season Pass Price` | Moeda (R$) | Preço do EA Play | R$ 30, ou `-` quando não contratou |
| `Minecraft Season Pass` | Texto | Contratou o Minecraft Season Pass | `Yes`, `No` |
| `Minecraft Season Pass Price` | Moeda (R$) | Preço do Minecraft Season Pass | R$ 20, ou R$ 0 quando não contratou |
| `Coupon Value` | Moeda (R$) | Valor de cupom de desconto aplicado | R$ 0 a R$ 20 (média de R$ 7,19) |
| `Total Value` | Moeda (R$) | Valor total da venda | R$ 3 a R$ 62 |

### Regras identificadas na base

- **`Total Value = Subscription Price + EA Play Price + Minecraft Price − Coupon Value`.** Isso vale para os 295 registros, gravados como **valor fixo**, não como fórmula.
- **EA Play** é contratado apenas por assinantes do plano `Ultimate` (98 assinantes).
- **Minecraft Season Pass** é contratado apenas por assinantes dos planos `Standard` e `Ultimate` (96 e 98 assinantes). Nenhum assinante `Core` contratou.

### Distribuição

| Dimensão | Distribuição |
|----------|--------------|
| Plano | Core 101 · Standard 96 · Ultimate 98 |
| Periodicidade | Monthly 139 · Quarterly 85 · Annual 71 |
| Auto renovação | Sim 148 · Não 147 |
| EA Play | Sim 98 · Não 197 |
| Minecraft | Sim 194 · Não 101 |

---

## 4. Resultados

Valores calculados diretamente da base, em reais (R$):

| Indicador | Todos os tipos | Monthly | Quarterly | Annual |
|-----------|---------------:|--------:|----------:|-------:|
| Faturamento total | 7.633 | 3.571 | 2.308 | 1.754 |
| EA Play | 2.940 | 1.350 | 990 | 600 |
| Minecraft Season Pass | 3.880 | 1.800 | 1.140 | 940 |

**Faturamento por auto renovação:**

| Tipo | Sem auto renovação | Com auto renovação |
|------|-------------------:|-------------------:|
| Monthly | 2.824 | 747 |
| Quarterly | 806 | 1.502 |
| Annual | 217 | 1.537 |

**Faturamento por plano:** Core R$ 444 · Standard R$ 1.801 · Ultimate R$ 5.388.

---

## 5. Como utilizar

### Requisitos

- **Microsoft Excel 2013 ou superior**.

### Passo a passo

1. **1.** Faça o download do arquivo.
2. **Abra** `Planilha_de_Vendas_do_Xbox.xlsx` no Excel.
3. **Clique no menu interativo** e selecione a aba desejada, **Anual**, **Monthly** ou **Quarterly**.
4. Veja os valores totais arrecadados pelas inscrições.

---

## Aprendizados

O desenvolvimento deste projeto foi de suma importância, pois, é uma oportunidade de aplicar todos os conhecimentos trabalhados nas aulas do Felipão na DIO, especialmente na construção de um dashboard.
Além da prática com planilhas, o projeto permitiu exercitar a estruturação de informações, a organização de dados e a criação de uma ferramenta com finalidade definida.

---

## Autor!

* [@mauroajj-cpu](https://github.com/mauroajj-cpu)

---
