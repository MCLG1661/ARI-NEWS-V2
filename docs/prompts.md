# Engenharia de Prompts — ARI NEWS V2

## Visão Geral

O ARI NEWS V2 utiliza prompts especializados para separar responsabilidades ao longo do pipeline.

Cada etapa recebe um contexto específico e produz uma saída destinada ao próximo componente, reduzindo sobreposição de responsabilidades e facilitando validação e debugging.

## 1. Buscador de Notícias

### Objetivo

Localizar notícias reais e relevantes considerando:

- setor;
- região;
- data de referência.

### Estratégia

O Buscador utiliza pesquisa web para recuperar conteúdos relacionados ao contexto informado pelo usuário.

A etapa prioriza:

- aderência temática;
- aderência geográfica;
- proximidade temporal;
- identificação da fonte;
- preservação da URL original.

### Regra crítica de integridade

A URL utilizada pelo pipeline deve corresponder à página efetivamente recuperada durante a pesquisa.

O agente não deve:

- reconstruir URLs;
- deduzir endereços a partir do título;
- completar URLs incompletas;
- criar links com base na estrutura provável de um domínio.

Quando uma URL específica e verificável não estiver disponível, a notícia deve ser descartada.

---

## 2. Curador Estratégico

### Objetivo

Transformar resultados de pesquisa em informação relevante para tomada de decisão.

### Responsabilidades

- avaliar aderência ao setor;
- avaliar aderência à região;
- selecionar notícias relevantes;
- sintetizar o conteúdo;
- identificar implicações estratégicas;
- preservar fonte, data e URL.

O Curador não é responsável por realizar uma nova pesquisa ou reconstruir links.

---

## 3. Formatador de Dados

### Objetivo

Converter a saída editorial do Curador em uma estrutura consistente para apresentação.

### Estrutura esperada

Cada notícia deve preservar:

- título;
- fonte;
- data;
- resumo;
- relevância estratégica;
- URL original.

O Formatador atua sobre a estrutura da informação e não sobre a origem dos dados.

---

## 4. Criador de Imagens

### Objetivo

Gerar um elemento visual editorial coerente com o contexto da análise.

A imagem deve complementar a apresentação sem interferir na integridade das informações recuperadas.

---

## 5. Gerador da Webpage

### Objetivo

Transformar os dados estruturados em uma interface executiva de inteligência estratégica.

A página apresenta:

- identidade ARI NEWS;
- setor;
- região;
- data de referência;
- imagem editorial;
- destaques editoriais;
- fonte e data;
- resumo;
- relevância estratégica;
- acesso à notícia original.

---

## Princípios de Design dos Prompts

A arquitetura segue cinco princípios:

1. **Separação de responsabilidades** — cada componente possui uma função específica.
2. **Grounding** — notícias são baseadas em resultados recuperados da web.
3. **Rastreabilidade** — a fonte original acompanha a informação ao longo do pipeline.
4. **Não fabricação de URLs** — links não podem ser inferidos ou reconstruídos.
5. **Saída estruturada** — informações são organizadas antes de chegar à camada de apresentação.

## Fluxo de Informação

```text
User Inputs
    ↓
Search / Retrieval
    ↓
Curadoria
    ↓
Estruturação
    ↓
Apresentação
