# 🖥️ Central de Conferência Operacional

> **Módulo:** Central de Conferência Operacional
> **Documento:** 08
> **Versão:** 1.0.0

---

# 📖 Objetivo

A Central de Conferência Operacional é responsável por apresentar ao operador todas as informações coletadas e processadas pelo sistema antes da execução de qualquer ação automática.

Seu objetivo é garantir que o operador tenha total controle sobre a operação, podendo validar, corrigir ou complementar os dados antes do envio das comunicações e da geração da documentação.

Nenhuma ação externa será executada sem a confirmação do operador.

---

# 🎯 Objetivos

Este módulo deverá permitir ao operador:

- Conferir todas as informações da OP;
- Visualizar todas as tarifas pesquisadas;
- Confirmar a melhor opção encontrada;
- Alterar informações quando necessário;
- Escolher outra tarifa;
- Revisar a mensagem do WhatsApp;
- Revisar o e-mail;
- Revisar o PDF;
- Aprovar ou cancelar toda a operação.

---

# 🏗️ Fluxo Geral

```text
Pesquisa concluída
        │
        ▼
Comparador finalizado
        │
        ▼
Busca de Dados concluída
        │
        ▼
Abrir Central de Conferência
        │
        ▼
Operador revisa tudo
        │
        ▼
Aprovar?
   │
 ┌─┴──────────────┐
 │                │
Não             Sim
 │                │
 ▼                ▼
Encerrar      Executar automações
```

---

# 📋 Informações Exibidas

A tela deverá apresentar todas as informações organizadas por seções.

---

# 📌 Dados da OP

- Número da OP
- Número do Pedido
- Operador
- Passageiro
- Companhia aérea
- Origem
- Destino
- Datas
- Situação

---

# ✈️ Resultado da Pesquisa

Tabela contendo todos os portais pesquisados.

| Portal | Valor | Situação |
|---------|-------:|----------|
| Wooba | R$ 1.495,89 | Encontrado |
| Kontrip | R$ 1.362,42 | Encontrado |
| LATAM | R$ 958,80 | Melhor opção |

O menor valor deverá ser destacado visualmente.

---

# 🛫 Identificação do Trecho

O sistema deverá informar claramente:

- Ida retarifada;
- Volta retarifada;
- Ambos os trechos;
- Trecho não identificado.

Caso não seja possível identificar automaticamente, o operador poderá selecionar manualmente.

---

# 👤 Dados do Cliente

- Nome
- E-mail
- Comercial responsável
- Grupo do WhatsApp

Todos os campos poderão ser editados antes do envio.

---

# 💬 Pré-visualização do WhatsApp

A mensagem será exibida exatamente como será enviada.

Exemplo:

```text
Pedido 908082 / VZ11988

Wooba: R$ 1.495,89
Kontrip: R$ 1.362,42
LATAM: R$ 958,80

Valor Total do Pedido: R$ 1.417,73

Trecho LATAM retarifado.

@Comercial
```

O operador poderá editar o texto antes do envio.

---

# 📧 Pré-visualização do E-mail

A tela deverá exibir:

- Destinatário
- Assunto
- Corpo do e-mail
- Anexos

Todo o conteúdo poderá ser alterado antes do envio.

---

# 📄 Pré-visualização do PDF

O operador poderá visualizar o documento que será anexado à OP.

O PDF deverá conter:

- Dados da OP;
- Tarifas pesquisadas;
- Melhor opção;
- Data e hora;
- Operador;
- Observações.

---

# ✏️ Campos Editáveis

Os seguintes campos poderão ser alterados:

- E-mail;
- Comercial;
- Grupo do WhatsApp;
- Mensagem;
- Assunto;
- Corpo do e-mail;
- Portal escolhido;
- Tarifa escolhida;
- Trecho retarifado.

Toda alteração deverá ser registrada no histórico.

---

# 🔄 Atualização Manual

O operador poderá solicitar uma nova pesquisa.

Exemplo:

```
Atualizar Pesquisa
```

O sistema executará novamente apenas os módulos necessários.

---

# 🚦 Validações

Antes de liberar a confirmação, o sistema deverá verificar:

✅ Existe uma tarifa selecionada.

✅ Existe um e-mail válido.

✅ Existe um grupo do WhatsApp.

✅ Existe um comercial responsável.

✅ Existe um PDF gerado.

Caso alguma informação esteja ausente, o sistema deverá informar claramente ao operador.

---

# ⚠️ Alertas

A tela deverá exibir alertas quando:

- Nenhum portal retornou resultados;
- O menor valor não pertence à companhia original;
- O trecho não foi identificado;
- O cliente não possui e-mail;
- O grupo do WhatsApp não foi localizado.

---

# 🟢 Botões de Ação

A interface deverá possuir as seguintes ações:

✅ Confirmar Operação

Executa:

- WhatsApp;
- E-mail;
- PDF;
- Registro.

---

🔄 Atualizar Pesquisa

Realiza uma nova pesquisa nos portais.

---

📄 Visualizar PDF

Abre o documento completo.

---

❌ Cancelar

Encerra a operação.

Nenhuma mensagem será enviada.

---

# 📊 Resumo da Operação

Antes da confirmação, o sistema deverá apresentar um resumo.

Exemplo:

```text
Pesquisa realizada com sucesso.

4 portais consultados.

Melhor tarifa localizada.

Cliente identificado.

Comercial identificado.

Grupo localizado.

PDF gerado.

Sistema pronto para envio.
```

---

# 🛡️ Segurança

Nenhuma automação poderá ser executada sem aprovação do operador.

Mesmo que todas as informações estejam corretas, a confirmação manual será obrigatória.

Essa regra evita envios incorretos e garante que o operador mantenha o controle da operação.

---

# 📋 Registro

O sistema deverá registrar:

- Horário de abertura da conferência;
- Horário da confirmação;
- Alterações realizadas;
- Usuário responsável;
- Tempo gasto na conferência.

---

# 🚀 Melhorias Futuras

A Central de Conferência poderá evoluir para incluir:

- Destaque automático das diferenças entre tarifas;
- Comparação gráfica de preços;
- Sugestões inteligentes da IA;
- Validação automática de inconsistências;
- Assinatura digital da operação;
- Aprovação em dois níveis para operações críticas.

---

# 🧩 Integração

Este módulo recebe informações de:

- Leitura da OP;
- Motor de Análise;
- Classificação;
- Motor de Pesquisa;
- Comparador;
- Motor de Busca de Dados.

Após a confirmação do operador, os dados serão enviados para:

- WhatsApp;
- E-mail;
- PDF;
- Registro;
- Dashboard;
- Histórico.

---

# 💡 Observações para Desenvolvimento

A Central de Conferência deverá ser desenvolvida como uma única tela contendo todas as informações da operação.

O objetivo é permitir que o operador visualize e valide tudo sem precisar alternar entre diferentes janelas ou módulos.

A interface deverá priorizar rapidez, clareza e organização, reduzindo o tempo de análise e aumentando a produtividade.

---

# ✅ Próximo Capítulo

➡️ **09 - Envio do WhatsApp**

O próximo documento detalhará como o sistema montará automaticamente as mensagens, identificará o grupo correto, mencionará o comercial responsável e registrará o resultado do envio.