# ☀️ Predição de Irradiância Solar no Pará com Machine Learning

> TCC do curso de Bacharelado em Engenharia de Software — UEPA (2025)

Análise preditiva usando **Random Forest** e **Multi-Layer Perceptron (MLP)** para prever a irradiância solar diária em municípios do estado do Pará, com base em 15 anos de dados meteorológicos históricos do INMET.

---

## 🎯 Objetivo

Avaliar a aplicabilidade de técnicas de aprendizado de máquina no apoio ao planejamento energético regional, prevendo o potencial de geração de energia solar fotovoltaica em cidades paraenses e identificando os municípios com maior e menor potencial de irradiância.

## 📊 Dados

- **Fonte:** INMET — Banco de Dados Meteorológicos para Ensino e Pesquisa (BDMEP)
- **Período:** 2010 a 2024 (dados horários, agregados para série diária no intervalo 6h–18h)
- **Cobertura:** estações meteorológicas automáticas distribuídas pelo estado do Pará
- **Variáveis:** irradiância global, temperatura, umidade relativa, pressão atmosférica, velocidade do vento, precipitação, com defasagens (*lags*) de 1 a 7 dias

## 🧠 Metodologia

1. **Limpeza e tratamento**: remoção de duplicidades, tratamento de ausências, filtragem de outliers por percentil, consolidação diária das séries horárias
2. **Análise exploratória e clusterização**: agrupamento de municípios com perfil de radiação semelhante via **K-Means**
3. **Modelagem preditiva**: treinamento e comparação de dois algoritmos:
   - **Random Forest** — ensemble de árvores de decisão
   - **Multi-Layer Perceptron (MLP)** — rede neural feedforward, com normalização Min-Max e *early stopping*
4. **Validação temporal**: estratégia *walk-forward* (treino até o ano *t-1*, teste no ano *t*), evitando vazamento de informação futura
5. **Ranking de potencial solar**: elaborado a partir das previsões, combinando mediana e percentil 95 da radiação prevista

## 📈 Resultados

| Modelo | MAE (kJ/m²) | RMSE (kJ/m²) | R² |
|---|---|---|---|
| Random Forest | 1807,34 | 2527,04 | 0,705 |
| **MLP** | **1685,84** | **2405,25** | **0,730** |

A MLP apresentou melhor desempenho geral, capturando com mais precisão as relações não lineares entre variáveis meteorológicas e radiação solar.

**Previsão futura (2021–2024)**: erro médio absoluto entre 1650 e 1890 kJ/m², confirmando boa capacidade de generalização fora da amostra de treino.

**Top 5 cidades com maior potencial solar previsto:**
1. Conceição do Araguaia
2. Paragominas
3. Bragança
4. Tomé-Açu
5. Rondon do Pará

Municípios do interior, com menor nebulosidade, apresentaram maior e mais estável potencial solar, enquanto cidades litorâneas sofreram maior influência da umidade e cobertura de nuvens.

## 🛠️ Tecnologias

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white)
![TensorFlow](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)

## 📁 Estrutura do repositório

```
├── data/               # dados brutos e tratados
├── notebooks/          # notebooks de EDA, clusterização e modelagem
├── src/                # scripts de tratamento, modelagem e validação
├── results/            # gráficos, tabelas e métricas geradas
├── TCC.pdf             # documento completo do trabalho
└── README.md
```

*(ajuste essa estrutura para refletir a organização real dos seus arquivos)*

## 🚀 Como executar

```bash
git clone https://github.com/SEU_USUARIO/predicao-radiacao-solar-para.git
cd predicao-radiacao-solar-para
pip install -r requirements.txt
```

## 📄 Documento completo

O trabalho completo, incluindo referencial teórico e discussão detalhada dos resultados, está disponível em [`TCC.pdf`](./TCC.pdf).

## ✍️ Autor

**Vinícius** — Bacharelado em Engenharia de Software, UEPA (2025)
Orientador: Prof. Dr. Fabrício de Souza Farias

---

<sub>Trabalho de Conclusão de Curso apresentado à Universidade do Estado do Pará (UEPA) como requisito parcial para obtenção do grau de Bacharel em Engenharia de Software.</sub>
