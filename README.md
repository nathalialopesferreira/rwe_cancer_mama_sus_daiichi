# RWE em câncer de mama no SUS

## Objetivo
Este projeto utiliza dados públicos do DATASUS (SIA/SUS) para avaliar o impacto do acesso geográfico na continuidade do cuidado em pacientes com câncer de mama no SUS.

---

## Pergunta do estudo
- O acesso geográfico influencia a continuidade do cuidado no SUS?
- Pacientes em terapia HER2 seguem trajetórias diferentes?

---

## Dados
- Fonte: DATASUS (SIA/SUS – APAC)
- População: mulheres com CID-10 C50
- Período: 2019 e 2023
- Unidade geográfica: Estado de São Paulo

---

## Pipeline analítico
1. Extração dos dados via PySUS  
2. Limpeza e padronização  
3. Construção de variáveis:
   - deslocamento (tratamento fora do município)
   - tipo de terapia (HER2 vs não HER2)
   - tempo até último registro  
4. Estruturação em camadas:
   - Bronze: dados brutos  
   - Silver: dados tratados  
   - Gold: base analítica  
5. Análise descritiva e inferencial  

---

## Metodologia
- Estudo observacional com dados administrativos  
- Comparação entre grupos (HER2 vs não HER2)  
- Ajuste para confundidores (idade e ano)  
- Métodos:
  - Kaplan-Meier + log-rank  
  - Regressão de Cox  
  - Regressão logística  

Resultados interpretados como associações ajustadas (não causalidade estrita).

---

## Principais resultados
- ~49% dos pacientes realizam tratamento fora do município de residência  
- Forte concentração do cuidado em centros especializados  
- Pacientes HER2:
  - menor deslocamento  
  - maior continuidade no cuidado  
- Acesso geográfico é um determinante relevante da permanência no sistema  

---

## Limitações
- Dados administrativos (sem granularidade clínica)  
- Desfecho proxy (sem mortalidade)  
- Ausência de linkage com SIM  
- Possível confusão residual  

---

## Como rodar
pip install -r requirements.txt

Executar:
notebooks/rwe-cancer-mama-sus.ipynb

---

## Estrutura do projeto
├── notebooks/
│   └── rwe-cancer-mama-sus.ipynb
├── outputs/
│   ├── figures/
│   └── tables/
├── data/
│   └── bronze/
└── README.md

## Consideração final
Este projeto demonstra como dados do mundo real (RWE) podem ser utilizados para entender o impacto de fatores estruturais do sistema de saúde — como acesso geográfico — na jornada do paciente no SUS.
