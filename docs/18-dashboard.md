# 📊 Dashboard Inteligente

> **Módulo:** Dashboard Inteligente
> **Documento:** 15
> **Versão:** 1.0.0

---

# 📖 Objetivo

O Dashboard Inteligente é o painel principal do Assistente VIAZA.

Seu objetivo é apresentar, em tempo real, todas as informações relevantes sobre as operações realizadas pelo aplicativo, permitindo que operadores e gestores acompanhem o desempenho do sistema, identifiquem gargalos e monitorem indicadores estratégicos.

O Dashboard deverá fornecer uma visão clara e objetiva de todas as operações, desde a leitura da OP até a conclusão do processo.

---

# 🎯 Objetivos

O Dashboard deverá permitir:

- Acompanhar operações em tempo real;
- Visualizar estatísticas gerais;
- Monitorar pesquisas realizadas;
- Identificar retarificações;
- Acompanhar economia gerada;
- Visualizar produtividade dos operadores;
- Identificar falhas do sistema;
- Exibir indicadores para tomada de decisão.

---

# 🏗️ Funcionamento Geral

Todos os módulos do Assistente VIAZA enviarão informações para o Dashboard.

```text
Leitura da OP
      │
Motor de Análise
      │
Pesquisa Automática
      │
Comparador
      │
WhatsApp
      │
Email
      │
PDF
      │
Registro
      │
      ▼
Dashboard
```

O Dashboard será atualizado automaticamente conforme novas operações forem executadas.

---

# 🖥️ Tela Inicial

Ao abrir o aplicativo, o Dashboard deverá apresentar um resumo geral.

Exemplo:

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

OPs Processadas Hoje

152

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Retarificações

38

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Consultas Gerais

91

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Mensagens Enviadas

74

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Emails Enviados

38

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

PDFs Gerados

38

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

# 📈 Indicadores Gerais

O Dashboard deverá apresentar indicadores como:

- OPs processadas;
- OPs em andamento;
- OPs concluídas;
- OPs com erro;
- OPs aguardando conferência;
- OPs canceladas.

---

# ✈️ Indicadores de Retarificação

O sistema deverá informar:

- Quantidade de retarificações;
- Percentual de retarificação;
- Companhia aérea com maior incidência;
- Trechos mais afetados;
- Horários com maior ocorrência.

Exemplo:

| Companhia | Retarificações |
|------------|--------------:|
| LATAM | 42 |
| GOL | 18 |
| AZUL | 11 |

---

# 💰 Indicadores Financeiros

O Dashboard deverá apresentar:

- Economia obtida;
- Economia média por OP;
- Maior economia encontrada;
- Valor original das OPs;
- Valor final encontrado.

Exemplo:

```
Economia Hoje

R$ 12.847,31
```

---

# 🌐 Indicadores dos Portais

O sistema deverá informar:

- Quantidade de consultas;
- Tempo médio de resposta;
- Menor tarifa encontrada;
- Portal mais utilizado;
- Portal mais rápido;
- Portal com maior índice de erro.

Exemplo:

| Portal | Pesquisas | Tempo Médio |
|---------|----------:|-----------:|
| Wooba | 92 | 11 s |
| Kontrip | 87 | 9 s |
| LATAM | 78 | 6 s |

---

# 👨‍💼 Produtividade dos Operadores

O Dashboard deverá apresentar:

- Quantidade de OPs processadas por operador;
- Tempo médio por operação;
- Número de consultas realizadas;
- Quantidade de retarificações resolvidas.

Exemplo:

| Operador | OPs |
|-----------|----:|
| Ítalo | 41 |
| João | 37 |
| Maria | 35 |

---

# 💬 Indicadores de Comunicação

O sistema deverá informar:

## WhatsApp

- Mensagens enviadas;
- Falhas de envio;
- Tempo médio.

---

## Email

- Emails enviados;
- Emails pendentes;
- Emails com erro.

---

# 📄 Indicadores de PDF

O Dashboard deverá mostrar:

- PDFs gerados;
- PDFs anexados;
- Falhas na geração;
- Falhas na anexação.

---

# ⚠️ Alertas

O Dashboard deverá destacar automaticamente situações críticas.

Exemplo:

```
⚠️ Portal LATAM indisponível

⚠️ Alto índice de retarificação

⚠️ Falha de login no Wooba

⚠️ Emails pendentes

⚠️ PDF não anexado
```

---

# 📅 Filtros

O operador poderá filtrar os dados por:

