# 🔍 Motor de Busca de Dados

> **Módulo:** Motor de Busca de Dados
> **Documento:** 07
> **Versão:** 1.0.0

---

# 📖 Objetivo

O Motor de Busca de Dados é responsável por localizar automaticamente todas as informações complementares necessárias para a execução da operação.

Enquanto os módulos anteriores trabalham com os dados existentes na Ordem de Produção, este módulo consulta outras fontes de informação para enriquecer a operação.

Seu objetivo é eliminar consultas manuais realizadas pelos operadores.

---

# 🎯 Objetivos

O módulo deverá ser capaz de:

- Localizar automaticamente o e-mail do cliente;
- Identificar o comercial responsável;
- Localizar o grupo correto do WhatsApp;
- Buscar informações adicionais do pedido;
- Validar todas as informações encontradas;
- Padronizar os dados para os módulos seguintes.

---

# 🏗️ Funcionamento Geral

Após a conclusão da pesquisa de tarifas, o sistema iniciará automaticamente a busca das informações complementares.

```text
Pesquisa concluída
        │
        ▼
Receber Número do Pedido
        │
        ▼
Consultar Sistema
        │
        ▼
Localizar informações
        │
        ▼
Validar dados
        │
        ▼
Enviar para Tela de Conferência
```

---

# 📥 Dados Recebidos

O módulo receberá:

- Número da OP;
- Número do Pedido;
- Nome do Passageiro;
- Companhia Aérea;
- Melhor tarifa encontrada.

---

# 🔎 Fontes de Consulta

O sistema poderá consultar diferentes fontes de informação.

Exemplo:

- Sistema interno da empresa;
- Banco de dados;
- CRM;
- Cadastro de clientes;
- Cadastro de comerciais;
- Cadastro de grupos do WhatsApp;
- Arquivos de configuração.

Todas essas fontes deverão ser configuráveis.

---

# 📧 Busca do E-mail

Utilizando o número do pedido, o sistema localizará automaticamente o e-mail do cliente.

Exemplo:

```text
Pedido

↓

908082

↓

Pesquisar

↓

Cliente encontrado

↓

cliente@email.com
```

Caso existam múltiplos e-mails cadastrados, todos serão apresentados ao operador para conferência.

---

# 👤 Comercial Responsável

O sistema deverá identificar automaticamente o comercial responsável pelo pedido.

Exemplo:

```text
Pedido

↓

908082

↓

Comercial

↓

João Silva
```

Essa informação será utilizada para mencionar o responsável na mensagem do WhatsApp.

---

# 💬 Grupo do WhatsApp

Com base nas regras cadastradas, o sistema localizará automaticamente o grupo correto.

Exemplo:

```text
Companhia

↓

LATAM

↓

Grupo LATAM
```

Ou

```text
Equipe Corporativa

↓

Grupo Corporativo
```

As regras deverão ser totalmente configuráveis.

---

# 🧩 Estrutura das Regras

O sistema deverá permitir cadastrar regras de associação.

Exemplo:

| Condição | Grupo |
|-----------|----------------|
| LATAM | Grupo LATAM |
| GOL | Grupo GOL |
| AZUL | Grupo Azul |
| Internacional | Grupo Internacional |

Novas regras poderão ser adicionadas sem alterar o código do sistema.

---

# 📋 Informações Retornadas

Ao finalizar a busca, o módulo deverá retornar:

- E-mail do cliente;
- Comercial responsável;
- Grupo do WhatsApp;
- Nome do cliente;
- Informações adicionais encontradas.

---

# ⚠️ Tratamento de Erros

## Pedido não encontrado

Registrar ocorrência.

Solicitar conferência manual.

---

## Cliente sem e-mail

Permitir que o operador informe manualmente.

Registrar a inconsistência.

---

## Comercial não localizado

Encaminhar para conferência.

Não impedir o restante do fluxo.

---

## Grupo não encontrado

Permitir seleção manual.

Registrar a ocorrência.

---

# 🔄 Cache Inteligente

Caso o mesmo pedido seja consultado novamente durante a sessão, o sistema utilizará as informações armazenadas em memória.

Isso reduzirá consultas desnecessárias e aumentará a velocidade do aplicativo.

---

# 📊 Registro

Toda consulta deverá gerar um registro contendo:

- Data;
- Hora;
- Pedido;
- OP;
- Fonte consultada;
- Tempo da consulta;
- Resultado obtido.

---

# 🔗 Integração

As informações encontradas serão utilizadas pelos seguintes módulos:

- Tela de Conferência;
- WhatsApp;
- E-mail;
- PDF;
- Registro;
- Dashboard.

---

# 🚀 Melhorias Futuras

O Motor de Busca de Dados poderá evoluir para:

- Consulta em múltiplos bancos de dados;
- Integração com CRM;
- Integração com APIs internas;
- Identificação automática de novos contatos;
- Histórico de alterações dos clientes;
- Sincronização automática de cadastros.

---

# 🏛️ Arquitetura

O módulo deverá utilizar conectores independentes para cada fonte de informação.

```text
Busca de Dados

        │

 ┌──────┼─────────┐

 ▼      ▼         ▼

CRM   Sistema   Banco

Interno Dados

        │

        ▼

Consolidar Informações

        │

        ▼

Enviar Resultado
```

Cada conector será responsável apenas por consultar sua fonte específica.

---

# 🛡️ Regras de Negócio

- O número do pedido será a chave principal da consulta.
- Nenhum dado poderá ser alterado pelo módulo.
- O sistema apenas realizará consultas.
- Todas as consultas deverão ser registradas.
- As informações encontradas deverão passar por validação antes de serem utilizadas.

---

# 💡 Inteligência do Módulo

Sempre que existirem múltiplos resultados para um mesmo pedido, o sistema deverá:

- Priorizar registros ativos;
- Priorizar dados mais recentes;
- Eliminar duplicidades;
- Informar ao operador qualquer conflito encontrado.

---

# 📈 Benefícios

A utilização do Motor de Busca de Dados proporcionará:

- Eliminação de consultas manuais;
- Maior velocidade operacional;
- Redução de erros;
- Padronização das informações;
- Melhor integração entre módulos;
- Maior confiabilidade dos dados.

---

# ✅ Próximo Capítulo

➡️ **08 - Comparador Inteligente**

No próximo capítulo será detalhado como o sistema analisará todas as tarifas encontradas, identificará a melhor opção disponível e preparará as informações para a tomada de decisão do operador.