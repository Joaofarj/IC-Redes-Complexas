# Iniciação científica - Algoritmo de Gillespie na simulação de modelos epidêmicos markovianos

Aluno: João Pedro Farjoun Silva / N° usp: 13731319


Orientador: Thomas Kauê Dal'Maso Peron


Período: 1/08/2024 - 31/05/2025

# Simulação de Modelos Epidêmicos com o Algoritmo de Gillespie

Este repositório contém os códigos, resultados e explicações do projeto de Iniciação Científica desenvolvido por João Pedro Farjoun Silva, sob orientação do Prof. Thomas Kauê Dal’Maso Peron, no Instituto de Ciências Matemáticas e de Computação (ICMC-USP), com apoio da FAPESP (Processo nº 2024/08892-2).

## Objetivo

Estudar a propagação de doenças infecciosas por meio de modelos epidêmicos markovianos simulados com o Algoritmo de Gillespie. O projeto investigou como diferentes topologias de redes e taxas de infecção afetam a dinâmica da epidemia, com foco na determinação do valor crítico da taxa de transmissão (λc).

## Metodologia

### Redes Utilizadas

- **Random Regular Networks (RRN):** Todos os nós têm o mesmo grau.
- **Configuration Model:** Os graus são gerados a partir de uma distribuição binomial negativa, permitindo redes heterogêneas com hubs.

### Modelos de Propagação

- **SIS (Susceptible-Infected-Susceptible):** Indivíduos recuperados voltam a ser suscetíveis.
- **SIR (Susceptible-Infected-Recovered):** Indivíduos recuperados entram em estado imune.

### Algoritmo de Gillespie

Simulador estocástico que gera trajetórias possíveis da evolução de um sistema a partir de taxas de transição. No contexto de epidemias, é usado para simular infecções e recuperações ao longo do tempo em redes.

### Taxa Crítica de Infecção (λc)

A taxa crítica define o limiar entre a extinção e a manutenção da doença em uma população. Quando λ > λc, o sistema tende a um estado endêmico.

χ = N * (⟨ρ²⟩ − ⟨ρ⟩²) / ⟨ρ⟩

Ou

χ = N * Var[ρ] / E[ρ]

Onde ρ é a fração de infectados. O valor de λ que maximiza χ é uma estimativa de λc.

### Método Quase-Estacionário (QS)

Para evitar que o sistema caia no estado absorvente (sem infectados), foi utilizado o método QS. Ele reinicia a simulação a partir de estados ativos previamente salvos, permitindo calcular médias de forma mais estável e eficiente.

## Resultados

### Modelo SIR

- O tempo de execução do Algoritmo de Gillespie cresce com O(n²), onde n é o número de nós.
- Em redes RRN, a infecção se espalha de forma mais uniforme.
- Em redes geradas por Configuration Model, a presença de hubs cria desigualdade na disseminação.

### Modelo SIS

#### Random Regular Networks

- Estimativa do valor crítico: λc ≈ 0.211
- O pico de suscetibilidade indica claramente a transição de fase epidêmica.

#### Configuration Model

- Valores estimados de λc variam com o parâmetro r da distribuição binomial negativa:
  - r = 0.5: λc ≈ 0.063
  - r = 1: λc ≈ 0.081
  - r = 2: λc ≈ 0.114
  - r = 1000: λc ≈ 0.171
- Quanto menor o r, maior a variância da rede e menor o λc.
- Redes mais heterogêneas permitem a persistência da doença com taxas de infecção mais baixas.

## Conclusões

- Redes heterogêneas com hubs facilitam a persistência de epidemias, mesmo com baixa taxa de transmissão.
- A topologia da rede é um fator determinante na dinâmica da propagação de doenças.
- O algoritmo de Gillespie mostrou-se eficiente e apropriado para esse tipo de simulação estocástica.
- Os resultados reproduziram fenômenos bem documentados na literatura, como o decaimento de λc com o aumento da heterogeneidade estrutural.

## Referências Principais

- Gillespie, D. T. (1976). A general method for numerically simulating the stochastic time evolution of coupled chemical reactions.
- Mata, A. S., & Ferreira, S. C. (2015). Multiple transitions of the SIS epidemic model on complex networks.
- Kermack, W. O., & McKendrick, A. G. (1927). A contribution to the mathematical theory of epidemics.

## Agradecimentos

Agradeço à FAPESP pelo suporte à pesquisa (Processo nº 2024/08892-2).


### Suscetibilidade

Para estimar λc, foi usada a suscetibilidade:


