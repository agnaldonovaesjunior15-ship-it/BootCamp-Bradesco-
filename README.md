#  Miniguia de Estudos — Inteligência Artificial Generativa com NotebookLM

> **Projeto de Portfólio — Bootcamp DIO**  
> Caderno Temático criado com NotebookLM | Tema: Inteligência Artificial Generativa (GenAI)


##  Contexto e Objetivos

### Por que escolhi este tema?

A **Inteligência Artificial Generativa** é uma das áreas de maior impacto tecnológico da atualidade. Modelos como GPT, Claude, Gemini e Stable Diffusion estão transformando indústrias inteiras — de saúde a entretenimento, de educação a desenvolvimento de software. Entender como essas tecnologias funcionam, quais são seus fundamentos e como aplicá-las de forma ética e eficiente é uma habilidade essencial para profissionais de tecnologia em 2024 e além.

### Objetivos de Estudo

-  Compreender os fundamentos dos **Large Language Models (LLMs)** e sua arquitetura Transformer
-  Entender o processo de **treinamento, fine-tuning e RLHF** (Reinforcement Learning from Human Feedback)
-  Aprender sobre **Engenharia de Prompts** e suas técnicas avançadas (few-shot, chain-of-thought, RAG)
-  Avaliar as **implicações éticas** da IA Generativa: vieses, alucinações e uso responsável
-  Mapear as **aplicações práticas** em diferentes domínios profissionais
-  Construir um **vocabulário técnico** sólido para comunicação no mercado de trabalho


##  Engenharia de Prompts e "Cicatrizes"

Esta seção documenta o processo real de interação com o NotebookLM — incluindo prompts testados, resultados obtidos


###  Prompt 1 — Exploração Inicial (Simples)

**Objetivo:** Obter uma visão geral do tema para nortear os estudos

```
O que é Inteligência Artificial Generativa? Explique de forma clara 
para alguém com conhecimento intermediário em programação.
```

**Resposta obtida:** O NotebookLM gerou um resumo coerente, mas genérico demais — trazia definições básicas sem mencionar as fontes específicas carregadas. As referências aos papers não foram citadas automaticamente.

** Dificuldade encontrada:** A IA usou conhecimento geral em vez das fontes carregadas.

** Ajuste:** Reformulei o prompt para forçar o uso das fontes:

```
Com base exclusivamente nos documentos carregados neste notebook, 
explique o que é Inteligência Artificial Generativa. Cite os autores 
e documentos de origem para cada afirmação.
```

**Resultado após ajuste:** Muito melhor! O NotebookLM passou a citar corretamente os papers do Vaswani et al. e do Zhao et al., conectando os conceitos às fontes.

###  Prompt 2 — Aprofundamento Técnico (Intermediário)

**Objetivo:** Entender a arquitetura Transformer com base no paper original

```
Explique como funciona o mecanismo de "self-attention" descrito 
no artigo "Attention Is All You Need". Use analogias para facilitar 
a compreensão e indique em qual seção do documento isso está detalhado.
```

**Resposta obtida:** Excelente! O NotebookLM localizou a Seção 3.2 do paper e explicou o mecanismo de atenção com clareza, usando a analogia de "palavras votando em outras palavras" para capturar contexto.

** Técnica que funcionou bem:** Pedir que a IA indique a seção do documento aumentou muito a precisão das respostas.


###  Prompt 3 — Chain-of-Thought (Avançado)

**Objetivo:** Comparar abordagens de alinhamento de IA

```
Pense passo a passo: 
1. O que é RLHF (Reinforcement Learning from Human Feedback)?
2. O que é Constitutional AI (CAI)?
3. Quais são as principais diferenças entre essas abordagens?
4. Segundo os documentos, qual delas parece mais escalável?
Cite as fontes para cada passo.
```

**Resposta obtida:** O formato step-by-step funcionou muito bem. O NotebookLM estruturou uma comparação clara entre o paper do Anthropic (CAI) e referências ao RLHF no survey de LLMs.

** Insight:** Prompts com numeração explícita e instrução "pense passo a passo" produzem respostas mais organizadas e rastreáveis.


###  Prompt 4 — Criação de Glossário (Aplicado)

**Objetivo:** Extrair vocabulário técnico das fontes

```
Com base em todos os documentos carregados, crie um glossário 
com os 15 termos técnicos mais importantes da IA Generativa. 
Para cada termo: (1) definição em português, (2) exemplo prático, 
(3) documento de origem.
```

**Resposta obtida:** Gerou um glossário muito completo. Alguns termos tiveram definições um pouco longas demais.

** Dificuldade:** A IA às vezes misturava definições de múltiplas fontes sem distingui-las claramente.

** Ajuste:**

