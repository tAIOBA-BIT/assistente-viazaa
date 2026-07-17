# 📄 Gerador Inteligente de Relatórios (PDF)

> **Módulo:** Gerador Inteligente de Relatórios (PDF)
> **Documento:** 11
> **Versão:** 1.0.0

---

# 📖 Objetivo

O Gerador Inteligente de Relatórios é responsável por criar automaticamente um documento em formato PDF contendo todas as informações da operação.

O documento servirá como registro oficial da retarificação, podendo ser enviado ao cliente, anexado na Ordem de Produção (OP) e armazenado para futuras auditorias.

O PDF deverá ser padronizado, organizado e de fácil leitura.

---

# 🎯 Objetivos

O módulo deverá ser capaz de:

- Gerar automaticamente um PDF profissional;
- Consolidar todas as informações da operação;
- Inserir a pesquisa realizada em todos os portais;
- Destacar a melhor tarifa encontrada;
- Informar o trecho retarifado;
- Registrar data, hora e operador;
- Inserir observações relevantes;
- Preparar o documento para anexação na OP e envio por e-mail.

---

# 🏗️ Fluxo Geral

```text
Central de Conferência

        │

        ▼

Operador confirma

        │

        ▼

Receber informações

        │

        ▼

Montar relatório

        │

        ▼

Gerar PDF

        │

        ▼

Validar documento

        │

        ▼

Enviar para:

• E-mail

• OP

• Histórico
```

---

# 📥 Informações Recebidas

O módulo receberá:

- Número da OP;
- Número do Pedido;
- Nome do Cliente;
- Nome do Passageiro;
- Companhia Aérea;
- Origem;
- Destino;
- Datas;
- Valores pesquisados;
- Melhor tarifa;
- Trecho retarifado;
- Operador responsável;
- Data e hora.

---

# 📋 Estrutura do Documento

O PDF deverá seguir uma estrutura padronizada.

```text
Capa

↓

Resumo

↓

Dados da OP

↓

Pesquisa dos Portais

↓

Comparativo

↓

Melhor Tarifa

↓

Trecho Retarifado

↓

Observações

↓

Histórico da Operação
```

---

# 🏢 Cabeçalho

O documento deverá conter:

- Logotipo da empresa;
- Nome do aplicativo;
- Data da geração;
- Número do relatório;
- Número da OP;
- Número do Pedido.

---

# 📌 Resumo da Operação

Exemplo:

```
Pedido: 908082

OP: VZ11988

Passageiro:

João da Silva

Companhia:

LATAM

Status:

Retarificação
```

---

# ✈️ Pesquisa dos Portais

Tabela contendo todos os resultados.

| Portal | Valor | Situação |
|---------|-------:|----------|
| Wooba | R$ 1.495,89 | Encontrado |
| Kontrip | R$ 1.362,42 | Encontrado |
| LATAM | R$ 958,80 | Melhor opção |

A melhor tarifa deverá ser destacada.

---

# 📊 Comparativo Financeiro

O relatório deverá apresentar:

- Valor original do pedido;
- Melhor tarifa encontrada;
- Diferença de valor;
- Economia obtida (quando houver).

Exemplo:

```text
Valor Original

R$ 1.417,73

↓

Melhor Tarifa

R$ 958,80

↓

Economia

R$ 458,93
```

---

# 🛫 Trecho Retarifado

O documento deverá informar claramente:

- Ida;
- Volta;
- Ambos os trechos.

Exemplo:

```
Trecho LATAM retarifado.
```

---

# 📝 Observações

As observações da OP deverão ser registradas integralmente.

Caso o operador tenha realizado alterações durante a conferência, essas modificações também deverão ser documentadas.

---

# 👨‍💻 Dados do Operador

O PDF deverá registrar:

- Nome do operador;
- Data;
- Hora;
- Tempo total da operação.

---

# 📎 Anexos

O sistema deverá permitir anexar documentos complementares.

Exemplos:

- Capturas de tela;
- Relatórios adicionais;
- Arquivos fornecidos pelo cliente.

---

# ✔️ Validação

Antes da geração, o sistema deverá verificar:

✅ Existe OP.

✅ Existe Pedido.

✅ Existe pesquisa.

✅ Existe tarifa selecionada.

✅ Existe trecho identificado.

Caso alguma informação esteja ausente, o sistema alertará o operador.

---

# 📤 Destinos do PDF

Após a geração, o documento poderá ser utilizado em:

- Envio por e-mail;
- Anexação na OP;
- Histórico da operação;
- Dashboard;
- Auditorias futuras.

---

# 📋 Registro

Toda geração deverá registrar:

- Número do relatório;
- OP;
- Pedido;
- Operador;
- Data;
- Hora;
- Tempo da geração.

---

# 🔒 Segurança

Após sua geração, o PDF não poderá ser alterado pelo aplicativo.

Caso seja necessário realizar alterações, um novo documento deverá ser gerado, preservando o histórico.

---

# 🧾 Assinatura Digital (Opcional)

O sistema poderá incluir:

- Nome do operador;
- Data;
- Hora;
- Identificador único do relatório (UUID).

No futuro, poderá ser implementada assinatura digital para garantir autenticidade.

---

# 🎨 Layout

O relatório deverá seguir um padrão visual corporativo.

Características desejadas:

- Cabeçalhos destacados;
- Tabelas organizadas;
- Cores padronizadas;
- Ícones para facilitar a leitura;
- Destaque para a melhor tarifa;
- Numeração das páginas;
- Rodapé com informações do sistema.

---

# 🚀 Melhorias Futuras

O Gerador Inteligente poderá evoluir para incluir:

- QR Code para validação do relatório;
- Gráficos comparativos de tarifas;
- Linha do tempo da operação;
- Assinatura digital certificada;
- Exportação para outros formatos (Excel, Word, HTML);
- Templates personalizados por cliente.

---

# 🔗 Integração

Recebe informações de:

- Leitura da OP;
- Motor de Análise;
- Classificação;
- Motor de Pesquisa;
- Comparador;
- Motor de Busca de Dados;
- Central de Conferência.

Envia informações para:

- E-mail;
- Anexação na OP;
- Histórico;
- Dashboard;
- Registro.

---

# 💡 Templates

O sistema deverá permitir diferentes modelos de PDF.

Exemplos:

- Modelo Corporativo;
- Modelo Executivo;
- Modelo Resumido;
- Modelo Completo;
- Modelo para Auditoria.

A escolha do template poderá ser automática ou realizada pelo operador.

---

# 🛡️ Observações para Desenvolvimento

O documento deverá ser gerado utilizando um mecanismo de templates.

Nenhum conteúdo deverá ficar fixo no código.

Isso permitirá alterar o layout, incluir novos campos ou personalizar o documento sem necessidade de modificar a lógica do sistema.

O PDF deverá ser responsivo para impressão em A4 e manter boa legibilidade tanto em tela quanto impresso.

---

# 📈 Benefícios

A utilização do Gerador Inteligente de Relatórios proporcionará:

- Padronização da documentação;
- Maior transparência das operações;
- Facilidade em auditorias;
- Redução de erros;
- Registro completo das retarificações;
- Melhor comunicação com clientes e equipes internas.

---

# ✅ Próximo Capítulo

➡️ **12 - Anexação Automática na OP**

No próximo documento será detalhado como o aplicativo localizará automaticamente o campo de anexos da Ordem de Produção, realizará o upload do PDF gerado e registrará a conclusão da operação.