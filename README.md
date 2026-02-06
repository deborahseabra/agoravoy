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

### 🔍 Analisar resultados

Dado o tamanho de amostra e conversões observadas de cada grupo, calcula o nível de confiança do resultado.

- Entrada por **números absolutos** ou **taxa percentual**
- Retorna **p-valor**, **Z-score** e **confiança observada**
- Badge visual de significância (p < 0.05)
- Cálculo de uplift observado entre grupos

## Fórmula

A aba de planejamento usa a fórmula de Evan Miller para comparação de duas proporções:

```
n = (Zα · √(2·p₁·q₁) + Zβ · √(p₁·q₁ + p₂·q₂))² / (p₂ − p₁)²
```

Onde:
- `p₁` = taxa base (controle)
- `p₂` = taxa esperada (variante)
- `q = 1 − p`
- `Zα` = valor Z para o nível de confiança (1.96 para 95% bicaudal)
- `Zβ` = valor Z para o poder estatístico (0.84 para 80%)

O poder estatístico é fixado em **80%** (padrão da indústria, Cohen 1988).

A aba de análise usa o **Z-test para duas proporções** com variância pooled:

```
Z = (pA − pB) / √(p̂·(1−p̂)·(1/nA + 1/nB))
```

Onde `p̂` é a proporção pooled dos dois grupos.

### Referências

- [Evan Miller — Sample Size Calculator (código-fonte)](https://www.evanmiller.org/ab-testing/sample-size.html)
- [Lachin, J.M. (1981). Introduction to sample size determination and power analysis for clinical trials](https://doi.org/10.1016/0197-2456(81)90001-5)
- Cohen, J. (1988). *Statistical Power Analysis for the Behavioral Sciences*. 2nd ed.

## Como usar

Abra `index.html` no navegador. Não precisa de servidor, build, nem instalação.

```bash
git clone https://github.com/deborahseabra/agoravoy.git
open index.html
```

Ou acesse via GitHub Pages se habilitado no repositório.

## Stack

- HTML + CSS + JavaScript vanilla
- Zero dependências externas
- Fontes: [DM Sans](https://fonts.google.com/specimen/DM+Sans) + [Fraunces](https://fonts.google.com/specimen/Fraunces) (Google Fonts)

## Licença

MIT
