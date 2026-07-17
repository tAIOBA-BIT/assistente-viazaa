# 👁️ Leitura Automática da OP

> **Módulo:** Leitura Automática da OP  
> **Documento:** 03  
> **Versão:** 1.0.0

---

# 📖 Objetivo

Este módulo é responsável por capturar automaticamente todas as informações presentes na Ordem de Produção (OP), transformando os dados exibidos na tela em informações estruturadas que serão utilizadas pelos demais módulos do sistema.

A leitura da OP é a etapa mais importante do Assistente VIAZA, pois todas as decisões posteriores dependerão da qualidade das informações capturadas.

---

# 🎯 Objetivos do Módulo

O módulo deverá ser capaz de:

- Detectar automaticamente quando uma OP for aberta;
- Identificar o carregamento completo da página;
- Ler todos os campos relevantes;
- Organizar os dados em memória;
- Validar se todas as informações necessárias foram encontradas;
- Informar eventuais erros de leitura.

---

# 🏗️ Funcionamento Geral

Assim que o operador abrir uma OP, o aplicativo iniciará automaticamente o processo de leitura.

O operador não precisará clicar em nenhum botão.

```text
Operador abre a OP
        │
        ▼
Aplicativo detecta nova página
        │
        ▼
Aguarda carregamento completo
        │
        ▼
Captura os elementos da tela
        │
        ▼
Extrai todas as informações
        │
        ▼
Valida os dados
        │
        ▼
Envia para o Motor de Análise
```

---

# 🔍 Informações Obrigatórias

O aplicativo deverá localizar automaticamente:

## Dados da OP

- Número da OP
- Situação da OP
- Data da criação
- Operador responsável

---

## Dados do Pedido

- Número do pedido

Exemplo:

```
Pedido 908082
```

---

## Dados do Passageiro

- Nome completo
- Quantidade de passageiros
- Adultos
- Crianças
- Bebês

---

## Dados do Voo

- Companhia aérea
- Origem
- Destino
- Escalas
- Número do voo
- Classe tarifária
- Datas
- Horários

---

## Dados Financeiros

- Valor do pedido
- Forma de pagamento (caso disponível)
- Taxas

---

## Observações

Todo o campo de observações deverá ser capturado integralmente.

Nenhuma linha poderá ser ignorada.

Esse campo será utilizado posteriormente pelo Motor de Análise.

---

# 📥 Estrutura dos Dados

Após a leitura, todas as informações deverão ser organizadas em memória.

Exemplo:

```text
OP
│
├── Número
├── Pedido
├── Passageiros
├── Voos
├── Valores
├── Observações
└── Status
```

---

# 🔎 Campos Críticos

Algumas informações são obrigatórias para que o fluxo continue.

| Campo | Obrigatório |
|---------|:----------:|
| Número da OP | ✅ |
| Número do Pedido | ✅ |
| Passageiro | ✅ |
| Observações | ✅ |

Caso qualquer um desses campos esteja ausente, o sistema deverá interromper o fluxo e informar o operador.

---

# 📖 Leitura das Observações

O campo de observações será lido exatamente como aparece na OP.

Nenhum filtro será aplicado nesta etapa.

Exemplo:

```
Observações

Lorem ipsum...

Retarifação...

Mensagem do robô...

Status...

Outras informações...
```

A interpretação dessas mensagens será realizada exclusivamente pelo **Motor de Análise**.

---

# ⚠️ Regras de Leitura

O sistema nunca deverá assumir valores.

Caso uma informação não seja encontrada, ela deverá permanecer vazia e ser registrada no log.

Exemplo:

```
Origem:
Não encontrada.
```

---

# 🔄 Atualização Automática

Caso o operador altere de OP sem fechar o aplicativo, o sistema deverá:

```text
Nova OP detectada
        │
        ▼
Limpar dados anteriores
        │
        ▼
Realizar nova leitura
        │
        ▼
Enviar para análise
```

Nenhuma informação da OP anterior poderá permanecer em memória.

---

# 📊 Fluxo de Leitura

```text
Abrir OP
      │
      ▼
Detectar carregamento
      │
      ▼
Ler HTML da página
      │
      ▼
Capturar informações
      │
      ▼
Validar dados
      │
      ▼
Salvar em memória
      │
      ▼
Enviar ao Motor de Análise
```

---

# ❌ Tratamento de Erros

O módulo deverá tratar situações como:

## Página não carregada

Aguardar automaticamente alguns segundos antes de tentar novamente.

---

## Campo inexistente

Registrar no log e continuar, desde que o campo não seja obrigatório.

---

## Campo obrigatório ausente

Interromper o fluxo.

Exibir uma mensagem ao operador informando qual informação não foi encontrada.

---

## Erro de leitura

Caso ocorra qualquer erro inesperado durante a captura dos dados, o sistema deverá registrar o erro e permitir uma nova tentativa.

---

# 📋 Registro de Logs

Toda leitura deverá gerar um registro contendo:

- Data;
- Hora;
- Operador;
- Número da OP;
- Tempo da leitura;
- Resultado da captura;
- Campos ausentes (se houver).

---

# 🚀 Melhorias Futuras

Este módulo foi projetado para evoluir.

Entre as melhorias previstas estão:

- Leitura por OCR para elementos que não estejam disponíveis no HTML;
- Identificação automática de anexos;
- Captura de imagens da OP para auditoria;
- Cache das últimas OPs abertas;
- Monitoramento em tempo real de alterações na OP.

---

# 🔗 Dependências

Este módulo fornece informações para:

- Motor de Análise;
- Classificação;
- Pesquisa Automática;
- Comparador;
- Dashboard;
- Registro;
- Histórico.

Sem a conclusão da leitura automática, nenhum outro módulo poderá ser executado.

---

# ✅ Próximo Capítulo

➡️ **04 - Motor de Análise**

No próximo capítulo será detalhado como o sistema interpretará as observações da OP para identificar retarificações, falhas de emissão e definir automaticamente o fluxo que deverá ser seguido.