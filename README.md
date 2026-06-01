# urban-safety

Visão Geral

O Urban Safety ES é um projeto de Ciência de Dados, Engenharia de Dados e Inteligência Artificial que tem como objetivo coletar automaticamente notícias de ocorrências policiais publicadas em veículos de comunicação do Espírito Santo, transformar essas informações em dados estruturados e gerar indicadores geográficos de risco urbano.

A proposta surgiu da necessidade de criar uma solução capaz de responder perguntas como:

Quais regiões apresentam maior incidência de crimes?
Como a criminalidade está evoluindo ao longo do tempo?
Existe concentração espacial de determinados tipos de ocorrência?
É possível criar um índice preditivo de risco para auxiliar cidadãos, empresas e órgãos públicos?

O projeto utiliza técnicas de:

Web Scraping
Processamento de Linguagem Natural (NLP)
Geoprocessamento
Engenharia de Dados
Machine Learning
Sistemas de Informação Geográfica (GIS)
Objetivo Principal

Transformar notícias policiais não estruturadas em uma base de dados georreferenciada capaz de alimentar modelos de análise e previsão de risco urbano.

Fluxo esperado:

Notícias
    ↓
Extração automática
    ↓
Dados estruturados
    ↓
Geolocalização
    ↓
Banco de dados
    ↓
Modelo de risco
    ↓
Mapa interativo
Problema Identificado

Grande parte das informações sobre segurança pública encontra-se dispersa em portais de notícias.

Embora existam bases oficiais de criminalidade, muitas vezes elas:

Possuem atraso na divulgação;
Não apresentam granularidade suficiente;
Não fornecem atualizações em tempo real.

As notícias policiais representam uma fonte complementar de informações que pode ser explorada por técnicas modernas de IA e NLP.

Escopo Inicial
Região

Estado do Espírito Santo.

Fontes de Dados

As primeiras fontes consideradas para o projeto são:

G1 Espírito Santo
A Gazeta
Tribuna Online
Folha Vitória

A coleta será realizada preferencialmente por:

páginas de categorias;
páginas de tags;
seções de polícia;
seções de segurança pública.
Arquitetura Geral
┌────────────────────┐
│ Fontes de Notícias │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Coleta de URLs     │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Extração de Texto  │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Limpeza de Dados   │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ NLP e Entidades    │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Geocodificação     │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Banco de Dados     │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Modelo de Risco    │
└─────────┬──────────┘
          │
          ▼
┌────────────────────┐
│ Dashboard / API    │
└────────────────────┘
Pipeline de Dados
1. Coleta de Notícias

Responsável por localizar novas matérias publicadas.

Entradas:

URLs de categorias policiais
URLs de tags específicas

Saída:

{
  "url": "https://site.com/noticia123"
}
2. Extração de Conteúdo

Responsável por capturar:

título;
data;
corpo da notícia;
autor;
categoria.

Exemplo:

{
  "title": "Homem é preso após assalto",
  "date": "2026-05-20",
  "content": "..."
}
3. Limpeza de Texto

Remoção de:

caracteres especiais;
scripts;
propagandas;
elementos HTML;
espaços excedentes.
4. Extração de Entidades

Primeira versão:

palavras-chave;
regras;
expressões regulares.

Versão futura:

spaCy;
modelos NER;
LLMs.

Campos previstos:

{
  "crime_type": "assalto",
  "city": "Vitória",
  "neighborhood": "Jardim Camburi",
  "date": "2026-05-20"
}
5. Geocodificação

Conversão de:

Jardim Camburi, Vitória

para

Latitude: -20.257
Longitude: -40.264

Ferramenta inicial:

Nominatim
OpenStreetMap
6. Persistência

Estrutura mínima:

{
  "crime": "assalto",
  "location": "Jardim Camburi",
  "latitude": -20.257,
  "longitude": -40.264,
  "date": "2026-05-20"
}

Evolução futura:

PostgreSQL
PostGIS
Estrutura de Diretórios
urban-safety-es/
│
├── README.md
├── requirements.txt
├── .env.example
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
│
├── src/
│   ├── core/
│   │   ├── config.py
│   │   └── logger.py
│   │
│   ├── scraper/
│   │   ├── collect_links.py
│   │   └── extract_article.py
│   │
│   ├── processing/
│   │   └── clean.py
│   │
│   ├── nlp/
│   │   └── extract_entities.py
│   │
│   ├── geo/
│   │   └── geocode.py
│   │
│   ├── models/
│   │   └── risk_model.py
│   │
│   ├── services/
│   │   └── risk_service.py
│   │
│   ├── pipelines/
│   │   └── run_scraper.py
│   │
│   └── api/
│       └── main.py
│
├── models/
├── tests/
└── docker/
Roadmap
Fase 1 — MVP
 Coletar notícias
 Extrair texto
 Estruturar dados
 Geocodificar ocorrências
 Salvar em banco

Resultado:

Mapa simples de ocorrências.

Fase 2 — Inteligência
 Classificação automática de crimes
 Extração avançada com NLP
 Correção automática de localizações
 Banco geoespacial

Resultado:

Base histórica confiável.

Fase 3 — Predição
 Construção do índice de risco
 Análise temporal
 Heatmaps
 Machine Learning

Resultado:

Modelo de risco urbano.

Fase 4 — Produto
 API pública
 Dashboard web
 Consulta por endereço
 Alertas automáticos

Resultado:

Plataforma completa de monitoramento urbano.

Próximo Passo Estratégico

A etapa mais importante do projeto não é o scraping, mas a criação de um modelo matemático de risco.

O objetivo futuro será transformar ocorrências históricas em um Risk Score, considerando:

frequência dos crimes;
gravidade;
recência;
concentração geográfica;
tendências temporais.

Exemplo:

Score 0-20     → Baixo risco
Score 21-40    → Moderado
Score 41-60    → Alto
Score 61-80    → Muito alto
Score 81-100   → Crítico

Esse será o principal diferencial do Urban Safety ES, permitindo sair da simples visualização de ocorrências para a construção de um sistema preditivo de segurança urbana.

Autor

Projeto idealizado para estudo e desenvolvimento de competências em:

Engenharia de Dados
Ciência de Dados
Inteligência Artificial
Geoprocessamento
Machine Learning
Desenvolvimento de Produtos Analíticos

Objetivo final: criar uma plataforma capaz de transformar notícias públicas em inteligência geográfica acionável para análise de risco urbano no Espírito Santo.
