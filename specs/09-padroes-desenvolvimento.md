# 🏗️ Padrões de Desenvolvimento

> Documento: 09  
> Projeto: Assistente VIAZA  
> Versão: 1.0.0

---

# Objetivo

Este documento estabelece os padrões de desenvolvimento utilizados no Assistente VIAZA.

Seu objetivo é garantir consistência, qualidade, organização e facilidade de manutenção durante toda a evolução do projeto.

Todos os desenvolvedores deverão seguir estas diretrizes.

---

# Arquitetura

O projeto utilizará uma arquitetura modular em camadas.

Interface

↓

Aplicação

↓

Domínio

↓

Infraestrutura

↓

Banco de Dados

Cada camada deverá possuir responsabilidade única.

---

# Estrutura do Projeto

```
src/
│
├── app/
├── assets/
├── components/
├── config/
├── core/
├── database/
├── interfaces/
├── modules/
├── services/
├── shared/
├── types/
└── utils/
```

Cada diretório deverá conter apenas arquivos relacionados à sua responsabilidade.

---

# Organização dos Módulos

Cada módulo deverá seguir o mesmo padrão estrutural.

Exemplo:

```
MotorAnalise/

MotorAnaliseController.ts

MotorAnaliseService.ts

MotorAnaliseRepository.ts

MotorAnaliseValidator.ts

MotorAnaliseTypes.ts

MotorAnaliseUtils.ts
```

---

# Convenção de Nomes

## Arquivos

Utilizar PascalCase.

Exemplos:

MotorAnalise.ts

PesquisaService.ts

DashboardController.ts

---

## Classes

Sempre PascalCase.

Exemplo:

MotorAnaliseService

EmailService

WhatsappService

---

## Funções

Sempre camelCase.

Exemplo:

buscarTarifas()

gerarPdf()

enviarWhatsapp()

compararResultados()

---

## Variáveis

Sempre camelCase.

Exemplo:

numeroPedido

melhorTarifa

listaResultados

---

## Constantes

Sempre UPPER_SNAKE_CASE.

Exemplo:

MAX_TIMEOUT

DEFAULT_PORTAL

MAX_RETRY

---

# Interfaces

Toda interface deverá iniciar com I.

Exemplo:

IMotorAnaliseService

IPesquisaRepository

IEmailService

---

# Responsabilidade Única

Cada classe deverá possuir apenas uma responsabilidade.

Exemplos:

PesquisaService → Pesquisa tarifas.

EmailService → Envia emails.

WhatsappService → Envia mensagens.

PdfService → Gera PDFs.

---

# SOLID

Todo o desenvolvimento deverá seguir os princípios SOLID.

- Single Responsibility
- Open/Closed
- Liskov Substitution
- Interface Segregation
- Dependency Inversion

---

# Clean Code

Priorizar:

- Código legível
- Métodos curtos
- Baixo acoplamento
- Alta coesão
- Reutilização
- Simplicidade

Evitar duplicação de código.

---

# Tratamento de Erros

Todos os erros deverão ser tratados.

Nunca utilizar:

```
catch {}
```

Registrar:

- Mensagem
- Origem
- Data
- Stack Trace

Exibir mensagens amigáveis ao usuário.

---

# Validação

Toda entrada deverá ser validada antes do processamento.

Nunca confiar em dados externos.

---

# Comunicação Assíncrona

Utilizar:

- async
- await

Evitar callbacks e Promises encadeadas desnecessariamente.

---

# Logs

Utilizar Winston.

Níveis:

INFO

WARN

ERROR

DEBUG

Todos os logs deverão possuir:

- Data
- Hora
- Módulo
- Operação
- Resultado

---

# Banco de Dados

Todas as tabelas deverão possuir:

- id
- createdAt
- updatedAt

Relacionamentos deverão utilizar chaves estrangeiras.

---

# Git Flow

Utilizar as seguintes branches:

main

develop

feature/*

fix/*

release/*

hotfix/*

---

# Commits

Seguir Conventional Commits.

Exemplos:

feat:

fix:

docs:

style:

refactor:

test:

chore:

---

# Pull Requests

Antes da aprovação:

- Código compilando
- Sem erros de lint
- Testes executados
- Documentação atualizada
- Revisão concluída

---

# Testes

Cada módulo deverá possuir:

- Testes Unitários
- Testes de Integração
- Testes End-to-End (quando aplicável)

---

# Interface

Utilizar componentes reutilizáveis.

Exemplos:

- Botões
- Inputs
- Cards
- Modais
- Tabelas
- Gráficos

---

# Documentação

Toda funcionalidade deverá possuir documentação contendo:

- Objetivo
- Entradas
- Saídas
- Dependências
- Fluxo
- Exemplos

---

# Performance

Evitar:

- Loops desnecessários
- Consultas repetidas
- Código morto
- Dependências sem utilização

Priorizar eficiência e legibilidade.

---

# Segurança

Nunca:

- Armazenar senhas em texto puro
- Versionar arquivos .env
- Registrar dados sensíveis em logs
- Compartilhar credenciais

---

# Escalabilidade

A arquitetura deverá permitir:

- Inclusão de novos módulos
- Inclusão de novos portais
- Inclusão de novas companhias aéreas
- Inclusão de novos relatórios
- Inclusão de novos dashboards

Sem necessidade de alterar módulos existentes.

---

# Definition of Done

Uma funcionalidade será considerada concluída quando:

- Requisitos implementados
- Testes aprovados
- Código revisado
- Documentação atualizada
- Logs implementados
- Tratamento de erros concluído
- Build executado sem falhas

---

# Checklist para Desenvolvimento

Antes de finalizar uma tarefa, verificar:

- Código organizado
- Sem duplicação
- Métodos pequenos
- Testes executados
- Documentação atualizada
- Logs implementados
- Tratamento de erros implementado
- Convenções de nomenclatura respeitadas

---

# Conclusão

Todos os desenvolvedores deverão seguir este padrão para garantir que o Assistente VIAZA permaneça organizado, escalável, seguro e de fácil manutenção ao longo de sua evolução.