# 📚 Histórico de Operações

> **Módulo:** Histórico de Operações
> **Documento:** 16
> **Versão:** 1.0.0

---

# 📖 Objetivo

O módulo de Histórico é responsável por disponibilizar ao operador e aos gestores uma visão completa de todas as operações realizadas pelo Assistente VIAZA.

Enquanto o módulo de Registro armazena tecnicamente todos os eventos do sistema, o Histórico organiza essas informações de forma clara e intuitiva, permitindo consultas, auditorias e análises posteriores.

O Histórico funciona como uma central de consulta das operações executadas.

---

# 🎯 Objetivos

O módulo deverá permitir:

- Consultar operações anteriores;
- Visualizar todas as pesquisas realizadas;
- Consultar retarificações;
- Acompanhar mensagens enviadas;
- Consultar e-mails enviados;
- Visualizar PDFs gerados;
- Acompanhar alterações realizadas;
- Facilitar auditorias internas.

---

# 🏗️ Funcionamento Geral

Sempre que uma operação for finalizada, todas as informações registradas serão disponibilizadas no Histórico.

```text
Processamento da OP
        │
        ▼
Registro
        │
        ▼
Banco de Dados
        │
        ▼
Histórico
        │
        ▼
Consulta do Usuário
```

---

# 📋 Informações Disponíveis

Cada operação deverá possuir uma ficha completa.

Exemplo:

```
OP

Pedido

Cliente

Passageiro

Comercial

Operador

Companhia

Status

Data

Hora
```

---

# 🔎 Pesquisa

O Histórico deverá possuir uma pesquisa inteligente.

Será possível localizar operações utilizando:

- Número da OP;
- Número do Pedido;
- Nome do Passageiro;
- Cliente;
- Comercial responsável;
- Companhia aérea;
- Operador;
- Data;
- Status.

A pesquisa deverá ser instantânea.

---

# 📅 Filtros

O sistema deverá permitir filtros avançados.

## Período

- Hoje;
- Ontem;
- Últimos 7 dias;
- Últimos 30 dias;
- Personalizado.

---

## Situação

- Finalizada;
- Retarificada;
- Em andamento;
- Erro;
- Cancelada.

---

## Companhia

- LATAM;
- GOL;
- AZUL;
- Outras.

---

## Operador

Selecionar um operador específico.

---

## Comercial

Consultar apenas operações vinculadas a determinado comercial.

---

# 📄 Tela de Consulta

O Histórico deverá apresentar uma tabela semelhante à seguinte.

| Data | OP | Pedido | Cliente | Companhia | Status |
|------|----|---------|----------|-----------|---------|
| 15/07 | VZ11988 | 908082 | João | LATAM | Finalizada |
| 15/07 | VZ12032 | 908145 | Maria | GOL | Retarificada |

---

# 👁️ Detalhes da Operação

Ao selecionar uma operação, o sistema exibirá todas as informações.

Exemplo:

```text
Pedido: 908082

OP: VZ11988

Cliente: João

Operador: Ítalo

Companhia: LATAM

Retarificação: Sim

Trecho: Ida

Tempo Total:

03m42s

Status:

Finalizado
```

---

# 💰 Histórico das Pesquisas

Cada operação deverá armazenar todas as pesquisas realizadas.

Exemplo:

| Portal | Valor |
|---------|-------:|
| Wooba | R$ 1.495,89 |
| Kontrip | R$ 1.362,42 |
| LATAM | R$ 958,80 |

---

# 🏆 Resultado Final

O Histórico deverá destacar:

- Portal escolhido;
- Melhor tarifa;
- Economia obtida;
- Diferença para o valor original.

---

# 💬 Comunicação

Será possível visualizar todas as mensagens enviadas.

## WhatsApp

- Grupo;
- Comercial mencionado;
- Data;
- Hora;
- Status;
- Conteúdo enviado.

---

## Email

- Destinatário;
- Assunto;
- Corpo da mensagem;
- Data;
- Hora;
- Situação.

---

# 📄 PDF

O Histórico deverá permitir visualizar:

- PDF gerado;
- Data de geração;
- Situação da anexação;
- Download do arquivo.

---

# 📈 Linha do Tempo

Cada operação deverá possuir uma timeline.

```text
09:01

Leitura

↓

09:02

Motor de Análise

↓

09:03

Pesquisa

↓

09:05

Comparação

↓

09:06

WhatsApp

↓

09:07

Email

↓

09:08

PDF

↓

09:09

Finalizado
```

---

# 📝 Observações

Também deverão ser armazenadas:

- Observações da OP;
- Mensagens identificadas;
- Classificação realizada;
- Regras aplicadas;
- Observações do operador.

---

# 📊 Estatísticas

O Histórico permitirá responder perguntas como:

- Quantas vezes um pedido foi consultado?
- Qual operador realizou determinada pesquisa?
- Quanto foi economizado?
- Quantas retarificações ocorreram?
- Qual portal apresentou o menor preço?
- Quantas mensagens foram enviadas?

---

# 🔒 Permissões

## Operador

Visualiza apenas suas operações.

---

## Supervisor

Visualiza operações da equipe.

---

## Gestor

Visualiza todas as operações.

---

# 📤 Exportação

O sistema deverá permitir exportar o Histórico.

Formatos previstos:

- PDF;
- Excel;
- CSV.

---

# 🔍 Pesquisa Avançada

O Histórico deverá permitir consultas combinadas.

Exemplo:

```
LATAM

+

Últimos 30 dias

+

Retarificação

+

Operador Ítalo
```

Retornando apenas operações compatíveis.

---

# 🚀 Melhorias Futuras

O módulo poderá evoluir para:

- Favoritos;
- Etiquetas personalizadas;
- Pesquisa por conteúdo das observações;
- Comparação entre operações;
- Linha do tempo gráfica;
- Histórico em nuvem;
- Compartilhamento de operações.

---

# 🔗 Dependências

Recebe informações de:

- Registro das Operações.

Fornece informações para:

- Dashboard;
- Auditoria;
- Relatórios;
- Consulta dos operadores.

---

# 📝 Observações para Desenvolvimento

O Histórico deverá ser otimizado para consultas rápidas, mesmo com milhões de registros.

As informações deverão ser indexadas pelos principais campos de pesquisa, garantindo excelente desempenho.

Sempre que possível, a consulta deverá utilizar paginação e carregamento sob demanda (Lazy Loading), evitando carregar grandes volumes de dados de uma única vez.

---

# 💡 Central Inteligente de Histórico

Além da consulta tradicional, o Histórico deverá oferecer uma visão consolidada de cada OP.

Ao abrir uma operação, o usuário visualizará uma página única contendo:

- Dados da OP;
- Dados do cliente;
- Passageiros;
- Resultado da análise;
- Histórico das pesquisas;
- Comparador de tarifas;
- Mensagens enviadas por WhatsApp;
- E-mails enviados;
- PDF gerado;
- Linha do tempo completa;
- Eventos registrados;
- Economia obtida;
- Tempo total da operação.

Essa central permitirá que qualquer colaborador compreenda toda a operação sem precisar acessar outros módulos do sistema.

---

# ✅ Próximo Capítulo

➡️ **17 - Configurações**

No próximo documento será detalhado o módulo de Configurações, responsável por permitir a personalização do Assistente VIAZA, gerenciamento de usuários, integração com portais, regras do sistema, grupos de WhatsApp, modelos de e-mail, geração de PDF e preferências da aplicação.