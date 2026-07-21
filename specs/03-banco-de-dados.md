# 🗄️ Banco de Dados

> Documento: 03
> Projeto: Assistente VIAZA
> Versão: 1.0.0

---

# 📖 Objetivo

Este documento define a estrutura do banco de dados do Assistente VIAZA.

O banco de dados será responsável por armazenar todas as informações necessárias para o funcionamento da aplicação, incluindo registros das Ordens de Produção (OPs), pesquisas realizadas, resultados encontrados, usuários, configurações, histórico e logs do sistema.

A modelagem foi projetada para garantir organização, desempenho, escalabilidade e facilidade de manutenção.

---

# 🎯 Objetivos

O banco deverá permitir:

- Armazenar informações das OPs.
- Registrar todas as pesquisas realizadas.
- Registrar resultados encontrados nos portais.
- Armazenar histórico de operações.
- Controlar usuários e permissões.
- Registrar logs da aplicação.
- Salvar configurações do sistema.
- Permitir consultas rápidas.
- Garantir integridade dos dados.

---

# 🏗️ Tecnologia

O projeto utilizará:

- SQLite (desenvolvimento)
- Prisma ORM
- TypeScript

Futuramente poderá ser migrado para:

- PostgreSQL
- MySQL
- SQL Server

Sem necessidade de alterar a lógica da aplicação.

---

# 📊 Modelo Geral

```
Usuários
        │
        ▼
Ordens de Produção
        │
        ▼
Pesquisas
        │
        ▼
Resultados
        │
        ▼
Registro
        │
        ▼
Histórico
```

Além disso:

```
Configurações

↓

Aplicação

↓

Todos os módulos
```

---

# 📂 Tabelas

O banco será composto inicialmente pelas seguintes tabelas:

```
users

orders

searches

results

records

history

emails

whatsapp_messages

pdf_reports

logs

settings
```

---

# 👤 Tabela users

Responsável pelos usuários da aplicação.

Campos:

- id
- nome
- email
- login
- senha_hash
- perfil
- status
- createdAt
- updatedAt

Relacionamentos:

- Um usuário pode executar várias pesquisas.
- Um usuário pode gerar vários registros.

---

# 📄 Tabela orders

Representa uma Ordem de Produção.

Campos:

- id
- numeroOP
- numeroPedido
- companhia
- origem
- destino
- dataIda
- dataVolta
- passageiros
- observacoes
- status
- createdAt
- updatedAt

Relacionamentos:

Uma OP poderá possuir:

- várias pesquisas
- vários registros
- vários PDFs

---

# 🔎 Tabela searches

Representa cada pesquisa realizada.

Campos:

- id
- orderId
- usuarioId
- tipoPesquisa
- dataPesquisa
- status
- tempoExecucao

Relacionamentos:

Uma pesquisa pertence a:

- uma OP

Uma pesquisa possui:

- vários resultados

---

# 💰 Tabela results

Armazena os resultados encontrados.

Campos:

- id
- pesquisaId
- portal
- companhia
- valor
- taxas
- moeda
- disponibilidade
- trecho
- dataConsulta

Cada resultado representa uma tarifa encontrada.

---

# 📋 Tabela records

Registra todas as operações executadas.

Campos:

- id
- usuarioId
- orderId
- operacao
- resultado
- dataHora

Exemplos:

Pesquisa

WhatsApp enviado

Email enviado

PDF gerado

---

# 📚 Tabela history

Histórico completo da aplicação.

Campos:

- id
- registroId
- descricao
- dataHora
- usuario

Permite consultar toda a evolução da operação.

---

# 📧 Tabela emails

Registra todos os emails enviados.

Campos:

- id
- destinatario
- assunto
- status
- dataEnvio
- orderId

---

# 💬 Tabela whatsapp_messages

Registra todas as mensagens enviadas.

Campos:

- id
- grupo
- mensagem
- comercial
- status
- dataEnvio
- orderId

---

