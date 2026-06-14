# 📈 Experimento LIS: Análise de Tendência de Ações (Investimento)

Este repositório contém o desenvolvimento e a análise empírica do problema de **Investimento em Ações**, modelado através do problema clássico da **Maior Subsequência Crescente** (*Longest Increasing Subsequence - LIS*).

Segue link para vídeo sobre a atividade: [Experimento 7.6 - Análise de Algoritmos](https://youtu.be/sLmlrwYnAH0)

## 🎯 Objetivo do Experimento

O objetivo principal deste experimento é auxiliar um analista financeiro a identificar **períodos de crescimento sustentado** no valor de uma ação ao longo do tempo. 

Dada uma série temporal contendo o preço diário de um ativo, o sistema busca encontrar a **maior sequência de dias em que os preços apresentaram tendência crescente**, sem a obrigatoriedade de que esses dias sejam consecutivos. O foco é extrair tanto o **tamanho (quantidade de dias)** dessa janela ideal de valorização quanto a **sequência exata dos preços** que compõem essa tendência.

---

## 💻 Algoritmos Comparados

Para resolver o problema e avaliar o impacto da escolha algorítmica no processamento de grandes volumes de dados financeiros, foram implementadas e comparadas três abordagens:

1. **Algoritmo Ingênuo (Força Bruta):** Testa todas as combinações de subsequências crescentes possíveis. Possui complexidade exponencial $O(2^n)$, tornando-se inviável para séries temporais longas.
2. **Programação Dinâmica Recursiva (com Memoization):** Abordagem *top-down* que quebra o problema em subproblemas e armazena os resultados em uma tabela analítica para evitar recomputações, reduzindo a complexidade para $O(n^2)$.
3. **Programação Dinâmica Iterativa:** Abordagem *bottom-up* que preenche a tabela de soluções de forma linear e iterativa. Também possui complexidade $O(n^2)$, mas elimina o overhead de chamadas de funções da pilha de recursão.

---

## 📊 Metodologia do Experimento

O experimento foi estruturado em duas etapas principais utilizando geradores de vetores aleatórios com valores simulando preços reais de mercado:
* **Etapa 1 (Escala Pequena - $n=10$ a $n=24$):** Avaliação dos três algoritmos para validar a **corretude** do código (garantindo que todos encontram exatamente o mesmo valor ótimo) e observar a explosão do tempo da Força Bruta.
* **Etapa 2 (Escala Macro - $n=100$ a $n=1500$):** Teste de estresse focado exclusivamente nas duas abordagens de Programação Dinâmica para medir a eficiência em cenários de séries temporais mais extensas.

---

## 💡 Como os Dados Refletem o Contexto de Investimento?

Para aproximar o experimento matemático da realidade do mercado financeiro e tornar a visualização intuitiva (especialmente para apresentações e relatórios), a exibição dos dados no terminal foi projetada estrategicamente:

### 1. Representação Temporal e Caótica dos Preços
As entradas não são meros números sequenciais, mas sim um vetor caótico e independente (gerado no intervalo de `10` a `500`) que simula a **volatilidade real de um ativo** na bolsa de valores ao longo dos dias ($n$).

### 2. O Painel de Corretude Explícita como um "Histórico de Transações"
Ao final de cada etapa, o painel exibe de forma clara:
* `Preços (Entrada):` A linha do tempo completa do preço da ação em ordem cronológica de dias.
* `Sequência:` O "caminho de investimento ideal". Em vez de mostrar apenas um número isolado, o terminal exibe quais valores exatos compunham a tendência de alta. 

### 3. Visual Inteligente com Reticências (`[..., ...]`) para Escala Macro
Em investimentos, analisar uma série de 1500 dias geraria uma parede de texto ilegível no terminal. O visual adotado utiliza a exibição dos **6 primeiros dias e dos 4 últimos dias** separados por reticências. 

Isso reflete perfeitamente a forma como analistas olham gráficos históricos de ações de longo prazo: foca-se no **comportamento inicial (ponto de partida)**, sinaliza-se que o mercado continuou trabalhando no intervalo intermediário (`...`), e observa-se com precisão o **comportamento final (ponto de chegada)**.

### 4. Respostas Diferentes, Mas Igualmente Válidas (Oportunidades de Mercado)
Como o mercado financeiro pode apresentar caminhos diferentes com o mesmo retorno, o painel ilustra perfeitamente quando a PD Iterativa e a PD Recursiva encontram sequências de preços ligeiramente distintas, mas com o **mesmo tamanho final de dias ($Tamanho = 17$)**. Isso reflete visualmente que podem existir estratégias ou carteiras diferentes que geram o mesmo período total de lucro sustentado para o investidor.
