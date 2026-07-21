# 🏗️ Arquitetura do Sistema

> Documento: 02
> Projeto: Assistente VIAZA
> Versão: 1.0.0

---

# 📖 Objetivo

Este documento define a arquitetura de software do Assistente VIAZA.

Seu objetivo é padronizar a estrutura do sistema, facilitar a manutenção do código e permitir que novos módulos sejam adicionados sem comprometer os componentes existentes.

A arquitetura foi projetada seguindo princípios modernos de desenvolvimento de software, priorizando modularidade, escalabilidade, reutilização e baixo acoplamento entre os componentes.

---

# 🎯 Objetivos da Arquitetura

A arquitetura deverá garantir:

- Organização do código.
- Separação clara de responsabilidades.
- Facilidade para manutenção.
- Facilidade para testes.
- Escalabilidade.
- Reutilização de componentes.
- Baixo acoplamento entre módulos.
- Alta coesão.
- Facilidade para inclusão de novos portais.
- Facilidade para inclusão de novas regras de negócio.

---

# 🏛️ Visão Geral

O Assistente VIAZA será dividido em camadas independentes.

```text
┌─────────────────────────────────────────────┐
│              Interface (UI)                 │
└─────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────┐
│             Application Layer               │
└─────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────┐
│              Domain Layer                   │
└─────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────┐
│           Infrastructure Layer              │
└─────────────────────────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────┐
│                Database                     │
└─────────────────────────────────────────────┘
```

Cada camada possui responsabilidades específicas e não deve acessar diretamente camadas que não estejam imediatamente abaixo.

---

# 🧱 Arquitetura Modular

O sistema será composto por módulos independentes.

Cada módulo deverá possuir responsabilidade única.

Exemplo:

```
Motor de Análise

↓

Pesquisa

↓

Comparador

↓

WhatsApp

↓

Email

↓

PDF

↓

Registro
```

Cada módulo poderá evoluir independentemente.

---

# 📂 Estrutura do Projeto

```
src/

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

---

# 📁 Descrição das Pastas

## app/

Contém a inicialização da aplicação.

Responsável por:

- Inicialização do Electron.
- Inicialização do React.
- Carregamento das configurações.

---

## assets/

Arquivos estáticos.

Exemplos:

- imagens
- ícones
- logos
- fontes

---

## components/

Componentes reutilizáveis da interface.

Exemplos:

- Botões
- Inputs
- Cards
- Tabelas
- Modais
- Gráficos

---

## config/

Arquivos de configuração.

Exemplos:

- Variáveis de ambiente
- Configuração SMTP
- Configuração dos Portais
- Configuração do Banco

---

## core/

Núcleo do sistema.

Contém:

- Motor de Análise
- Motor de Regras
- Orquestrador
- Classificação

É o coração do Assistente VIAZA.

---

## database/

Responsável pelo banco de dados.

Contém:

- Prisma
- SQLite
- Migrations
- Seeds

---

## interfaces/

Interfaces TypeScript.

Exemplo:

```
IPesquisaService

IWhatsappService

IEmailService

IPdfService
```

---

## modules/

Cada funcionalidade será implementada como um módulo independente.

Exemplo:

```
Pesquisa/

Comparador/

Dashboard/

Historico/

Registro/

Whatsapp/

Email/

Pdf/
```

---

## services/

Serviços responsáveis por comunicação externa.

Exemplos:

- SMTP
- WhatsApp
- Wooba
- Kontrip
- LATAM

---

## shared/

Componentes compartilhados entre módulos.

Exemplos:

- Helpers
- Constantes
- Tipagens
- Utilitários

---

## utils/

Funções auxiliares reutilizáveis.

Exemplo:

- Formatação
- Datas
- Máscaras
- Conversões

---

# 🔄 Fluxo Arquitetural

```
Operador

↓

Leitura da OP

↓

Motor de Análise

↓

Motor de Regras

↓

Classificação

↓

Pesquisa

