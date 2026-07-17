# 🌎 Consulta Inteligente de Tarifas

> **Módulo:** Consulta Inteligente de Tarifas
> **Documento:** 14
> **Versão:** 1.0.0

---

# 📖 Objetivo

O módulo de Consulta Inteligente de Tarifas permite ao operador pesquisar qualquer Ordem de Produção (OP), independentemente de existir uma retarificação.

Seu objetivo é realizar uma consulta completa em todos os portais configurados, localizar as melhores tarifas disponíveis e apresentar ao operador um comparativo detalhado, auxiliando na tomada de decisão antes da emissão.

Diferentemente da Pesquisa Automática, que é acionada apenas quando uma retarificação é detectada, este módulo pode ser utilizado manualmente a qualquer momento.

---

# 🎯 Objetivos

O módulo deverá ser capaz de:

- Consultar qualquer OP aberta;
- Pesquisar simultaneamente todos os portais configurados;
- Comparar tarifas;
- Identificar a melhor opção disponível;
- Informar diferenças de preço;
- Exibir resultados organizados;
- Permitir atualização manual das pesquisas;
- Registrar todas as consultas realizadas.

---

# 🏗️ Funcionamento Geral

O operador poderá iniciar uma consulta sempre que desejar.

O sistema utilizará os dados da OP para realizar pesquisas automáticas em todos os portais disponíveis.

```text
Operador abre uma OP
        │
        ▼
Seleciona "Consulta Geral"
        │
        ▼
Aplicativo coleta os dados da OP
        │
        ▼
Pesquisa todos os portais
        │
        ▼
Compara os resultados
        │
        ▼
Exibe o melhor cenário
```

---

# 📥 Informações Utilizadas

O módulo utilizará automaticamente os seguintes dados da OP:

- Origem;
- Destino;
- Datas;
- Companhia aérea;
- Passageiros;
- Classe tarifária (quando disponível);
- Tipo da viagem;
- Número do Pedido;
- Número da OP.

Nenhum dado precisará ser digitado manualmente.

---

# 🌐 Portais Consultados

O sistema deverá permitir a consulta em todos os portais cadastrados.

Exemplo:

- Wooba;
- Kontrip;
- Portal da Companhia Aérea;
- Outros portais adicionados futuramente.

Cada portal será pesquisado de forma independente.

---

# 🔍 Processo de Pesquisa

Cada portal seguirá o mesmo fluxo.

```text
Abrir Portal
        │
        ▼
Realizar Login (caso necessário)
        │
        ▼
Inserir dados da viagem
        │
        ▼
Pesquisar
        │
        ▼
Capturar resultados
        │
        ▼
Enviar ao Comparador
```

Caso o operador já esteja autenticado, o sistema utilizará a sessão existente.

---

# 💰 Comparação das Tarifas

Após finalizar todas as pesquisas, o sistema organizará os resultados.

Exemplo:

| Portal | Valor |
|---------|-------:|
| Wooba | R$ 1.495,89 |
| Kontrip | R$ 1.362,42 |
| LATAM | R$ 958,80 |

---

# 🏆 Melhor Tarifa

O sistema deverá destacar automaticamente:

- Menor valor;
- Portal correspondente;
- Economia em relação às demais opções.

Exemplo:

```
Melhor opção encontrada

Portal: LATAM

Valor:

R$ 958,80

Economia:

R$ 537,09
```

---

# ✈️ Comparação por Trecho

Sempre que possível, o sistema deverá comparar os trechos individualmente.

Exemplo:

```text
IDA

Wooba

Kontrip

LATAM

↓

Melhor tarifa
```

```text
VOLTA

Wooba

Kontrip

LATAM

↓

Melhor tarifa
```

Caso existam tarifas diferentes para ida e volta, elas deverão ser destacadas.

---

# 📊 Tela de Resultados

O operador visualizará uma tela semelhante à seguinte:

