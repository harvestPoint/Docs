# HarvestPoint

> Plataforma inteligente para monitoramento climático e apoio à decisão no cultivo e comercialização de frutas no Vale do São Francisco.

## Sobre o projeto

O HarvestPoint é uma solução de monitoramento e análise de dados voltada à produção de frutas no Vale do São Francisco.

A plataforma tem como objetivo integrar dados provenientes de sensores IoT instalados em áreas de produção com informações produtivas, climáticas, comerciais e logísticas, permitindo aos produtores e gestores acompanhar as condições das plantações e obter apoio à decisão sobre colheita e exportação.

O projeto será desenvolvido como parte do Projeto Integrador e será evoluído em duas etapas.

## Objetivos

### Objetivo geral

Desenvolver uma plataforma integrada de monitoramento e análise de dados para apoiar decisões relacionadas ao cultivo, colheita e exportação de frutas.

### Objetivos específicos

* Monitorar temperatura e umidade das áreas produtivas;
* Centralizar informações de produtores e propriedades;
* Gerenciar culturas e lotes de produção;
* Gerenciar sensores IoT;
* Armazenar o histórico das condições climáticas;
* Disponibilizar dashboards e gráficos;
* Identificar condições climáticas fora dos parâmetros recomendados;
* Integrar informações de mercado e logística;
* Analisar dados históricos;
* Apoiar a identificação da janela adequada de colheita;
* Apoiar decisões relacionadas à janela de exportação.

## Arquitetura

A arquitetura inicial da solução será baseada em uma aplicação cliente-servidor.

```text
ESP32
  │
  │ Dados de temperatura e umidade
  ▼
ThingSpeak
  │
  │ API
  ▼
Backend REST
  │
  ├──────────────► PostgreSQL
  │
  ▼
React / PWA
  │
  ▼
Dashboard
```

Na etapa inicial, o ThingSpeak será utilizado como camada de comunicação e armazenamento temporário dos dados provenientes dos dispositivos IoT. O backend será responsável por consumir, validar e persistir os dados relevantes no banco de dados da aplicação.

A arquitetura foi definida de forma desacoplada para permitir uma futura substituição ou expansão da camada de comunicação IoT, incluindo a utilização de MQTT com um broker próprio.

## Tecnologias

### Hardware / IoT

* ESP32
* Sensor de temperatura e umidade

### Comunicação IoT

* ThingSpeak
* HTTP/REST
* MQTT — possibilidade de expansão

### Backend

* Node.js
* TypeScript
* API REST

### Frontend

* React
* PWA

### Banco de dados

* PostgreSQL
* TimescaleDB — possibilidade de utilização para séries temporais

### Data Science

* Python
* Pandas
* NumPy
* Scikit-learn
* Matplotlib

### Infraestrutura

* GitHub
* Ambiente de nuvem a ser definido para o MVP
* CI/CD com GitHub Actions — evolução prevista

## Principais módulos

### Usuários

* Cadastro
* Login
* Autenticação
* Controle de acesso

### Produtores

* Cadastro de produtores e empresas
* Associação com propriedades

### Propriedades

* Cadastro de propriedades rurais
* Localização
* Área
* Status

### Culturas

* Cadastro de frutas
* Variedades
* Parâmetros climáticos recomendados
* Ciclo médio de produção

### Lotes

* Cadastro das áreas de produção
* Cultura cultivada
* Data de plantio
* Previsão de colheita
* Situação do lote

### Sensores

* Cadastro de dispositivos
* Associação com propriedades e lotes
* Status
* Identificação do dispositivo

### Dados climáticos

* Temperatura
* Umidade
* Data e hora da leitura
* Histórico das medições

### Mercado

* Cultura
* Mercado de destino
* Preço médio
* Moeda
* Demanda estimada

### Logística

* Origem
* Destino
* Modal
* Tempo estimado
* Custo
* Transportadora
* Situação

### Dashboard

* Temperatura atual
* Umidade atual
* Médias climáticas
* Sensores ativos
* Quantidade de leituras
* Histórico climático
* Alertas

## Fluxo principal

```text
Coleta
  ↓
ESP32
  ↓
ThingSpeak
  ↓
API REST
  ↓
Validação
  ↓
PostgreSQL
  ↓
Processamento
  ↓
Dashboard
```

Em uma etapa posterior:

```text
Dados climáticos
      +
Dados produtivos
      +
Dados de mercado
      +
Dados logísticos
      ↓
Tratamento
      ↓
Análise de dados
      ↓
Modelo / regras preditivas
      ↓
Recomendação
      ↓
Dashboard executivo
```

## Estrutura do projeto

```text
harvest-point/
│
├── backend/
├── frontend/
├── iot/
├── data-science/
├── database/
├── docs/
└── .github/
```

## Entregas

### Primeira entrega — MVP

Data prevista: **13/10/2026**

A primeira etapa contempla:

* Aplicação web responsiva/PWA;
* API REST;
* Banco de dados;
* Cadastro e autenticação;
* Cadastro de produtores;
* Cadastro de propriedades;
* Cadastro de culturas;
* Cadastro de lotes;
* Cadastro de sensores;
* Registro de leituras;
* Integração com a camada IoT;
* Dados de mercado e logística;
* Dashboard climático;
* Histórico dos dados;
* Gráficos e filtros;
* Alertas climáticos;
* Documentação técnica inicial.

### Segunda entrega — solução completa

Data prevista: **08/12/2026**

A segunda etapa contempla:

* Deploy em nuvem;
* Banco de dados em nuvem;
* Pipeline de dados;
* Tratamento e análise dos dados;
* Indicadores produtivos;
* Recomendação da janela de colheita;
* Recomendação da janela de exportação;
* Dashboard executivo;
* RBAC;
* Segurança;
* Auditoria;
* Testes automatizados;
* CI/CD;
* Monitoramento;
* Relatório de segurança e qualidade;
* Documentação final;
* Demonstração completa da solução.

## Status

**Em desenvolvimento — fase de definição da arquitetura e preparação do MVP.**

## Equipe

| Integrante | Responsabilidade        |
| ---------- | ----------------------- |
| A definir  | Backend / API           |
| A definir  | Frontend / PWA          |
| A definir  | IoT / ESP32             |
| A definir  | Banco de dados          |
| A definir  | Data Science            |
| A definir  | Infraestrutura / DevOps |

## Documentação

* [Arquitetura](docs/arquitetura.md)
* [Modelo de Dados](docs/modelo-dados.md)
* [API](docs/api.md)
* [Requisitos](docs/requisitos.md)
* [Decisões Técnicas](docs/decisoes-tecnicas.md)
