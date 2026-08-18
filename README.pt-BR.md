# 🛡️ Triaxial Cybersecurity Maturity Framework

<p align="left">
  <img alt="Status" src="https://img.shields.io/badge/status-ativo-2ea44f?style=flat">
  <img alt="Versão" src="https://img.shields.io/badge/versão-v1.0-blue?style=flat">
  <img alt="Licença" src="https://img.shields.io/badge/licença-uso%20acadêmico-lightgrey?style=flat">
  <img alt="Formato" src="https://img.shields.io/badge/formato-.xlsx-217346?style=flat&logo=microsoftexcel&logoColor=white">
  <a href="https://doi.org/10.5281/zenodo.21986801"><img alt="DOI" src="https://zenodo.org/badge/DOI/10.5281/zenodo.21986801.svg"></a>
</p>

<p align="left">
  <img alt="Critérios" src="https://img.shields.io/badge/critérios-16-orange?style=flat">
  <img alt="Prismas" src="https://img.shields.io/badge/prismas-4-purple?style=flat">
  <img alt="Escala" src="https://img.shields.io/badge/escala-1--5-yellow?style=flat">
  <img alt="Base científica" src="https://img.shields.io/badge/base-32%20refs%20científicas-blueviolet?style=flat">
</p>

**🌐 Leia em outro idioma:** [English](README.md) · **Português (BR)** · [Español](README.es.md)

> **Instrumento auditável e quantitativo** para medir a maturidade de cibersegurança sob a ótica do fator humano, derivado do artigo *"Human Factors in Cybersecurity: A Triaxial Analysis from the Psychological, Organizational, and Design Perspectives, with an Extended Governance-Oriented Maturity Assessment Instrument"* (Santos, Silva & Florindo, PPEE/UnB).

---

## 📖 Sobre o Framework

Estudos apontam que **mais de 95%** dos incidentes cibernéticos envolvem, em algum nível, erro ou manipulação humana. Apesar disso, a maioria das organizações mede sua postura de segurança de forma puramente técnica ou por *reach metrics* (quantas pessoas "assistiram ao treinamento"), sem nenhuma métrica objetiva de efetividade.

Este repositório disponibiliza a planilha **[`framework-triaxial-maturidade-ciberseguranca.xlsx`](framework-triaxial-maturidade-ciberseguranca.xlsx)** — a versão totalmente em português da planilha original `cybersecurity-maturity-framework.xlsx` (abas, cabeçalhos, critérios e mensagens de validação traduzidos) — que opera­cionaliza o **Modelo Triaxial** (Psicológico, Organizacional e Design) descrito no artigo, estendido com um **quarto prisma de Governança e Conformidade** (NIST SP 800-53 e LGPD), resultando em um instrumento de **16 critérios de avaliação, agrupados em 4 dimensões**, com pesos e fórmulas ponderadas que geram um **Índice Geral de Maturidade (Imat)** e uma classificação organizacional automática.

| Prisma | Foco | Referência-chave |
|---|---|---|
| 🧠 **Psicológico** | Amygdala hijacking, viés de automação, letramento digital, phishing | Hadlington (2017); Hagen et al. (2025); Anwar et al. (2017) |
| 🏢 **Organizacional** | Paradoxo conhecimento‑comportamento, efetividade de CSA via CTI, inteligência integrada, notificação de incidentes | Georgiadou et al. (2022); Silva et al. (2025) |
| 🎨 **Design** | Framework HC3, carga cognitiva, *security by design*, governança de BYOD/Shadow IT | Cristiano & Spadafora (2024); Gutzwiller & Van Bruggen (2021) |
| ⚖️ **Governança e Conformidade** | Controles NIST SP 800‑53, princípios da LGPD, notificação ao CTIR Gov, OSINT antifraude | NIST SP 800‑53 Rev. 5; LGPD (Lei nº 13.709/2018) |

---

## 🖼️ Prévia do Painel Executivo

<p align="center">
  <img src="docs/dashboard-preview.pt-BR.svg" alt="Prévia ilustrativa da aba Painel de Controle com dados de exemplo" width="100%">
</p>

<p align="center"><sub>Mockup ilustrativo com dados de exemplo, reproduzindo o layout real da aba <code>Painel de Controle</code> — Índice Geral de Maturidade, Categoria de Maturidade e o gráfico de desempenho por prisma. Não é uma captura de tela literal da planilha.</sub></p>

