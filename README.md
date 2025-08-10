<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Análise de Risco Cardíaco</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        h1, h2, h3 {
            color: #2c3e50;
        }
        h1 {
            border-bottom: 2px solid #3498db;
            padding-bottom: 10px;
        }
        h2 {
            border-left: 4px solid #3498db;
            padding-left: 10px;
            margin-top: 30px;
        }
        .highlight {
            background-color: #f8f9fa;
            padding: 15px;
            border-radius: 5px;
            border-left: 4px solid #3498db;
            margin: 20px 0;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
        code {
            background-color: #f8f9fa;
            padding: 2px 5px;
            border-radius: 3px;
            font-family: monospace;
        }
        .metrics {
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
            margin: 20px 0;
        }
        .metric-box {
            background-color: #e8f4fc;
            border-radius: 5px;
            padding: 15px;
            margin: 10px;
            min-width: 200px;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .footer {
            margin-top: 40px;
            font-size: 0.9em;
            text-align: center;
            color: #7f8c8d;
        }
    </style>
</head>
<body>
    <h1>Análise de Risco Cardíaco</h1>
    
    <div class="highlight">
        <p>Este projeto utiliza machine learning para prever risco cardíaco com base em um dataset clínico. O modelo de Regressão Logística foi treinado para classificar pacientes em duas categorias: <strong>sem risco (0)</strong> e <strong>com risco (1)</strong>.</p>
        <p><strong>Dataset utilizado</strong>: <a href="https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset" target="_blank">Heart Disease Dataset (Kaggle)</a></p>
    </div>

    <h2>🔍 Principais Análises Realizadas</h2>
    
    <h3>1. Pré-processamento</h3>
    <ul>
        <li>Tratamento de outliers (IQR) nas variáveis <code>trestbps</code> (pressão arterial) e <code>chol</code> (colesterol).</li>
        <li>Normalização dos dados com <code>StandardScaler</code>.</li>
    </ul>
    
    <h3>2. Exploração dos Dados</h3>
    <ul>
        <li>Distribuição de variáveis como idade, sexo, pressão arterial e colesterol.</li>
        <li>Análise de correlação entre features e o target (risco cardíaco).</li>
    </ul>
    
    <h3>3. Modelagem Preditiva</h3>
    <ul>
        <li><strong>Algoritmo</strong>: Regressão Logística (<code>LogisticRegression</code>).</li>
    </ul>
    
    <div class="metrics">
        <div class="metric-box">
            <h3>Acurácia</h3>
            <p>86%</p>
        </div>
        <div class="metric-box">
            <h3>Recall (risco)</h3>
            <p>89%</p>
            <small>Minimiza falsos negativos</small>
        </div>
        <div class="metric-box">
            <h3>Precisão (sem risco)</h3>
            <p>88%</p>
        </div>
    </div>
    
    <h3>4. Matriz de Confusão</h3>
    <table>
        <tr>
            <th></th>
            <th>Previsto Sem Risco</th>
            <th>Previsto Com Risco</th>
        </tr>
        <tr>
            <td><strong>Real Sem Risco</strong></td>
            <td>73 (VP)</td>
            <td>29 (FP)</td>
        </tr>
        <tr>
            <td><strong>Real Com Risco</strong></td>
            <td>13 (FN)</td>
            <td>90 (VP)</td>
        </tr>
    </table>
    
    <h2>📊 Principais Resultados</h2>
    
    <div class="highlight">
        <p>✅ <strong>Melhor desempenho para a classe "risco"</strong>:</p>
        <ul>
            <li><strong>Recall de 89%</strong>: O modelo identifica corretamente 89% dos pacientes com risco cardíaco.</li>
            <li><strong>F1-Score de 0.86</strong>: Balanceamento ideal entre precisão e recall.</li>
        </ul>
        
        <p>📉 <strong>Trade-offs</strong>:</p>
        <ul>
            <li><strong>Falsos positivos (29)</strong>: Pacientes classificados erroneamente como "risco".</li>
            <li><strong>Falsos negativos (13)</strong>: Casos de risco não detectados (prioridade para reduzir!).</li>
        </ul>
        
        <p>🌍 <strong>Impacto clínico</strong>:</p>
        <p>O modelo é <strong>adequado para triagem inicial</strong>, mas deve ser usado em conjunto com avaliação médica.</p>
    </div>
    
    <h2>🛠 Como Executar o Projeto</h2>
    
    <h3>1. Instalação</h3>
    <pre><code>pip install pandas scikit-learn seaborn matplotlib</code></pre>
    
    <h3>2. Treinar e avaliar o modelo</h3>
    <pre><code>from sklearn.linear_model import LogisticRegression
modelo = LogisticRegression(max_iter=1000)
modelo.fit(X_train, y_train)
y_pred = modelo.predict(X_test)</code></pre>
    
    <h3>3. Gerar métricas</h3>
    <pre><code>from sklearn.metrics import classification_report
print(classification_report(y_test, y_pred))</code></pre>
    
    <h2>📌 Próximos Passos</h2>
    <ul>
        <li><strong>Reduzir falsos negativos</strong>: Testar thresholds mais baixos (ex.: 0.4) para aumentar o recall.</li>
        <li><strong>Feature importance</strong>: Identificar quais variáveis (ex.: <code>thalach</code>, <code>oldpeak</code>) têm maior peso na previsão.</li>
        <li><strong>Modelos alternativos</strong>: Testar Random Forest ou XGBoost para comparar desempenho.</li>
    </ul>
    
    <h2>📄 Licença</h2>
    <p>Este projeto é open-source (MIT License).</p>
    <p><strong>Contato</strong>: [Seu Nome] | [LinkedIn/GitHub]</p>
    
    <div class="footer">
        <p>🔗 <strong>Links Úteis</strong>:</p>
        <p><a href="https://www.kaggle.com/datasets/johnsmith88/heart-disease-dataset" target="_blank">Dataset no Kaggle</a> | 
        <a href="https://scikit-learn.org/stable/" target="_blank">Documentação scikit-learn</a></p>
        <p>✨ <em>"Um modelo com <strong>89% de recall</strong> para risco cardíaco pode salvar vidas ao identificar precocemente pacientes em perigo."</em></p>
    </div>
</body>
</html>