# 📄 Tabela pdf_reports

Armazena informações dos PDFs gerados.

Campos:

- id
- nomeArquivo
- caminho
- dataGeracao
- usuarioId
- orderId

O arquivo poderá permanecer no disco, enquanto o banco armazenará apenas suas informações.

---

# ⚙️ Tabela settings

Armazena as configurações da aplicação.

Campos:

- id
- chave
- valor
- descricao

Exemplos:

SMTP

WhatsApp

Portais

Tempo de atualização

Modelos de mensagens

---

# 📝 Tabela logs

Armazena eventos técnicos.

Campos:

- id
- nivel
- modulo
- mensagem
- stack
- dataHora

Níveis:

INFO

WARN

ERROR

DEBUG

---

# 🔗 Relacionamentos

```
User

↓

Orders

↓

Searches

↓

Results

↓

Records

↓

History
```

Também:

```
Orders

↓

Emails

↓

WhatsApp

↓

PDFs
```

---

# 📌 Chaves Primárias

Todas as tabelas possuirão:

```
id
```

Tipo:

UUID

ou

Autoincrement

(conforme implementação).

---

# 🔑 Chaves Estrangeiras

Relacionamentos previstos:

```
orders.userId

searches.orderId

searches.userId

results.searchId

records.orderId

records.userId

history.recordId

emails.orderId

whatsapp_messages.orderId

pdf_reports.orderId
```

---

# 📈 Índices

Criar índices para:

numeroPedido

numeroOP

companhia

portal

status

createdAt

usuarioId

orderId

Esses índices melhorarão o desempenho das consultas.

---

# 🔒 Integridade Referencial

Toda chave estrangeira deverá possuir restrições de integridade.

Exemplo:

Uma pesquisa não poderá existir sem uma OP.

Um resultado não poderá existir sem uma pesquisa.

Um PDF deverá pertencer a uma OP.

---

# 🧹 Exclusão

Utilizar Soft Delete quando possível.

Campos:

deletedAt

deletedBy

Dessa forma, nenhuma informação importante será perdida.

---

# 📦 Migrações

Toda alteração no banco deverá ser realizada através do Prisma Migrate.

Cada mudança deverá possuir:

- Nome
- Data
- Descrição

Nunca alterar tabelas manualmente em produção.

---

# 🌱 Seed

O projeto deverá possuir dados iniciais para desenvolvimento.

Exemplo:

Usuário Administrador

Perfis

Configurações padrão

Modelos de Email

Modelos de WhatsApp

---

# 🔐 Segurança

Nunca armazenar:

- Senhas em texto puro
- Tokens
- Cookies
- Sessões

Utilizar hash para senhas e proteger informações sensíveis.

---

# 📊 Performance

Boas práticas:

- Utilizar índices.
- Evitar consultas desnecessárias.
- Utilizar paginação.
- Utilizar filtros.
- Evitar duplicação de dados.

---

# 🔄 Backup

O sistema deverá permitir:

- Backup automático
- Backup manual
- Restauração

Itens incluídos:

- Banco de Dados
- Configurações
- Histórico
- Registros

---

# 🚀 Escalabilidade

O banco foi projetado para suportar:

- Novos portais
- Novas companhias
- Novos módulos
- Novos relatórios
- Novos dashboards

Sem necessidade de remodelagem significativa.

---

# 📌 Futuras Expansões

O banco poderá receber novas tabelas como:

- notifications
- audit_logs
- api_tokens
- integrations
- machine_learning
- ai_predictions
- scheduled_tasks
- reports
- attachments

Sem impactar a estrutura existente.

---

# ✅ Conclusão

A estrutura do banco de dados do Assistente VIAZA foi projetada para suportar todas as funcionalidades previstas, garantindo organização, integridade, desempenho e escalabilidade.

A utilização do Prisma ORM permitirá que futuras alterações na modelagem sejam realizadas de forma segura e controlada, mantendo o banco consistente e preparado para o crescimento da aplicação.