---

## 🗂️ Estrutura da Planilha

> As tabelas abaixo usam os nomes técnicos originais das abas/colunas (`Dashboard`, `Assessment`) para facilitar a referência cruzada com fórmulas e a versão em inglês. Na planilha traduzida `framework-triaxial-maturidade-ciberseguranca.xlsx`, essas abas se chamam **`Painel de Controle`** e **`Avaliação`**, com todos os cabeçalhos, critérios e mensagens de validação em português.

A planilha possui **2 abas**:

### 1. `Dashboard` (**"Painel de Controle"** na versão PT) — Painel Executivo

| Célula | Conteúdo | Fórmula |
|---|---|---|
| `A5:B6` | **Índice Geral de Maturidade** | `=Assessment!H21/Assessment!I21` |
| `C5:D6` | **Categoria de Maturidade** (veredito dinâmico) | `=IF(A5<0.4,"Vulnerable/Critical", IF(A5<0.6,"Reactive/Basic", IF(A5<0.8,"Proactive/Managed","Resilient/Optimized")))` |
| `F4:I8` | Tabela de referência com a descrição de cada faixa de maturidade | estático |
| `A9:C13` | **Desempenho por Prisma**, calculado via `SUMIF` sobre a aba `Assessment`, comparado à meta mínima recomendada por dimensão | `=SUMIF(Assessment!$B$5:$B$20, "<Prisma>", Assessment!$H$5:$H$20) / SUMIF(...!$I$5:$I$20)` |
| — | Gráfico de colunas nativo comparando **maturidade atual vs. meta mínima** por prisma | Excel Chart |

### 2. `Assessment` (**"Avaliação"** na versão PT) — Entrada de Dados (16 critérios)

| Coluna | Nome | Descrição |
|---|---|---|
| A | ID | Identificador do critério (`PS-01`…`GO-04`) |
| B | Analysis Prism | Dimensão à qual o critério pertence |
| C | Metric / Requirement | O que está sendo avaliado |
| D | Scientific Reference | Autor/ano que fundamenta o critério |
| E | Evidence & Evaluation Criteria | Descrição operacional do que observar/auditar |
| **F** | **Score (1–5)** | 🔵 **Única coluna editável** — nota atribuída pelo avaliador |
| G | Weight (1–3) | Peso do critério na dimensão |
| H | Weighted Score | `=F*G` |
| I | Max Score | `=G*5` |
| J | Progress | `=H/I` (% de maturidade do critério) |
| 21 | **TOTALS & AVERAGES** | `F21=AVERAGE(F5:F20)` · `G21=SUM(G5:G20)` · `H21=SUM(H5:H20)` · `I21=SUM(I5:I20)` · `J21=H21/I21` |

> 🔒 **Validação de dados:** o intervalo `F5:F20` aceita **somente números inteiros de 1 a 5**. Qualquer outro valor é rejeitado pela regra `dataValidation` embutida na planilha, com a mensagem *"A nota inserida deve ser um número inteiro de 1 a 5."*

---

## 📐 Fórmula do Índice Geral de Maturidade

$$
I_{mat} = \frac{\sum_{i=1}^{16} s_i \cdot w_i}{\sum_{i=1}^{16} 5 \cdot w_i} \times 100\%
$$

onde `sᵢ ∈ {1,...,5}` é a nota atribuída ao critério *i* e `wᵢ` é o peso do critério, conforme a tabela de critérios abaixo.

### 🚦 Classificação de Maturidade

| Faixa | Categoria | Significado |
|---|---|---|
| 🔴 `< 40%` | **Vulnerável / Crítico** | Alta exposição à manipulação e falhas graves de processo/design |
| 🟠 `41% – 60%` | **Reativo / Básico** | Cumprimento burocrático de política formal de TI, baixo engajamento real |
| 🟡 `61% – 80%` | **Proativo / Gerenciado** | Monitoramento ativo via inteligência e interfaces centradas no usuário |
| 🟢 `81% – 100%` | **Resiliente / Otimizado** | Cultura de resiliência integrada, conformidade nativa, segurança *by design* |

---

## 📋 Os 16 Critérios de Avaliação

<details>
<summary><b>🧠 Prisma Psicológico</b> (clique para expandir)</summary>

