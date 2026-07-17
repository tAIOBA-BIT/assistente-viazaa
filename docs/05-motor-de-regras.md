# ⚙️ Motor de Regras

O Motor de Análise não possuirá regras fixas implementadas diretamente no código-fonte.

Toda a lógica de decisão será baseada em um **Motor de Regras Configurável**, permitindo que novos padrões sejam adicionados sem necessidade de alterar ou recompilar o aplicativo.

Essa abordagem torna o sistema mais flexível, reduz o custo de manutenção e facilita a adaptação a novas mensagens do sistema interno.

---

# 🎯 Objetivos do Motor de Regras

O Motor de Regras será responsável por:

- Identificar mensagens conhecidas;
- Classificar automaticamente a ocorrência;
- Determinar qual ação deverá ser executada;
- Definir o nível de prioridade;
- Informar ao operador quando uma mensagem desconhecida for encontrada;
- Permitir atualização das regras sem necessidade de desenvolvimento.

---

# 🏗️ Funcionamento

Após receber as observações da OP, o Motor de Análise enviará todo o texto para o Motor de Regras.

O Motor de Regras percorrerá todas as regras cadastradas até encontrar uma correspondência.

```text
Observações
        │
        ▼
Motor de Regras
        │
        ▼
Existe regra correspondente?
        │
 ┌──────┴────────┐
 │               │
Não             Sim
 │               │
 ▼               ▼
Registrar     Executar ação
```

---

# 📚 Estrutura das Regras

Cada regra deverá possuir uma estrutura semelhante à seguinte:

| Campo | Descrição |
|--------|-----------|
| Nome | Nome da regra |
| Prioridade | Ordem de execução |
| Tipo | Categoria da ocorrência |
| Padrão | Texto ou expressão a ser localizada |
| Ação | Fluxo que deverá ser executado |
| Status | Ativa ou Inativa |

---

# 📋 Exemplo de Cadastro

| Nome | Padrão | Tipo | Ação |
|--------|---------|---------|----------------------------|
| Retarifação | retarifad | Retarificação | Iniciar Pesquisa |
| Não Emitido | não emitido | Falha | Iniciar Pesquisa |
| Pagamento | pagamento | Financeiro | Encerrar Fluxo |
| Cancelamento | cancelado | Cancelamento | Encerrar Fluxo |

O sistema deverá permitir o cadastro de inúmeras regras.

---

# 🔍 Tipo de Correspondência

Cada regra poderá utilizar diferentes formas de pesquisa.

## Contém

```
retarifad
```

Detectará:

```
Retarifada

Retarifação

Retarifado

Retarifar
```

---

## Igual

A mensagem deverá ser exatamente igual.

---

## Expressão Regular

Permitirá localizar padrões complexos.

Exemplo:

```
Pedido 908082

Pedido 912345

Pedido 845912
```

---

# 🥇 Prioridade das Regras

Caso duas ou mais regras sejam compatíveis, será utilizada a de maior prioridade.

Exemplo:

| Prioridade | Regra |
|------------|-------|
| 1 | Falha Crítica |
| 2 | Retarificação |
| 3 | Pagamento |
| 4 | Informação |

Isso evita conflitos entre regras semelhantes.

---

# ❓ Mensagens Desconhecidas

Caso nenhuma regra seja encontrada, o sistema deverá:

- Registrar a mensagem completa;
- Armazenar a ocorrência;
- Solicitar conferência manual;
- Disponibilizar a mensagem para criação de uma nova regra futuramente.

Exemplo:

```
Mensagem não reconhecida.

Necessita análise manual.
```

---

# 📈 Evolução Contínua

Sempre que uma nova mensagem for identificada pelos operadores, será possível cadastrá-la como uma nova regra.

Dessa forma, o sistema evoluirá continuamente sem necessidade de alterações no código.

Com o passar do tempo, o número de mensagens desconhecidas tende a diminuir, tornando o Assistente VIAZA cada vez mais eficiente.

---

# 💡 Benefícios

- Não exige atualização do aplicativo para novas mensagens;
- Fácil manutenção;
- Fácil expansão;
- Menor dependência do desenvolvedor;
- Maior confiabilidade;
- Melhor escalabilidade.