↓

Comparador

↓

Busca de Dados

↓

Tela de Conferência

↓

WhatsApp

↓

Email

↓

PDF

↓

Registro

↓

Dashboard

↓

Histórico
```

Cada módulo deverá receber apenas as informações necessárias.

---

# 🧠 Motor de Análise

Responsável por interpretar a OP.

Funções:

- Ler observações.
- Detectar retarificações.
- Identificar padrões.
- Classificar mensagens.

Saída:

Objeto estruturado para o Motor de Regras.

---

# ⚙️ Motor de Regras

Responsável por aplicar regras configuráveis.

Exemplos:

Se encontrar determinada mensagem:

↓

Pesquisar Portais

↓

Comparar Tarifas

↓

Enviar WhatsApp

↓

Enviar Email

↓

Gerar PDF

---

# 🔍 Pesquisa

Responsável por consultar automaticamente todos os portais.

Inicialmente:

- Wooba
- Kontrip
- Companhia aérea

No futuro:

- Novos portais poderão ser adicionados sem alterar os módulos existentes.

---

# ⚖️ Comparador

Recebe todos os resultados.

Funções:

- Comparar tarifas.
- Identificar menor valor.
- Calcular economia.
- Ordenar resultados.

---

# 📨 Comunicação

Após aprovação do operador.

Executará:

WhatsApp

↓

Email

↓

PDF

---

# 📊 Dashboard

Receberá dados do módulo Registro.

Indicadores:

- Total de OPs.
- Retarificações.
- Economia.
- Tempo médio.
- Portais mais utilizados.

---

# 🗄️ Registro

Todas as operações deverão ser registradas.

Exemplo:

- Data
- Hora
- Operador
- Pedido
- Resultado
- Portal utilizado
- Melhor tarifa

---

# 🔌 Integrações

O sistema deverá integrar-se com:

- Sistema VIAZA
- Wooba
- Kontrip
- Companhias Aéreas
- Outlook (SMTP)
- WhatsApp Web

Cada integração deverá possuir um serviço dedicado.

---

# 🧩 Princípios Arquiteturais

Todo o sistema deverá seguir:

- SOLID
- Clean Architecture
- Clean Code
- DRY
- KISS
- Separation of Concerns

---

# 🚀 Escalabilidade

A arquitetura foi projetada para permitir:

- Inclusão de novos portais.
- Inclusão de novas companhias.
- Inclusão de novos módulos.
- Inclusão de novos relatórios.
- Inclusão de novos dashboards.
- Inclusão de novos meios de comunicação.

Sem necessidade de alterar módulos existentes.

---

# 🔒 Segurança Arquitetural

Cada módulo deverá:

- Validar entradas.
- Tratar exceções.
- Registrar logs.
- Não acessar diretamente outros módulos.
- Utilizar apenas interfaces públicas.

---

# 🧪 Testabilidade

Todos os módulos deverão permitir:

- Testes Unitários.
- Testes de Integração.
- Mock de dependências.
- Injeção de Dependências.

---

# 📈 Evolução da Arquitetura

A arquitetura foi planejada para suportar futuras implementações, como:

- Inteligência Artificial para interpretação de mensagens.
- APIs oficiais das companhias aéreas.
- Aplicativo Mobile.
- Dashboard Web.
- Integração com Microsoft Teams.
- Integração com Slack.
- API pública para integração com outros sistemas.
- Relatórios analíticos.
- Machine Learning para sugestão automática da melhor tarifa.

---

# 📌 Conclusão

A arquitetura do Assistente VIAZA foi projetada para ser modular, escalável e de fácil manutenção.

Cada módulo possui responsabilidades bem definidas e comunica-se por meio de interfaces padronizadas, permitindo que novas funcionalidades sejam adicionadas sem comprometer a estabilidade da aplicação.

Esta arquitetura servirá como base para todas as etapas de desenvolvimento do projeto e deverá ser seguida por toda a equipe técnica.
