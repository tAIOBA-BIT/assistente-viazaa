# 🗃️ Registro das Operações

> **Módulo:** Registro das Operações
> **Documento:** 13
> **Versão:** 1.0.0

---

# 📖 Objetivo

O módulo de Registro é responsável por armazenar todas as ações executadas pelo Assistente VIAZA durante o processamento de uma Ordem de Produção (OP).

Cada etapa realizada pelo aplicativo deverá gerar um registro detalhado, permitindo auditoria, rastreabilidade e análise histórica das operações.

O registro representa a "memória" do sistema.

---

# 🎯 Objetivos

O módulo deverá ser capaz de:

- Registrar todas as operações executadas;
- Registrar decisões tomadas automaticamente;
- Armazenar pesquisas realizadas;
- Registrar alterações feitas pelo operador;
- Registrar erros encontrados;
- Registrar mensagens enviadas;
- Registrar geração de documentos;
- Disponibilizar informações para Dashboard e Histórico.

---

# 🏗️ Funcionamento Geral

Ao longo do processamento da OP, cada módulo enviará eventos ao Registro.

O Registro armazenará essas informações em ordem cronológica.

```text
Leitura da OP
      │
      ▼
Motor de Análise
      │
      ▼
Pesquisa Automática
      │
      ▼
Comparador
      │
      ▼
WhatsApp
      │
      ▼
Email
      │
      ▼
PDF
      │
      ▼
Registro Final
```

---

# 📥 Informações Registradas

Cada operação deverá possuir um identificador único.

Exemplo:

```
Registro

ID

OP

Pedido

Data

Hora

Operador
```

---

# 📋 Dados Gerais

O Registro deverá armazenar:

- Número da OP;
- Número do Pedido;
- Operador responsável;
- Cliente;
- Comercial responsável;
- Companhia aérea;
- Passageiros;
- Data da operação;
- Hora de início;
- Hora de término.

---

# 🔎 Dados da Pesquisa

Sempre que uma pesquisa for executada, deverão ser registrados:

- Portal consultado;
- Data da consulta;
- Hora;
- Tempo da pesquisa;
- Resultado obtido.

---

## Exemplo

| Portal | Valor Encontrado |
|---------|-----------------:|
| Wooba | R$ 1.495,89 |
| Kontrip | R$ 1.362,42 |
| LATAM | R$ 958,80 |

---

# 🏆 Resultado da Comparação

O sistema deverá registrar:

- Menor valor encontrado;
- Portal vencedor;
- Diferença entre os valores;
- Quantidade de portais pesquisados.

---

# ✈️ Dados da Retarificação

Caso exista retarificação, registrar:

- Companhia aérea;
- Trecho afetado;
- Tipo de trecho;

Exemplo:

```
Ida

Volta

Ida e Volta
```

---

# 💬 Registro das Mensagens

Toda mensagem enviada deverá ser registrada.

## WhatsApp

- Grupo utilizado;
- Comercial mencionado;
- Horário do envio;
- Status do envio.

---

## Gestora

Caso exista configuração para envio à gestora:

- Grupo;
- Horário;
- Situação.

---

## Email

Registrar:

- Destinatário;
- Assunto;
- Data;
- Hora;
- Situação.

---

# 📄 Registro do PDF

Após gerar o PDF, registrar:

- Nome do arquivo;
- Data;
- Hora;
- Tamanho;
- Situação da geração;
- Situação da anexação.

---

# ⚠️ Registro de Erros

Todo erro deverá ser registrado.

Exemplo:

```
Portal indisponível

Campo não encontrado

Erro de Login

Erro de Timeout

Erro de Pesquisa

Erro de Envio

Erro de Geração do PDF
```

---

# 📜 Linha do Tempo

Cada operação deverá possuir uma linha do tempo.

Exemplo:

```
09:01

Leitura iniciada

↓

09:02

Leitura concluída

↓

09:03

Pesquisa Wooba

↓

09:04

Pesquisa LATAM

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

Registro Final
```

---

# 👤 Identificação do Operador

Cada registro deverá informar:

- Nome do operador;
- Login utilizado;
- Computador (quando possível);
- Versão do aplicativo.

---

# 📈 Indicadores

O módulo deverá gerar indicadores utilizados pelo Dashboard.

Exemplo:

- Quantidade de OPs processadas;
- Quantidade de retarificações;
- Média de tempo por OP;
- Média de economia obtida;
- Portal mais utilizado;
- Companhia aérea com maior número de retarificações.

---

# 🧠 Estatísticas

O Registro permitirá responder perguntas como:

- Qual operador realizou determinada pesquisa?
- Qual foi a menor tarifa encontrada?
- Qual portal apresentou o menor preço?
- Quanto tempo durou a operação?
- Qual companhia mais retarificou?
- Quantas mensagens foram enviadas?
- Quantos PDFs foram gerados?

---

# 🔒 Segurança

O Registro não poderá ser alterado manualmente.

Caso alguma informação seja corrigida posteriormente, deverá ser criada uma nova versão do registro, preservando o histórico.

Nenhuma informação poderá ser apagada sem autorização administrativa.

---

# 🔄 Fluxo

```text
Módulo executa ação
        │
        ▼
Gerar Evento
        │
        ▼
Enviar ao Registro
        │
        ▼
Validar
        │
        ▼
Salvar
        │
        ▼
Atualizar Dashboard
        │
        ▼
Atualizar Histórico
```

---

# 🚀 Melhorias Futuras

O módulo poderá evoluir para:

- Registro em banco de dados na nuvem;
- Exportação para Excel;
- Exportação para PDF;
- API para auditoria;
- Assinatura digital dos registros;
- Integração com sistemas corporativos.

---

# 🔗 Dependências

Recebe informações de:

- Leitura Automática;
- Motor de Análise;
- Classificação;
- Pesquisa Automática;
- Comparador;
- Busca de Dados;
- Tela de Conferência;
- WhatsApp;
- Email;
- PDF.

Fornece informações para:

- Dashboard;
- Histórico;
- Relatórios;
- Auditoria.

---

# 📝 Observações para Desenvolvimento

O módulo de Registro deve operar de forma assíncrona, sem bloquear o fluxo principal do aplicativo.

Sempre que possível, os registros devem ser gravados em segundo plano para garantir maior desempenho.

Cada operação deverá possuir um identificador único (UUID), permitindo relacionar todos os eventos da mesma OP.

---

# 📌 Exemplo de Registro Completo

```text
OP: VZ11988
Pedido: 908082
Operador: Ítalo Lima

Cliente: VIAZA

Companhia: LATAM

Retarificação: Sim

Trecho: Ida

Portal escolhido: LATAM

Wooba: R$ 1.495,89

Kontrip: R$ 1.362,42

LATAM: R$ 958,80

Valor do Pedido: R$ 1.417,73

WhatsApp: Enviado

Email: Enviado

PDF: Gerado e anexado

Tempo Total: 03m42s

Status: Finalizado com sucesso
```

---

# ✅ Próximo Capítulo

➡️ **14 - Dashboard**

No próximo documento será especificado o painel gerencial do Assistente VIAZA, contendo indicadores em tempo real, gráficos, filtros, métricas de desempenho e acompanhamento das operações processadas.