- Hoje;
- Ontem;
- Últimos 7 dias;
- Últimos 30 dias;
- Intervalo personalizado.

Também deverá ser possível filtrar por:

- Companhia;
- Portal;
- Operador;
- Comercial;
- Cliente;
- Status da OP.

---

# 📊 Gráficos

O Dashboard deverá possuir gráficos interativos.

## Retarificações por Companhia

```text
LATAM

██████████████

GOL

███████

AZUL

████
```

---

## Pesquisas por Portal

```text
Wooba

██████████

Kontrip

████████

LATAM

██████
```

---

## Economia por Dia

```text
Segunda

██████

Terça

██████████

Quarta

████████
```

---

## Produtividade

Quantidade de OPs processadas por operador.

---

# 🔍 Pesquisa Rápida

O Dashboard deverá possuir um campo de pesquisa.

O operador poderá localizar rapidamente:

- Número da OP;
- Número do Pedido;
- Nome do Passageiro;
- Cliente;
- Comercial.

---

# 📋 Últimas Operações

Uma tabela deverá apresentar as operações mais recentes.

Exemplo:

| Hora | OP | Pedido | Status |
|------|----|--------|--------|
| 09:21 | VZ11988 | 908082 | Finalizada |
| 09:18 | VZ12032 | 908145 | Pesquisa |
| 09:12 | VZ12041 | 908152 | Conferência |

---

# 🚨 Centro de Alertas

O Dashboard deverá manter uma área exclusiva para notificações.

Exemplo:

- Portal indisponível;
- Login expirado;
- Falha de envio;
- Pesquisa interrompida;
- PDF não anexado;
- Mensagem não enviada.

---

# ⚙️ Personalização

Cada operador poderá configurar:

- Widgets visíveis;
- Ordem dos painéis;
- Tema claro ou escuro;
- Atualização automática;
- Sons de notificação.

---

# 📈 Atualização em Tempo Real

Sempre que uma nova ação for registrada, o Dashboard deverá atualizar automaticamente os indicadores.

Nenhuma atualização manual será necessária.

---

# 🔐 Segurança

As informações exibidas deverão respeitar o perfil de acesso.

## Operador

Visualiza apenas suas operações.

---

## Supervisor

Visualiza sua equipe.

---

## Gestor

Visualiza todas as operações da empresa.

---

# 🚀 Melhorias Futuras

O Dashboard poderá evoluir para incluir:

- Inteligência Artificial para previsão de retarificações;
- Ranking de companhias aéreas;
- Ranking de comerciais;
- Mapa de calor por horário;
- Indicadores de SLA;
- Comparativo mensal;
- Exportação para Excel;
- Exportação para Power BI;
- Integração com Microsoft Teams e Google Looker Studio.

---

# 🔗 Dependências

Recebe informações de:

- Leitura Automática;
- Motor de Análise;
- Classificação;
- Pesquisa Automática;
- Consulta Inteligente;
- Comparador;
- WhatsApp;
- Email;
- PDF;
- Registro;
- Histórico.

Não envia informações para outros módulos.

É o principal painel de monitoramento do Assistente VIAZA.

---

# 📝 Observações para Desenvolvimento

O Dashboard deverá ser desenvolvido utilizando arquitetura baseada em eventos (Event Driven).

Sempre que qualquer módulo gerar um novo evento, o Dashboard deverá atualizar automaticamente seus indicadores, sem necessidade de recarregar a aplicação.

As consultas deverão ser otimizadas para garantir excelente desempenho, mesmo com milhares de registros armazenados.

---

# 💡 Dashboard Executivo

Além do painel operacional, o sistema deverá oferecer um Dashboard Executivo, voltado para supervisores e gestores.

Esse painel deverá apresentar:

- Economia total por período;
- Total de retarificações por companhia;
- Tempo médio de resolução;
- Eficiência dos operadores;
- Portais com melhor desempenho;
- Índice de sucesso das pesquisas;
- Histórico de produtividade;
- Ranking de economia gerada por operador;
- Percentual de falhas por portal;
- Volume de mensagens enviadas por WhatsApp e e-mail.

O Dashboard Executivo será utilizado para tomada de decisões estratégicas e acompanhamento da performance do setor.

---

# ✅ Próximo Capítulo

➡️ **16 - Histórico**

O próximo documento especificará o módulo responsável por armazenar e disponibilizar todo o histórico das operações realizadas pelo Assistente VIAZA, permitindo auditoria completa, consultas detalhadas e rastreabilidade de todas as ações executadas pelo sistema.