| ID | Critério | Peso |
|---|---|:---:|
| `PS-01` | Controle de Amygdala Hijacking | 3 |
| `PS-02` | Atenuação de viés de automação/confirmação | 2 |
| `PS-03` | Autoeficácia e letramento digital | 2 |
| `PS-04` | Suscetibilidade a phishing | 3 |

</details>

<details>
<summary><b>🏢 Prisma Organizacional</b></summary>

| ID | Critério | Peso |
|---|---|:---:|
| `OR-01` | Paradoxo conhecimento–comportamento | 2 |
| `OR-02` | Efetividade/resiliência de CSA via CTI | 3 |
| `OR-03` | Processo de inteligência integrada | 2 |
| `OR-04` | Notificação ágil de incidentes | 2 |

</details>

<details>
<summary><b>🎨 Prisma de Design</b></summary>

| ID | Critério | Peso |
|---|---|:---:|
| `DS-01` | Uso do framework HC3 | 3 |
| `DS-02` | Carga cognitiva e fricção de autenticação | 2 |
| `DS-03` | *Security by Design* e controle humano | 2 |
| `DS-04` | Governança de BYOD e Shadow IT | 1 |

</details>

<details>
<summary><b>⚖️ Prisma de Governança e Conformidade</b></summary>

| ID | Critério | Peso |
|---|---|:---:|
| `GO-01` | Controles de governança NIST SP 800-53 (PM/AC/CA) | 3 |
| `GO-02` | Controles de detecção/resposta NIST SP 800-53 (AU/PT/IR/CP) | 3 |
| `GO-03` | Princípios de privacidade da LGPD | 2 |
| `GO-04` | Blindagem OSINT e mitigação de fraude | 1 |

</details>

---

## 🚀 Como Usar

Preencher a planilha é um processo simples, prático e totalmente automatizado. Toda a lógica de cálculo está protegida — você só precisa inserir as notas da sua avaliação.

### Passo 1 — Acesse a aba de Avaliação

Abra `framework-triaxial-maturidade-ciberseguranca.xlsx` no Excel, LibreOffice Calc ou Google Sheets e navegue até a aba **`Avaliação`** (segunda aba). É nela que você realizará todo o preenchimento de dados.

> **Nota:** A primeira aba, **`Painel de Controle`**, é de **leitura exclusiva** e exibe os gráficos e resultados finais consolidados automaticamente.

### Passo 2 — Avalie os 16 Critérios (Coluna F)

Na aba `Avaliação` você verá 16 linhas de critérios técnicos divididas entre os quatro prismas (Psicológico, Organizacional, Design e Governança). Para cada critério, vá até a **Coluna F (Nota)** e insira uma nota inteira de **1 a 5**, de acordo com a maturidade atual da organização, sob os seguintes parâmetros:

| Nota | Nível | Descrição |
|:---:|---|---|
| **1** | Very Weak / Critical | O controle é inexistente ou há falhas graves de segurança. |
| **2** | Weak | O processo é reativo (ad hoc), feito apenas quando há incidentes e não é documentado. |
| **3** | Intermediate | O controle está parcialmente implementado, formalizado e monitorado de forma básica. |
| **4** | Good | O processo está totalmente implementado, integrado à rotina operacional e ativamente monitorado. |
| **5** | Leader / Resilient | O processo é otimizado continuamente com base em dados de ameaças (CTI), testado sob simulações e auditado de forma recorrente. |

> ⚠️ **Atenção:** A coluna F possui uma regra de Validação de Dados. A planilha rejeitará automaticamente qualquer valor que não seja um número inteiro entre 1 e 5, para evitar erros acidentais de preenchimento.

### Passo 3 — Não altere as Fórmulas (Colunas H, I e J)

À medida que você insere as notas na coluna F:

- A **Coluna H (Pontuação Ponderada)** calculará dinamicamente a multiplicação da sua nota pelo peso de criticidade do critério (Coluna G).
- A **Coluna J (Progresso)** mostrará o percentual de conformidade daquele critério individual.

Não edite estas colunas, para não romper os vínculos matemáticos.

### Passo 4 — Analise o Painel Executivo

Após preencher os 16 critérios da aba `Avaliação`, volte para a aba `Painel de Controle`. Ela calculará de forma imediata:

