# 📖 Introdução

> **Projeto:** Assistente Inteligente VIAZA  
> **Versão:** 1.0.0  
> **Status:** 🟡 Em Planejamento

---

# 📌 Visão Geral

O **Assistente Inteligente VIAZA** é um aplicativo desktop desenvolvido para automatizar o processo operacional de emissão e retarificação de passagens aéreas.

Seu principal objetivo é reduzir tarefas repetitivas executadas pelos operadores, aumentando a produtividade, reduzindo erros humanos e padronizando todo o fluxo operacional da empresa.

O sistema atuará como um assistente inteligente, trabalhando em conjunto com o sistema interno utilizado pela equipe de emissão. Enquanto o operador realiza suas atividades normalmente, o aplicativo será responsável por monitorar a Ordem de Produção (OP), interpretar informações relevantes, realizar pesquisas automáticas em diferentes portais, comparar tarifas, gerar documentação e automatizar comunicações.

O operador continuará sendo o responsável pela decisão final da emissão, porém deixará de executar tarefas repetitivas e operacionais.

---

# 🎯 Objetivo

O projeto tem como objetivo automatizar o maior número possível de processos relacionados à emissão e retarificação de passagens aéreas.

Entre as principais funcionalidades previstas estão:

- Monitoramento automático das OPs;
- Leitura inteligente das informações da OP;
- Identificação automática de retarificações;
- Pesquisa simultânea em múltiplos portais;
- Comparação automática de tarifas;
- Identificação da melhor tarifa disponível;
- Identificação do trecho afetado (ida, volta ou ambos);
- Busca automática de informações complementares;
- Geração automática de mensagens;
- Envio de notificações via WhatsApp;
- Envio de e-mails ao cliente;
- Geração automática de documentos em PDF;
- Registro completo das operações;
- Dashboard de acompanhamento e produtividade.

---

# ❗ Problema Atual

Atualmente, quando uma emissão sofre uma retarificação, o operador precisa executar diversas atividades manualmente.

Esse processo normalmente envolve:

1. Identificar que a emissão não foi concluída.
2. Ler as observações da OP.
3. Interpretar o motivo da falha.
4. Identificar qual trecho foi afetado.
5. Pesquisar novamente em diferentes portais.
6. Comparar manualmente todas as tarifas encontradas.
7. Localizar o comercial responsável.
8. Localizar o grupo correto do WhatsApp.
9. Informar a retarificação.
10. Enviar e-mail ao cliente.
11. Gerar documentação da pesquisa.
12. Registrar toda a operação.

Além do tempo gasto, esse fluxo aumenta significativamente a possibilidade de erros operacionais.

---

# 💡 Solução Proposta

O Assistente Inteligente VIAZA será responsável por automatizar praticamente todas essas etapas.

Sempre que uma OP for aberta, o sistema poderá realizar automaticamente:

- Leitura completa da OP;
- Identificação de retarificação;
- Pesquisa de tarifas em diferentes plataformas;
- Comparação automática dos preços encontrados;
- Identificação do melhor portal;
- Identificação do trecho retarificado;
- Localização do e-mail do cliente;
- Localização do comercial responsável;
- Localização do grupo correto do WhatsApp;
- Geração da mensagem padrão;
- Geração do e-mail;
- Geração do PDF da pesquisa;
- Registro da operação.

Ao operador caberá apenas validar as informações e confirmar a execução das ações.

---

# 🏗️ Escopo do Projeto

Inicialmente o sistema será focado exclusivamente na automação do processo de emissão de passagens aéreas.

O projeto será desenvolvido de forma modular, permitindo que novas funcionalidades sejam adicionadas futuramente sem alterações significativas na arquitetura principal.

Entre as possibilidades futuras estão:

- Integração com APIs;
- Inteligência Artificial para interpretação de mensagens;
- Emissão totalmente automatizada;
- Dashboards gerenciais;
- Relatórios estatísticos;
- Histórico inteligente;
- Novos portais de pesquisa;
- Integração com outros sistemas internos.

---

# 👥 Público-Alvo

O sistema foi projetado para atender diferentes perfis dentro da operação.

## Operadores de Emissão

Responsáveis por abrir as OPs, validar as informações encontradas e concluir a emissão.

## Equipe Comercial

Receberá automaticamente notificações sobre retarificações e pesquisas realizadas.

## Gestores

Poderão acompanhar indicadores operacionais, histórico das pesquisas e produtividade da equipe.

## Administradores

Responsáveis pela configuração dos portais, mensagens, grupos, usuários e demais parâmetros do sistema.

---

# ⭐ Benefícios Esperados

A implementação do Assistente Inteligente VIAZA proporcionará diversos ganhos operacionais.

## Redução do tempo operacional

Automação de tarefas repetitivas que atualmente são executadas manualmente.

## Redução de erros

Diminuição de erros de digitação, pesquisas incorretas, comparações equivocadas e falhas de comunicação.

## Padronização

Todas as mensagens, documentos e registros seguirão um único padrão operacional.

## Maior produtividade

Os operadores poderão atender um número significativamente maior de OPs em menos tempo.

## Histórico centralizado

Todas as pesquisas e ações executadas ficarão registradas para consultas futuras.

---

# 📈 Visão Geral do Fluxo

```text
Operador abre uma OP
        │
        ▼
Assistente identifica automaticamente
        │
        ▼
Leitura da OP
        │
        ▼
Motor de Análise
        │
        ▼
Pesquisa Automática
        │
        ▼
Comparador Inteligente
        │
        ▼
Tela de Conferência
        │
        ▼
WhatsApp • E-mail • PDF
        │
        ▼
Registro no Histórico
```

---

# 📚 Estrutura da Documentação

Esta documentação foi dividida em capítulos para facilitar a compreensão do projeto.

Cada capítulo descreve um módulo específico do sistema, detalhando seu funcionamento, regras de negócio, entradas, saídas e fluxos de execução.

---

# ✅ Próximo Capítulo

➡️ **02 - Fluxo Geral**

O próximo documento apresentará o funcionamento completo do sistema desde a abertura de uma OP até a conclusão da operação.