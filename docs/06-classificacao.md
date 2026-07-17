# 📑 Classificação

> **Módulo:** Classificação Inteligente  
> **Documento:** 05  
> **Versão:** 1.0.0

---

# 📖 Objetivo

O módulo de Classificação é responsável por transformar o resultado produzido pelo Motor de Análise em uma decisão operacional.

Enquanto o Motor de Análise identifica o que aconteceu, o Classificador determina exatamente quais ações deverão ser executadas.

Este módulo funciona como um "controlador de fluxo", garantindo que cada ocorrência siga o processo correto.

---

# 🎯 Objetivos

O módulo deverá ser capaz de:

- Classificar automaticamente a ocorrência;
- Definir o fluxo que será executado;
- Definir a prioridade da operação;
- Determinar quais módulos serão acionados;
- Evitar execuções desnecessárias;
- Padronizar todas as decisões do sistema.

---

# 🏗️ Funcionamento

Após o Motor de Análise interpretar a OP, ele envia um conjunto de informações para o Classificador.

Exemplo:

```text
Tipo:

Retarificação

Trecho:

Ida

Mensagem:

Retarifação LATAM

Portal:

LATAM
```

O Classificador então determina quais ações serão executadas.

---

# 🔄 Fluxo

```text
Motor de Análise

        │

        ▼

Classificador

        │

        ▼

Definir Categoria

        │

        ▼

Definir Prioridade

        │

        ▼

Selecionar Fluxo

        │

        ▼

Acionar os módulos necessários
```

---

# 📚 Categorias

Cada OP deverá pertencer a apenas uma categoria principal.

## ✅ Emissão Concluída

A emissão foi realizada com sucesso.

Nenhuma pesquisa será executada.

Apenas registrar a operação.

---

## 💰 Retarificação

Foi identificada uma retarificação.

Executar:

- Pesquisa
- Comparador
- WhatsApp
- E-mail
- PDF
- Registro

---

## ⚠️ Falha Temporária

Erro momentâneo.

Executar:

- Registrar ocorrência
- Aguardar
- Nova tentativa

---

## ❌ Erro Crítico

Erro que impede qualquer continuidade.

Executar:

- Registrar erro
- Notificar operador

---

## ❓ Mensagem Desconhecida

Não existe regra cadastrada.

Executar:

- Registrar ocorrência
- Encaminhar para conferência manual

---

# 🚦 Prioridade

Cada ocorrência possuirá um nível de prioridade.

| Prioridade | Significado |
|------------|-------------|
| 🔴 Alta | Necessita ação imediata |
| 🟠 Média | Pode aguardar confirmação |
| 🟢 Baixa | Apenas registro |

A prioridade será utilizada pelo Dashboard e pelo Histórico.

---

# ⚙️ Plano de Execução

Após a classificação, será criado um plano de execução.

Exemplo:

```text
Pesquisa

↓

Comparador

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
```

Esse plano será enviado ao Orquestrador do Sistema.

---

# 📋 Estrutura da Classificação

O sistema deverá gerar um objeto semelhante ao exemplo abaixo.

```text
Categoria:

Retarificação

Prioridade:

Alta

Pesquisar:

Sim

Comparar:

Sim

WhatsApp:

Sim

Email:

Sim

PDF:

Sim

Registro:

Sim

Consulta Geral:

Não
```

Todos os módulos seguintes utilizarão essas informações.

---

# 🚫 Regras

O Classificador nunca deverá tomar decisões baseadas em texto.

Ele utilizará exclusivamente o resultado produzido pelo Motor de Análise.

Isso garante que toda a inteligência permaneça centralizada.

---

# 🔍 Casos Especiais

## Mais de uma ocorrência

Caso existam múltiplas mensagens na mesma OP.

Exemplo:

```
Retarificação

+

Erro de Pagamento
```

O sistema deverá utilizar a ocorrência de maior prioridade.

---

## Informações Incompletas

Caso o Motor de Análise não consiga classificar totalmente a OP.

O sistema deverá:

- Registrar a ocorrência;
- Encaminhar para conferência manual.

---

# 📈 Benefícios

A separação entre Análise e Classificação oferece diversas vantagens.

- Código mais organizado;
- Fácil manutenção;
- Inclusão de novas categorias;
- Redução de erros;
- Padronização das decisões;
- Melhor integração entre módulos.

---

# 🔗 Dependências

Recebe informações de:

- Motor de Análise Inteligente

Envia informações para:

- Pesquisa Automática
- Comparador
- Tela de Conferência
- Registro
- Dashboard
- Histórico

---

# 🚀 Melhorias Futuras

Este módulo poderá evoluir para:

- Classificação baseada em IA;
- Aprendizado de novos padrões;
- Priorização dinâmica;
- Sugestão automática de ações;
- Classificação estatística.

---

# 📌 Observações para Desenvolvimento

O Classificador não deverá executar nenhuma ação diretamente.

Sua única responsabilidade será decidir qual fluxo será seguido.

A execução será realizada por módulos específicos, mantendo a arquitetura desacoplada e facilitando futuras expansões do sistema.

---

# ✅ Próximo Capítulo

➡️ **06 - Pesquisa Automática**

No próximo capítulo será detalhado como o aplicativo pesquisará simultaneamente todos os portais de emissão, coletará as tarifas e preparará os dados para comparação.