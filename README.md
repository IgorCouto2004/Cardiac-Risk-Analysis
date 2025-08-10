# Análise de Risco Cardíaco

## 📌 Visão Geral do Projeto
Este projeto utiliza machine learning para prever risco cardíaco com base em um dataset clínico. O modelo de Regressão Logística foi treinado para classificar pacientes em duas categorias: **sem risco (0)** e **com risco (1)**.

**Dataset utilizado**: [Heart Disease Dataset (Kaggle)](https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset)

---

## 🔍 Principais Análises Realizadas

### 1. Pré-processamento
- Tratamento de outliers (IQR) nas variáveis `trestbps` (pressão arterial) e `chol` (colesterol)
- Normalização dos dados com `StandardScaler`

### 2. Exploração dos Dados
- Distribuição de variáveis como idade, sexo, pressão arterial e colesterol
- Análise de correlação entre features e o target (risco cardíaco)

### 3. Modelagem Preditiva
**Algoritmo**: Regressão Logística (`LogisticRegression`)

**Métricas de avaliação**:
| Métrica          | Valor |
|------------------|-------|
| Acurácia         | 86%   |
| Recall (risco)   | 89%   |
| Precisão (sem risco) | 88% |

### 4. Matriz de Confusão
|                | Previsto Sem Risco | Previsto Com Risco |
|----------------|--------------------|--------------------|
| **Real Sem Risco** | 73 (VP)            | 29 (FP)            |
| **Real Com Risco** | 13 (FN)            | 90 (VP)            |

---

## 📊 Principais Resultados
✅ **Melhor desempenho para a classe "risco"**:
- **Recall de 89%**: O modelo identifica corretamente 89% dos pacientes com risco cardíaco
- **F1-Score de 0.86**: Balanceamento ideal entre precisão e recall

📉 **Trade-offs**:
- **Falsos positivos (29)**: Pacientes classificados erroneamente como "risco"
- **Falsos negativos (13)**: Casos de risco não detectados *(prioridade para reduzir!)*

🌍 **Impacto clínico**:
O modelo é **adequado para triagem inicial**, mas deve ser usado em conjunto com avaliação médica

---

## 🛠 Como Executar o Projeto

### 1. Instalação
```bash
pip install pandas scikit-learn seaborn matplotlib