```
[Mesmo prompt anterior] — Limite cada definição a no máximo 2 frases. 
Se um termo aparecer em mais de um documento, mencione os dois.
```


###  Prompt 5 — Geração de Questões de Revisão (Meta-prompt)

**Objetivo:** Criar material de revisão ativa

```
Atue como um professor universitário de Ciência da Computação. 
Com base nos documentos, crie 10 questões de múltipla escolha 
(com gabarito e justificativa) para testar o entendimento sobre 
os fundamentos de LLMs e IA Generativa. Nível de dificuldade: intermediário.
```

**Resposta obtida:** Qualidade surpreendente! As questões abordaram transformer, attention, tokenização, RLHF e alucinações — todas rastreadas às fontes.

**Aprendizado:** Dar um papel/persona à IA ("Atue como um professor") melhora significativamente a qualidade pedagógica da resposta.


#### Módulo 1: Fundamentos da IA Generativa

**O que é IA Generativa?**  
IA Generativa refere-se a sistemas de inteligência artificial capazes de criar novos conteúdos — texto, imagens, código, áudio e vídeo — a partir de padrões aprendidos em grandes volumes de dados. Diferente dos sistemas discriminativos (que classificam ou predizem), os modelos generativos aprendem a distribuição dos dados de treinamento para gerar amostras novas e coerentes.

**A Arquitetura Transformer (2017)**  
Introduzida por Vaswani et al., a arquitetura Transformer revolucionou o processamento de linguagem natural ao abandonar as redes recorrentes (RNNs) em favor do mecanismo de **self-attention**. Isso permite que o modelo considere o contexto de toda a sequência simultaneamente — não palavra por palavra — tornando o treinamento paralelizável e muito mais eficiente.

*Componentes principais:*
- **Encoder**: processa a entrada e cria representações contextuais
- **Decoder**: gera a saída token por token, atendendo ao encoder
- **Multi-head Attention**: permite ao modelo focar em diferentes partes do contexto simultaneamente
- **Positional Encoding**: injeta informação sobre a posição dos tokens na sequência

---

#### Módulo 2: Large Language Models (LLMs)

**O que são LLMs?**  
Large Language Models são modelos Transformer treinados em quantidades massivas de texto (bilhões a trilhões de tokens) para prever o próximo token em uma sequência. Através dessa tarefa simples de pré-treinamento, os modelos emergem com capacidades surpreendentes: raciocínio, tradução, programação, resumo e geração criativa.

**Escala e Leis de Escala (Scaling Laws)**  
Pesquisas da OpenAI e DeepMind demonstraram que o desempenho dos LLMs melhora de forma previsível com o aumento de: (1) parâmetros do modelo, (2) volume de dados de treinamento e (3) poder computacional. Isso levou à corrida por modelos cada vez maiores.

**Etapas de Desenvolvimento de um LLM:**
1. **Pré-treinamento**: aprendizado não-supervisionado em corpus massivo (web, livros, código)
2. **Fine-tuning supervisionado (SFT)**: ajuste em exemplos curados de instrução-resposta
3. **RLHF**: refinamento com feedback humano para alinhar o comportamento ao desejado
4. **Avaliação e red-teaming**: testes de segurança e qualidade antes do deploy

---

#### Módulo 3: Alinhamento e Ética em IA

**O Problema do Alinhamento**  
Garantir que LLMs se comportem de acordo com valores e intenções humanas é um dos maiores desafios da área. Modelos não alinhados podem gerar desinformação, conteúdo prejudicial ou ser manipulados por usuários mal-intencionados.

**RLHF — Reinforcement Learning from Human Feedback**  
Técnica pioneirada pela OpenAI que usa preferências humanas para treinar um modelo de recompensa, que por sua vez guia o ajuste fino do LLM via reinforcement learning. Produz modelos mais úteis e menos nocivos, mas é custosa e difícil de escalar.

**Constitutional AI (Anthropic, 2022)**  
Abordagem alternativa da Anthropic que define um conjunto de princípios (uma "constituição") para guiar o comportamento do modelo. O próprio modelo AI avalia suas respostas contra esses princípios, reduzindo a dependência de anotadores humanos e permitindo maior escalabilidade.

**Principais Riscos da IA Generativa:**
- **Alucinações**: geração de informações falsas apresentadas com confiança
- **Vieses**: reprodução e amplificação de preconceitos presentes nos dados de treinamento
- **Desinformação**: criação de deepfakes, textos e imagens enganosas
- **Privacidade**: memorização de dados sensíveis do treinamento






Este projeto foi desenvolvido como atividade do bootcamp da **DIO (Digital Innovation One)**.  
Todas as fontes utilizadas são públicas e de acesso aberto (open access).

* Se este repositório foi útil para você, deixe uma estrela!*