- O **Índice Geral de Maturidade ($I_{mat}$)** (células `A5:B6`).
- A **Categoria de Maturidade** (células `C5:D6`): classificação automática entre *Vulnerable/Critical*, *Reactive/Basic*, *Proactive/Managed* ou *Resilient/Optimized*.
- A **Tabela de Desempenho por Prisma**: exibe em qual dimensão a organização está mais distante da meta mínima recomendada (Psicológica, Organizacional, Design ou Governança).
- O **Gráfico de Barras**: atualizará as colunas de desempenho atual contra as metas mínimas estabelecidas, para facilitar a apresentação visual dos gargalos em relatórios ou reuniões.

Reaplique a avaliação periodicamente (ex.: semestral) para acompanhar a evolução do índice ao longo do tempo.

> ⚠️ Não edite as colunas `H`, `I` e `J` — elas contêm fórmulas calculadas automaticamente a partir da nota (`F`) e do peso (`G`).

---

## 🔬 Fundamentação Científica

O framework opera­cionaliza, entre outros, os seguintes modelos citados no artigo original:

- **Modelo de efetividade de CSA via CTI** (Silva et al., 2025) — base do critério `OR-02`, cruzando participação em treinamentos com dados reais de exposição de credenciais.
- **Framework HC3** (Cristiano & Spadafora, 2024) — base do critério `DS-01`, com as 8 etapas de design centrado no usuário para sistemas criptográficos.
- **17 fatores humanos em cibersegurança** (Rohan et al., 2021) — fundamentam os critérios do prisma Psicológico.
- **NIST SP 800-53 Rev. 5** e **LGPD (Lei nº 13.709/2018)** — fundamentam o quarto prisma de Governança.

## 🔬 Rigor Científico, Escopo e Trabalhos Futuros (v1.0)

Este framework foi projetado seguindo um processo metodológico rigoroso de síntese da literatura de fatores humanos em cibersegurança. Como um projeto científico de código aberto (Open Science) em sua versão inicial (v1.0), seu escopo de aplicação está delimitado pelos seguintes parâmetros acadêmicos, os quais já estão sendo endereçados em nosso roadmap de pesquisa:

1. **Validação e Calibração de Pesos**: A atribuição atual de pesos ($w_i$) reflete a síntese qualitativa e teórica dos autores baseada na literatura revisada. Testes empíricos em larga escala e painéis de especialistas (Método Delphi) estão planejados para refinamento e calibração estatística desses coeficientes.
2. **Representatividade da Literatura**: A base conceitual do framework priorizou periódicos e conferências internacionais indexadas de alta relevância (predominantemente de escopo ocidental). Expansões futuras mapearão nuances culturais e comportamentais específicas de infraestruturas críticas do Sul Global.
3. **Análise de Causalidade**: O instrumento atual fornece um diagnóstico fotográfico (ponto no tempo) da maturidade. Estudos longitudinais futuros são necessários para estabelecer correlações causais de longo prazo entre a evolução do Índice Geral de Maturidade ($I_{mat}$) e a redução de incidentes reais.

## 📌 Citação e Preservação de Longo Prazo

Este repositório é versionado e arquivado permanentemente no **[Zenodo](https://zenodo.org)** (gratuito, mantido pelo CERN), que gera um **DOI** estável para cada release — diferente de um link comum do GitHub, um DOI não pode ser movido, renomeado ou apagado, tornando-o a referência adequada para a seção de metodologia de um artigo.

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21986801.svg)](https://doi.org/10.5281/zenodo.21986801)

> **DOI:** [10.5281/zenodo.21986801](https://doi.org/10.5281/zenodo.21986801)

**BibTeX:**

```bibtex
@software{santos_triaxial_framework,
  author    = {Santos, Karol Jozef Oliveira and Silva, Daniel Alves da and Florindo, Luiz Gustavo Marques},
  title     = {{Triaxial Cybersecurity Maturity Framework}},
  doi       = {10.5281/zenodo.21986801},
  url       = {https://doi.org/10.5281/zenodo.21986801}
}
```

---

<p align="center">
  <sub>Baseado em Santos, K. J. O.; Silva, D. A.; Florindo, L. G. M. — Programa de Pós-Graduação Profissional em Engenharia Elétrica (PPEE), Universidade de Brasília (UnB).</sub>
</p>
