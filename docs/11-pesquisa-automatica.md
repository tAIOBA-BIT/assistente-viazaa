# 🌐 Motor de Pesquisa Inteligente

> **Módulo:** Motor de Pesquisa Inteligente  
> **Documento:** 06  
> **Versão:** 1.0.0

---

# 📖 Objetivo

O Motor de Pesquisa Inteligente é responsável por realizar automaticamente pesquisas de tarifas em todos os portais configurados pelo sistema.

Seu objetivo é reproduzir o trabalho que atualmente é realizado manualmente pelos operadores, consultando diferentes plataformas de emissão e retornando todas as opções disponíveis para comparação.

Este módulo deverá atuar de forma rápida, padronizada e confiável, reduzindo significativamente o tempo necessário para localizar a melhor tarifa.

---

# 🎯 Objetivos

O módulo deverá ser capaz de:

- Ler os dados recebidos da OP;
- Identificar quais portais devem ser consultados;
- Realizar pesquisas automáticas;
- Coletar todas as tarifas encontradas;
- Padronizar os resultados;
- Detectar erros de pesquisa;
- Repetir consultas quando necessário;
- Encaminhar todas as informações ao Comparador.

---

# 🏗️ Funcionamento Geral

Após receber uma solicitação do Orquestrador de Fluxo, o Motor de Pesquisa iniciará automaticamente a consulta nos portais habilitados.

```text
Receber solicitação

        │

        ▼

Carregar dados da OP

        │

        ▼

Selecionar portais

        │

        ▼

Executar pesquisas

        │

        ▼

Coletar resultados

        │

        ▼

Validar informações

        │

        ▼

Enviar ao Comparador
```

---

# 📥 Dados Recebidos

O módulo receberá informações como:

- Companhia aérea
- Origem
- Destino
- Datas
- Passageiros
- Classe tarifária (quando disponível)
- Número do pedido
- Número da OP

---

# 🌍 Portais

O sistema deverá permitir a configuração de diversos portais.

Exemplo:

- Wooba
- Kontrip
- Portal da companhia aérea
- Outros portais internos

Novos portais poderão ser adicionados futuramente sem necessidade de alterar a arquitetura principal.

---

# 🔐 Autenticação

Todos os portais exigem autenticação.

O login será realizado pelo operador ao iniciar o aplicativo.

Enquanto a sessão permanecer válida, o Motor de Pesquisa utilizará a autenticação existente.

O sistema nunca deverá solicitar novo login durante uma pesquisa, exceto quando a sessão expirar.

---

# 🔎 Processo de Pesquisa

Para cada portal, o sistema deverá:

1. Abrir a página de pesquisa.
2. Preencher automaticamente os campos.
3. Executar a consulta.
4. Aguardar o carregamento completo.
5. Capturar os resultados.
6. Armazenar as tarifas encontradas.

---

# 📋 Informações Coletadas

Sempre que possível, o sistema deverá capturar:

- Valor da tarifa;
- Companhia aérea;
- Trecho;
- Horários;
- Classe tarifária;
- Disponibilidade;
- Taxas;
- Observações do portal.

---

# 🔄 Pesquisa Paralela

Sempre que possível, as pesquisas deverão ocorrer simultaneamente.

Exemplo:

```text
              Pesquisa

                  │

      ┌───────────┼───────────┐

      ▼           ▼           ▼

    Wooba     Kontrip      LATAM

      │           │           │

      └───────────┼───────────┘

                  ▼

       Consolidar resultados
```

Essa abordagem reduz significativamente o tempo total de consulta.

---

# ⏳ Tempo de Espera

Cada portal poderá possuir um tempo máximo de resposta.

Exemplo:

| Portal | Tempo Máximo |
|---------|--------------|
| Wooba | 30 segundos |
| Kontrip | 30 segundos |
| LATAM | 45 segundos |

Caso o tempo seja excedido, o sistema registrará a ocorrência e continuará com os demais portais.

---

# ❌ Tratamento de Erros

O módulo deverá tratar situações como:

## Portal indisponível

Registrar ocorrência e continuar a pesquisa nos demais portais.

---

## Login expirado

Solicitar novo login ao operador.

---

## Pesquisa sem resultados

Registrar a ausência de disponibilidade.

---

## Erro inesperado

Registrar no log.

Continuar normalmente.

---

# 📊 Estrutura dos Resultados

Ao finalizar todas as consultas, os resultados deverão ser organizados.

Exemplo:

```text
Pesquisa

│

├── Wooba

│      Valor

│      Horário

│      Companhia

│

├── Kontrip

│      Valor

│      Horário

│

├── LATAM

│      Valor

│      Horário

│

└── Outros Portais
```

---

# 🔁 Reutilização de Dados

Enquanto o operador permanecer na mesma OP, nenhuma nova pesquisa deverá ser realizada automaticamente.

Os resultados permanecerão em memória.

Uma nova consulta ocorrerá apenas quando:

- A OP mudar;
- O operador solicitar atualização;
- O cache expirar.

---

# 📈 Registro

Toda pesquisa deverá gerar informações para auditoria.

Exemplo:

- Data
- Hora
- Operador
- Portal pesquisado
- Tempo de resposta
- Resultado
- Erros encontrados

---

# 🔗 Integração

Ao concluir a pesquisa, o módulo enviará todos os resultados para o Comparador Inteligente.

Nenhuma decisão será tomada neste módulo.

Sua única responsabilidade é pesquisar e organizar os dados.

---

# 🚀 Melhorias Futuras

O Motor de Pesquisa foi projetado para evoluir continuamente.

Entre as melhorias previstas estão:

- Pesquisa simultânea em dezenas de portais;
- Identificação automática de promoções;
- Consulta utilizando APIs quando disponíveis;
- Cache inteligente;
- Balanceamento de pesquisas;
- Pesquisa por múltiplas companhias;
- Atualização automática dos conectores dos portais.

---

# 📌 Observações para Desenvolvimento

Cada portal deverá possuir um conector independente.

Isso significa que toda a lógica específica de um portal ficará isolada em seu próprio módulo.

Exemplo:

```text
Portais

│

├── Wooba

├── Kontrip

├── LATAM

├── Azul

├── Gol

└── Futuros Portais
```

Caso um portal seja alterado, apenas seu conector precisará ser atualizado, sem impactar os demais módulos do sistema.

---

# 🧩 Arquitetura dos Conectores

Cada conector deverá implementar uma interface padrão.

Todos deverão possuir as seguintes responsabilidades:

- Realizar login (quando necessário);
- Executar pesquisa;
- Capturar resultados;
- Informar erros;
- Retornar dados em formato padronizado.

Isso permitirá adicionar novos portais ao sistema com facilidade e manter o código organizado.

---

# ✅ Próximo Capítulo

➡️ **07 - Leitura dos Portais**

No próximo documento será detalhado como cada conector acessará os portais, localizará os elementos da interface, preencherá os formulários e capturará as informações necessárias para a pesquisa.