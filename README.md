# Prompt-Strategies-for-Bug-Detection-with-LLMs

# 🐞 Estratégias de Prompt para Detecção de Bugs com LLMs

Trabalho de conclusão da disciplina **Manutenção e Evolução de Software (MES)**  
Programa de Pós-Graduação em Ciência da Computação — UFMG  
Autores: Ester de Lima Pontes Andrade  e Larissa Duarta Santana

---

## 🎯 Objetivo

Este repositório contém um estudo experimental que investiga o impacto da **engenharia de prompts** na performance de modelos de linguagem (LLMs) para detectar **bugs sintáticos** em grandes arquivos de código Python. Para isso, utilizamos o benchmark **Bug In the Code Stack (BICS)** e propomos também **novas visualizações** para análise dos resultados.

Nosso foco está na melhoria da interpretabilidade e controle das ferramentas de manutenção automatizada baseadas em LLMs.

---

## 📦 Metodologia

### 🧠 Modelos de Linguagem Utilizados
Este estudo utilizará modelos de linguagem já avaliados no artigo original do benchmark BICS, a fim de manter consistência metodológica e permitir comparações diretas:

- `GPT-4o (OpenAI)`
- `Claude 3.5 (Anthropic)` 
- `Gemini 1.5 Pro (Google)`
- `LLaMA3-70B (Meta, open-source)`

Esses modelos serão acessados via LiteLLM API (como no benchmark original), ou diretamente por API oficial, conforme disponibilidade.

#### 🔍 Possibilidade adicional: 

Se houver tempo e recursos computacionais disponíveis, também realizaremos testes com modelos open-source como:

- `Mistral-7B-Instruct`
- `CodeLLaMA-13B`

Esses modelos serão executados localmente para fins de comparação e reprodutibilidade.


### 📚 Dataset Utilizado
- Benchmark **BICS**, baseado no [Python Alpaca Dataset](https://huggingface.co/datasets/tarunbisht/python-code-instructions-18k-alpaca)
- Contém código realista de várias áreas: ML, banco de dados, algoritmos
- Tipos de bug incluídos:
  - Falta de dois pontos, colchetes trocados, uso incorreto de aspas, etc.

### 🔄 Engenharia de Prompt
Testaremos variações como:
- **Zero-shot** (sem exemplo anterior)
- **Two-shot** (com exemplos, como no benchmark original)

Essas variações ajudam a entender como a **formulação da instrução** afeta o desempenho do modelo.

---

## 📊 Avaliação

A avaliação será dividida em duas partes: **quantitativa** (métrica de acerto) e **qualitativa** (análise manual das respostas), com foco em interpretar o desempenho dos modelos em diferentes variações de prompt.

---

### 📈 Avaliação Quantitativa

Nesta parte, vamos medir o desempenho dos modelos com base em sua capacidade de **localizar corretamente bugs sintáticos no código**.

#### 🔹 Métrica principal:
- **Acurácia**: porcentagem de vezes que o modelo acerta:
  - A **linha correta** onde o bug está inserido.
  - O **tipo de bug** (entre os 7 tipos definidos pelo benchmark BICS).

#### 🔹 Comparações previstas:
- Desempenho entre diferentes **modelos de linguagem** (ex: GPT-4o, Claude 3.5, LLaMA3-70B).
- Desempenho entre diferentes **variações de prompt** (zero-shot e two-shot).

#### 🔹 Visualizações que serão utilizadas:
- **Gráficos de barras**: para comparar a acurácia média por modelo e por tipo de prompt.
- **Gráficos por contexto (número de tokens)**: para observar se o tamanho do código influencia a precisão dos modelos.

> As visualizações serão geradas com ferramentas como Matplotlib ou Seaborn, priorizando representações simples e claras.

---

### 🧐 Avaliação Qualitativa

Nesta etapa, poderá ser feita uma análise manual/automática de exemplos selecionados, com o objetivo de observar **como os modelos se comportam além dos números**.

As respostas dos modelos (linha e tipo de bug) já são salvas automaticamente no benchmark, o que permite revisar e selecionar exemplos manualmente para análise qualitativa, onde pode ser classificados como:

- Casos onde o modelo acerta, mas com saída incompleta ou genérica.
- Casos em que o modelo erra, mas a saída parece plausível.
- Casos em que o modelo retorna algo fora do esperado.

> A análise qualitativa é importante para avaliar a **usabilidade prática** dos modelos em tarefas reais de manutenção de software.

---

## 📁 Organização do Repositório

---

## 📚 Referências

- Lee, H., Sharma, S., & Hu, B. (2024). Bug In The Code Stack: Can LLMs Find Bugs In Large Python Code Stacks? [arXiv:2406.15325](https://arxiv.org/abs/2406.15325)
- Tarun Bisht. python-code-instructions-18k-alpaca. HuggingFace Dataset. [https://huggingface.co/datasets/tarunbisht/python-code-instructions-18k-alpaca](https://huggingface.co/datasets/tarunbisht/python-code-instructions-18k-alpaca)
- Benchmark oficial: [https://github.com/HammingHQ/bug-in-the-code-stack](https://github.com/HammingHQ/bug-in-the-code-stack)

