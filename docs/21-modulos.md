# 🧩 Módulos do Assistente VIAZA

> **Documento:** 18  
> **Versão:** 1.0.0

---

# 📖 Objetivo

O Assistente VIAZA foi desenvolvido utilizando uma arquitetura modular.

Cada módulo possui uma responsabilidade específica e se comunica com os demais através de um fluxo organizado, desacoplado e escalável.

Essa arquitetura facilita a manutenção, evolução do sistema e inclusão de novas funcionalidades sem impactar módulos já existentes.

---

# 🏗️ Arquitetura Geral

```text
                    ASSISTENTE VIAZA

                            │
                            ▼

                 Leitura Automática da OP

                            │
                            ▼

                 Motor de Análise Inteligente

                            │
                            ▼

                    Motor de Regras

                            │
                            ▼

                     Classificação

                            │
                            ▼

                 Orquestrador de Fluxo

        ┌──────────────┬──────────────┬──────────────┐
        │              │              │              │
        ▼              ▼              ▼              ▼

Pesquisa        Busca de Dados   Comparador   Consulta Geral

        │              │              │              │
        └──────────────┴──────────────┴──────────────┘
                            │
                            ▼

                  Tela de Conferência

                            │
             ┌──────────────┼──────────────┐
             ▼              ▼              ▼

        WhatsApp         Email            PDF

             │              │              │
             └──────────────┴──────────────┘
                            │
                            ▼

                     Registro Geral

                            │
              ┌─────────────┴─────────────┐
              ▼                           ▼

          Histórico                 Dashboard

                            │
                            ▼

                     Configurações
```

---

# 📚 Lista dos Módulos

O Assistente VIAZA será composto pelos seguintes módulos.

| Nº | Módulo | Função Principal |
|---:|---------|------------------|
| 01 | Leitura Automática | Captura todas as informações da OP diretamente do sistema. |
| 02 | Motor de Análise Inteligente | Interpreta as observações e identifica eventos importantes. |
| 03 | Motor de Regras | Aplica regras configuráveis para reconhecer padrões e definir ações. |
| 04 | Classificação | Define a categoria da ocorrência e o fluxo que será executado. |
| 05 | Orquestrador de Fluxo | Coordena a execução dos módulos na ordem correta. |
| 06 | Pesquisa Automática | Pesquisa automaticamente todos os portais quando necessário. |
| 07 | Leitura dos Portais | Acessa os portais, realiza login e coleta informações das tarifas. |
| 08 | Comparador | Compara todas as tarifas encontradas e identifica a melhor opção. |
| 09 | Identificação do Trecho | Determina quais trechos foram impactados (ida, volta ou ambos). |
| 10 | Busca de Dados | Obtém informações complementares como e-mail do cliente, comercial responsável e grupo de WhatsApp. |
| 11 | Tela de Conferência | Exibe os resultados para validação do operador antes da execução das ações. |
| 12 | WhatsApp | Envia automaticamente mensagens para os grupos corretos, mencionando o comercial responsável. |
| 13 | Email | Envia automaticamente o comunicado de retarificação ao cliente. |
| 14 | PDF | Gera um relatório completo da operação. |
| 15 | Anexar PDF | Anexa automaticamente o PDF gerado à Ordem de Produção. |
| 16 | Registro | Armazena todos os eventos executados pelo sistema para auditoria. |
| 17 | Consulta Inteligente | Permite consultas manuais em qualquer OP, com comparação completa de tarifas. |
| 18 | Dashboard | Exibe indicadores, estatísticas e monitoramento em tempo real. |
| 19 | Histórico | Disponibiliza a consulta de todas as operações já executadas. |
| 20 | Configurações | Centraliza todas as parametrizações do sistema. |

---

# 🔄 Fluxo Completo

```text
Operador abre a OP
        │
        ▼
Leitura Automática
        │
        ▼
Motor de Análise
        │
        ▼
Motor de Regras
        │
        ▼
Classificação
        │
        ▼
Orquestrador de Fluxo
        │
        ▼
Pesquisa Automática
        │
        ▼
Leitura dos Portais
        │
        ▼
Comparador
        │
        ▼
Identificação do Trecho
        │
        ▼
Busca de Dados
        │
        ▼
Tela de Conferência
        │
        ▼
WhatsApp
        │
        ▼
Email
        │
        ▼
Geração do PDF
        │
        ▼
Anexação do PDF
        │
        ▼
Registro
        │
        ├────────► Histórico
        │
        └────────► Dashboard
```

---

# 🧠 Filosofia da Arquitetura

O Assistente VIAZA foi projetado seguindo princípios modernos de desenvolvimento de software.

Cada módulo possui apenas uma responsabilidade, reduzindo o acoplamento e facilitando a manutenção.

Essa abordagem permite:

- Evolução contínua do sistema;
- Inclusão de novos portais;
- Criação de novas regras;
- Adição de novos tipos de pesquisa;
- Integração com novos canais de comunicação;
- Escalabilidade da aplicação.

---

# 🔗 Comunicação entre os Módulos

Os módulos não devem depender diretamente uns dos outros.

A comunicação será realizada por meio do Orquestrador de Fluxo e de eventos internos.

Essa estratégia oferece:

- Maior estabilidade;
- Facilidade para testes;
- Reutilização de componentes;
- Menor impacto em futuras alterações.

---

# 🚀 Evolução da Plataforma

A arquitetura foi planejada para permitir a inclusão de novos módulos sem alterar os existentes.

Exemplos de futuras expansões:

- Inteligência Artificial para sugestão automática de decisões;
- Integração com APIs das companhias aéreas;
- Integração com Microsoft Teams;
- Integração com Slack;
- Aplicativo Mobile;
- Painel Web para gestores;
- Assistente por voz;
- Geração automática de relatórios executivos;
- Integração com Power BI;
- API pública para integração com sistemas corporativos.

---

# 🎯 Objetivo Final

O Assistente VIAZA tem como missão automatizar o processo de tratamento de retarificações e consultas tarifárias, reduzindo o tempo operacional, padronizando procedimentos, diminuindo erros humanos e fornecendo informações estratégicas para operadores e gestores.

A arquitetura modular garante que o sistema possa evoluir continuamente, acompanhando as necessidades da empresa sem comprometer sua estabilidade.

---

# 📌 Encerramento

Esta documentação descreve a estrutura funcional do Assistente VIAZA e servirá como referência para todas as etapas de desenvolvimento, testes, implantação e manutenção do projeto.

Novas funcionalidades deverão seguir os princípios arquiteturais definidos neste documento, garantindo a consistência, escalabilidade e qualidade da aplicação ao longo de sua evolução.