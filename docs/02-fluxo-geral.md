# 🔄 Fluxo Geral

> **Módulo:** Fluxo Geral  
> **Documento:** 02  
> **Versão:** 1.0.0

---

# 📖 Objetivo

Este documento descreve o fluxo completo de funcionamento do **Assistente Inteligente VIAZA**, desde o momento em que uma Ordem de Produção (OP) é aberta pelo operador até o encerramento da operação.

O objetivo deste fluxo é garantir que todas as etapas sejam executadas de forma padronizada, reduzindo o tempo operacional e minimizando erros humanos.

---

# 🎯 Visão Geral

O Assistente VIAZA atuará como um observador inteligente.

Ele permanecerá aguardando até que o operador abra uma Ordem de Produção.

A partir desse momento, iniciará automaticamente a leitura da OP e conduzirá todo o processo de análise, pesquisa, comparação e comunicação.

---

# 🏗️ Fluxo Principal

```text
Operador inicia o aplicativo
        │
        ▼
Login nos portais necessários
        │
        ▼
Aplicativo permanece aguardando
        │
        ▼
Operador abre uma OP
        │
        ▼
Assistente detecta automaticamente a OP
        │
        ▼
Realiza leitura completa da OP
        │
        ▼
Extrai todas as informações relevantes
        │
        ▼
Motor de análise interpreta as observações
        │
        ▼
Existe retarificação?
        │
 ┌──────┴─────────┐
 │                │
Não             Sim
 │                │
 ▼                ▼
Consulta Geral    Fluxo de Retarificação
```

---

# 📌 Fluxo de Retarificação

Quando uma retarificação for identificada, o sistema iniciará automaticamente uma nova sequência de ações.

```text
Retarificação detectada
        │
        ▼
Identificar o trecho afetado
        │
        ▼
Pesquisar todos os portais disponíveis
        │
        ▼
Comparar todas as tarifas
        │
        ▼
Selecionar a melhor opção
        │
        ▼
Buscar informações complementares
        │
        ▼
Montar tela de conferência
        │
        ▼
Operador confirma
        │
        ▼
Executar ações automáticas
```

---

# 🔍 Etapa 1 — Leitura da OP

Assim que detectar uma OP aberta, o aplicativo deverá capturar automaticamente todas as informações disponíveis na tela.

Entre elas:

- Número da OP;
- Número do Pedido;
- Nome do passageiro;
- Companhia aérea;
- Origem;
- Destino;
- Datas;
- Observações;
- Situação da emissão.

Nenhuma ação será executada antes da conclusão dessa leitura.

---

# 🧠 Etapa 2 — Motor de Análise

Após concluir a leitura da OP, o Motor de Análise interpretará o conteúdo das observações.

Seu objetivo será determinar se a emissão foi concluída normalmente ou se houve necessidade de retarificação.

Caso uma retarificação seja identificada, o sistema iniciará automaticamente o fluxo correspondente.

---

# 🌐 Etapa 3 — Pesquisa Automática

O aplicativo pesquisará automaticamente todos os portais configurados.

Exemplo:

- Wooba;
- Kontrip;
- Portal da companhia aérea;
- Outros portais cadastrados.

Cada portal será consultado utilizando exatamente as mesmas informações da OP.

---

# ⚖️ Etapa 4 — Comparação

Após concluir todas as pesquisas, o sistema organizará os resultados.

Exemplo:

| Portal | Valor |
|---------|-------:|
| Wooba | R$ 1.495,89 |
| Kontrip | R$ 1.362,42 |
| LATAM | R$ 958,80 |

Em seguida será identificado automaticamente o menor valor encontrado.

---

# ✈️ Etapa 5 — Identificação do Trecho

Antes da comunicação, o sistema deverá identificar exatamente qual trecho sofreu alteração.

Possibilidades:

- Apenas ida;
- Apenas volta;
- Ida e volta.

Essa informação será utilizada na mensagem enviada ao grupo do WhatsApp.

Exemplo:

> Trecho LATAM retarifado.

ou

> Ambos os trechos foram retarifados.

---

# 👤 Etapa 6 — Busca de Dados

Após encontrar a melhor tarifa, o aplicativo localizará automaticamente:

- E-mail do cliente;
- Comercial responsável;
- Grupo correto do WhatsApp.

Essas informações serão utilizadas automaticamente nas próximas etapas.

---

# 🖥️ Etapa 7 — Tela de Conferência

Antes do envio das mensagens, será apresentada uma tela contendo todas as informações encontradas.

O operador poderá conferir:

- Melhor tarifa;
- Portal escolhido;
- Valores pesquisados;
- Comercial responsável;
- Grupo do WhatsApp;
- E-mail do cliente.

Somente após a confirmação do operador o sistema continuará.

---

# 💬 Etapa 8 — WhatsApp

Após a confirmação, será enviada automaticamente uma mensagem ao grupo correspondente.

Exemplo:

```
Pedido 908082 / VZ11988

Wooba: R$ 1.495,89
Kontrip: R$ 1.362,42
LATAM: R$ 958,80

Valor Total do Pedido: R$ 1.417,73

Trecho LATAM retarifado.
```

O comercial responsável será mencionado automaticamente.

Uma segunda mensagem poderá ser enviada para a gestora, registrando a ocorrência.

---

# 📧 Etapa 9 — E-mail

O aplicativo montará automaticamente um e-mail para o cliente contendo:

- Assunto;
- Explicação da retarificação;
- Novos valores;
- Informações adicionais.

O operador poderá revisar antes do envio.

---

# 📄 Etapa 10 — PDF

Após concluir a operação, o sistema gerará automaticamente um PDF contendo:

- Dados da OP;
- Valores pesquisados;
- Portal escolhido;
- Melhor tarifa;
- Data;
- Hora;
- Operador responsável.

---

# 📎 Etapa 11 — Anexação

O PDF será anexado automaticamente à OP, no espaço destinado aos documentos.

Caso isso não seja possível por limitações do sistema, o aplicativo apresentará o arquivo pronto para anexação manual.

---

# 🗃️ Etapa 12 — Registro

Ao final da operação, todas as informações serão registradas.

Serão armazenados:

- Data;
- Hora;
- Operador;
- Pedido;
- OP;
- Valores pesquisados;
- Portal escolhido;
- Tempo da pesquisa;
- Resultado da operação.

---

# 📊 Fluxo Resumido

```text
Abrir OP
     │
     ▼
Leitura Automática
     │
     ▼
Motor de Análise
     │
     ▼
Retarificação?
     │
 ┌───┴─────────────┐
 │                 │
Não               Sim
 │                 │
 ▼                 ▼
Consulta Geral     Pesquisa Automática
                   │
                   ▼
             Comparação
                   │
                   ▼
          Identificar Trecho
                   │
                   ▼
            Buscar Dados
                   │
                   ▼
        Tela de Conferência
                   │
                   ▼
      WhatsApp • E-mail • PDF
                   │
                   ▼
              Registro Final
```

---

# ⚠️ Regras de Negócio

- Nenhuma mensagem será enviada sem confirmação do operador.
- Todos os portais configurados deverão ser pesquisados.
- O sistema sempre priorizará o menor valor encontrado.
- Toda operação deverá ser registrada no histórico.
- Caso algum portal esteja indisponível, a pesquisa continuará nos demais.
- Todas as ações deverão gerar logs para auditoria.

---

# ✅ Próximo Capítulo

➡️ **03 - Leitura Automática**

No próximo documento será detalhado como o aplicativo identifica uma OP, captura as informações da tela e prepara os dados para análise.