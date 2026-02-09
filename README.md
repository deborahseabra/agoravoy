# A/B Test Calculator

Calculadora de sample size e análise de significância para testes A/B. Ferramenta estática (HTML puro, zero dependências) pensada para times de produto e operações que precisam dimensionar experimentos ou validar resultados rapidamente.

## Funcionalidades

### 📐 Planejar sample size

Dado uma taxa base e a variação que você quer detectar, calcula o tamanho de amostra necessário por grupo.

- **Variação positiva ou negativa** — ex: detectar aumento de retenção (+5 p.p.) ou redução de churn (-5 p.p.)
- **Modo p.p. ou % relativo** — pontos percentuais (padrão) ou uplift relativo
- **Confiança configurável** — 90%, 95% ou 99%
- **Teste bicaudal ou unicaudal**
- Preview em tempo real mostrando a conversão entre modos (p.p. ↔ % relativo)

### 🔍 Analisar proporções

Dado o tamanho de amostra e conversões observadas de cada grupo, calcula o nível de confiança do resultado.

- Entrada por **números absolutos** ou **taxa percentual**
- Retorna **p-valor**, **Z-score** e **confiança observada**
- Badge visual de significância (p < 0.05)
- Cálculo de uplift observado entre grupos
- **Use para:** taxas de conversão, retenção, churn, CTR

### 📊 Comparar médias (t-test)

Compara a média de uma métrica contínua entre dois grupos usando Welch's t-test.

- Inputs: **média**, **desvio padrão** e **n** de cada grupo
- Retorna **p-valor**, **t-statistic**, **graus de liberdade** e **confiança observada**
- Não assume variâncias iguais (Welch's t-test)
- **Use para:** CSAT, NPS, nota média, tempo de resposta, ticket médio

## Fórmulas

### Planejar sample size — Evan Miller

```
n = (Zα · √(2·p₁·q₁) + Zβ · √(p₁·q₁ + p₂·q₂))² / (p₂ − p₁)²
```

Onde `p₁` = taxa base, `p₂` = taxa esperada, `q = 1 − p`, `Zα` = valor Z para o nível de confiança, `Zβ` = valor Z para o poder estatístico. Poder fixo em 80%.

### Analisar proporções — Z-test pooled

```
Z = (pA − pB) / √(p̂ · (1−p̂) · (1/nA + 1/nB))
```

Onde `p̂` é a proporção pooled dos dois grupos.

### Comparar médias — Welch's t-test

```
t = (x̄A − x̄B) / √(s²A/nA + s²B/nB)
```

Graus de liberdade calculados pela aproximação de Welch-Satterthwaite.

### Referências

- [Evan Miller — Sample Size Calculator](https://www.evanmiller.org/ab-testing/sample-size.html)
- [Lachin, J.M. (1981). Introduction to sample size determination and power analysis for clinical trials](https://doi.org/10.1016/0197-2456(81)90001-5)
- Cohen, J. (1988). *Statistical Power Analysis for the Behavioral Sciences*. 2nd ed.
- Welch, B.L. (1947). *The generalization of "Student's" problem when several different population variances are involved*. Biometrika, 34(1-2), 28–35.

## Como usar

[Acesse via navegador] (https://deborahseabra.github.io/agoravoy)

## Stack

- HTML + CSS + JavaScript vanilla
- Zero dependências externas
- Fontes: [DM Sans](https://fonts.google.com/specimen/DM+Sans) + [Fraunces](https://fonts.google.com/specimen/Fraunces) (Google Fonts)

## Licença

MIT