| Portal | Ida | Volta | Total | Situação |
|---------|----:|------:|------:|-----------|
| Wooba | R$ 720 | R$ 775 | R$ 1.495 | Disponível |
| Kontrip | R$ 650 | R$ 712 | R$ 1.362 | Disponível |
| LATAM | R$ 490 | R$ 468 | R$ 958 | Disponível |

O menor valor será destacado visualmente.

---

# 🔄 Atualização da Pesquisa

O operador poderá solicitar uma nova pesquisa a qualquer momento.

Exemplo:

```
Atualizar Pesquisa
```

O sistema repetirá automaticamente todas as consultas.

---

# 📜 Histórico de Consultas

Cada consulta deverá ser registrada.

Informações armazenadas:

- Data;
- Hora;
- Operador;
- Pedido;
- OP;
- Portais consultados;
- Valores encontrados;
- Melhor tarifa.

---

# ⚠️ Tratamento de Erros

Caso algum portal apresente erro, o sistema deverá continuar consultando os demais.

Exemplo:

```
Wooba

Indisponível

↓

Pesquisar Kontrip

↓

Pesquisar LATAM

↓

Continuar fluxo
```

Nenhum erro deverá interromper toda a consulta.

---

# 🔒 Regras

O módulo nunca deverá alterar informações da OP.

Seu único objetivo será consultar e apresentar informações.

Nenhuma compra será realizada automaticamente.

Nenhuma emissão será efetuada.

Nenhum pagamento será autorizado.

Toda decisão final permanecerá sob responsabilidade do operador.

---

# 📈 Indicadores

O módulo deverá fornecer informações ao Dashboard.

Exemplo:

- Quantidade de consultas realizadas;
- Portal mais rápido;
- Portal com menor preço;
- Economia média encontrada;
- Tempo médio das pesquisas.

---

# 🚀 Melhorias Futuras

O módulo poderá evoluir para:

- Pesquisa simultânea em múltiplas companhias aéreas;
- Comparação de tarifas por horário;
- Comparação por tempo de voo;
- Comparação por quantidade de bagagens;
- Comparação por franquia de bagagem;
- Comparação por política de cancelamento;
- Comparação por programa de milhas;
- Sugestão automática da melhor opção considerando preço e benefícios.

---

# 🔗 Dependências

Recebe informações de:

- Leitura Automática;
- Motor de Análise;
- Classificação.

Envia informações para:

- Comparador;
- Tela de Conferência;
- Registro;
- Dashboard;
- Histórico.

---

# 📝 Observações para Desenvolvimento

O módulo deverá executar as consultas em paralelo sempre que possível, reduzindo o tempo total de processamento.

Cada portal deverá possuir um conector independente, permitindo manutenção individual sem impactar os demais.

A arquitetura deverá permitir adicionar novos portais futuramente sem necessidade de alterar os módulos existentes.

---

# 💡 Cenários de Utilização

## Cenário 1 – OP sem retarificação

O operador deseja verificar se existe uma tarifa melhor antes de emitir.

O sistema realiza a consulta completa em todos os portais e apresenta o melhor preço disponível.

---

## Cenário 2 – OP com retarificação

O Motor de Análise detecta uma retarificação.

O módulo é acionado automaticamente para pesquisar novas tarifas.

Após a pesquisa, os resultados são enviados ao Comparador.

---

## Cenário 3 – Consulta Manual

O operador deseja apenas comparar preços para auxiliar uma negociação com o cliente.

Nenhuma mensagem é enviada.

Nenhum PDF é gerado.

Apenas a pesquisa é realizada.

---

# ✅ Próximo Capítulo

➡️ **15 - Dashboard**

O próximo documento apresentará o painel gerencial do Assistente VIAZA, contendo métricas em tempo real, indicadores operacionais, gráficos de desempenho, economia gerada, produtividade e acompanhamento completo das operações.