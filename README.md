
# 📉 Análise de Cancelamentos de Clientes

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)

Este projeto analisa uma base de dados fictícia para entender os principais **fatores que levam clientes ao cancelamento** de um serviço. Com base nos dados, foram propostas ações estratégicas para **reduzir a taxa de churn** e melhorar o relacionamento com o cliente.

---

## 🔍 Objetivos

- Identificar padrões de cancelamento de clientes.
- Analisar variáveis críticas como: tipo de contrato, número de ligações ao call center, e dias de atraso no pagamento.
- Propor ações preventivas para reter clientes com alto risco de churn.

---

## 🧰 Tecnologias Utilizadas

- **Python**
- **Pandas**
- **Plotly**
- **Jupyter Notebook**
- **OpenPyXL**
- **NumPy**

---

## 🚶 Passo a Passo do Projeto

### 🗂️ 1. Importação da Base de Dados

```python
import pandas as pd
tabela = pd.read_csv("cancelamentos_sample.csv")
```

---

### 👀 2. Visualização e Limpeza

- Remoção da coluna `CustomerID` (não relevante para análise).
- Exclusão de linhas com valores nulos.
- Visualização da estrutura da base de dados.

```python
tabela = tabela.drop(columns="CustomerID")
tabela = tabela.dropna()
```

---

### 📊 3. Análise Inicial dos Cancelamentos

- Contagem absoluta e percentual de cancelamentos:

```python
tabela["cancelou"].value_counts()
tabela["cancelou"].value_counts(normalize=True)
```

---

### 🧠 4. Análise das Causas

- Geração de gráficos para **todas as colunas**, com foco nos cancelamentos.

```python
import plotly.express as px

for coluna in tabela.columns:
    grafico = px.histogram(tabela, x=coluna, color="cancelou")
    grafico.show()
```

📸 *Exemplo de Gráfico:*  
![exemplo-grafico](images/grafico_cancelamento.png)

---

## 🧩 Principais Insights

📌 **Contrato Mensal = Maior índice de cancelamento**  
→ *Solução:* Criar incentivos para migração para planos trimestrais/anuais.

📌 **Mais de 4 ligações ao Call Center = alta chance de cancelamento**  
→ *Solução:* Melhorar a eficiência do atendimento, resolvendo em até 3 ligações.

📌 **Mais de 20 dias de atraso no pagamento = maior chance de churn**  
→ *Solução:* Implantar políticas proativas para regularização até o 10º dia.

---

## 🎯 Estratégia Simulada (Aplicação dos Filtros)

```python
tabela = tabela[tabela["duracao_contrato"]!="Monthly"]
tabela = tabela[tabela["ligacoes_callcenter"]<=4]
tabela = tabela[tabela["dias_atraso"]<=20]
```

📉 **Resultado após filtros:**

```python
tabela["cancelou"].value_counts(normalize=True)
```

✨ A taxa de cancelamento caiu drasticamente após aplicar os filtros estratégicos.

---

## ✅ Conclusão

Com uma análise clara dos dados, é possível prever o comportamento de clientes e **tomar decisões baseadas em evidências**, reduzindo significativamente o churn.  
O projeto prova o valor da **inteligência de dados aplicada à experiência do cliente**.

---

## 📁 Organização do Projeto

```
📦 cancelamento-clientes
├── 📜 cancelamentos_sample.csv
├── 📓 cancelamento.ipynb
├── 📊 images/
│   └── grafico_cancelamento.png
└── README.md
```

---

## 📌 Para Executar Localmente

1. Clone o repositório:
   ```bash
   git clone https://github.com/seu-usuario/cancelamento-clientes.git
   ```

2. Instale as bibliotecas necessárias:
   ```bash
   pip install pandas numpy openpyxl plotly
   ```

3. Rode o notebook `cancelamento.ipynb` com Jupyter Notebook.

---

## ✉️ Contato

[![LinkedIn](https://img.shields.io/badge/LinkedIn-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/viniciuscalisto/)  
Desenvolvido com 💡 por **Vinícius Calisto de Sirqueira**
