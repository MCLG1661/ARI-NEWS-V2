# Arquitetura — ARI NEWS V2

## Visão Geral

O ARI NEWS V2 utiliza um pipeline de agentes para transformar parâmetros fornecidos pelo usuário em uma página executiva de inteligência estratégica baseada em notícias reais.

### Fluxo principal

Setor + Região + Data  
↓  
Buscador de Notícias + Search Web  
↓  
Curador Estratégico  
↓  
Formatador de Dados  
↓  
Gerador da Webpage

Em paralelo:

Setor / Contexto  
↓  
Criador de Imagens  
↓  
Gerador da Webpage

### Arquitetura conceitual

**Entrada → Retrieval → Curadoria → Estruturação → Apresentação**

## Componentes

### User Inputs
Recebe os parâmetros de contexto da análise:

- Setor
- Região
- Data de referência

### Buscador de Notícias
Realiza a pesquisa web e recupera notícias relacionadas aos parâmetros informados pelo usuário.

### Curador Estratégico
Avalia os resultados recuperados, seleciona conteúdos relevantes e produz contexto e relevância estratégica.

### Formatador de Dados
Estrutura os dados editoriais para consumo pela camada de apresentação.

### Criador de Imagens
Gera uma imagem editorial relacionada ao contexto analisado.

### Gerador da Webpage
Consolida dados editoriais, contexto e imagem em uma interface executiva contendo notícias, fontes, resumos, análise estratégica e acesso às páginas originais.

## Integridade das fontes

Um requisito central do ARI NEWS V2 é preservar a URL original recuperada durante a pesquisa.

A URL percorre o pipeline sem reconstrução ou inferência:

Search Web → Buscador → Curador → Formatador → Webpage

Caso não exista uma URL específica e verificável para uma notícia, ela não deve ser utilizada.
