# 📧 Central de Comunicação por E-mail

> **Módulo:** Central de Comunicação por E-mail
> **Documento:** 10
> **Versão:** 1.0.0

---

# 📖 Objetivo

A Central de Comunicação por E-mail é responsável por informar o cliente sobre a retarificação identificada durante o processo de emissão, apresentando os novos valores encontrados e anexando toda a documentação gerada pelo sistema.

O envio do e-mail ocorrerá somente após a aprovação do operador na Central de Conferência.

Todo envio será registrado para fins de auditoria e rastreabilidade.

---

# 🎯 Objetivos

Este módulo deverá ser capaz de:

- Localizar automaticamente o e-mail do cliente;
- Validar o endereço de e-mail;
- Montar automaticamente o assunto;
- Gerar o corpo do e-mail;
- Inserir os valores pesquisados;
- Informar qual trecho sofreu retarificação;
- Anexar o PDF da operação;
- Enviar o e-mail;
- Registrar todo o processo.

---

# 🏗️ Fluxo Geral

```text
Central de Conferência

        │

        ▼

Operador confirma

        │

        ▼

Buscar e-mail do cliente

        │

        ▼

Montar assunto

        │

        ▼

Montar corpo do e-mail

        │

        ▼

Anexar PDF

        │

        ▼

Enviar e-mail

        │

        ▼

Registrar envio
```

---

# 📥 Informações Recebidas

O módulo receberá:

- Número da OP;
- Número do Pedido;
- Nome do Cliente;
- Passageiros;
- Companhia aérea;
- Trecho retarifado;
- Valores encontrados;
- Melhor tarifa;
- PDF gerado.

---

# 📧 Localização do Destinatário

Utilizando o número do pedido, o sistema localizará automaticamente o e-mail do cliente.

Exemplo:

```text
Pedido

↓

908082

↓

cliente@empresa.com.br
```

Caso mais de um endereço seja encontrado, todos serão apresentados ao operador para conferência.

---

# 📝 Assunto do E-mail

O assunto será gerado automaticamente.

Exemplo:

```text
Retarificação da Reserva - Pedido 908082
```

O operador poderá editar o assunto antes do envio.

---

# 📄 Corpo do E-mail

O sistema utilizará modelos configuráveis.

Exemplo:

```text
Prezado(a),

Durante o processo de emissão da sua reserva foi identificada uma alteração tarifária.

Realizamos uma nova pesquisa e encontramos as seguintes opções:

Wooba: R$ 1.495,89

Kontrip: R$ 1.362,42

LATAM: R$ 958,80

Valor original do pedido:

R$ 1.417,73

Trecho retarifado:

LATAM

Segue em anexo o relatório completo da pesquisa.

Permanecemos à disposição.

Equipe VIAZA
```

---

# 📎 Anexos

O sistema deverá anexar automaticamente:

- PDF da pesquisa;
- Outros documentos configurados (quando necessário).

Caso o PDF não esteja disponível, o envio será bloqueado até que o documento seja gerado.

---

# ✏️ Campos Editáveis

Antes do envio, o operador poderá alterar:

- Destinatário;
- Assunto;
- Corpo do e-mail;
- Anexos.

Todas as alterações deverão ser registradas.

---

# ✔️ Validações

Antes do envio, o sistema verificará:

✅ Existe destinatário.

✅ O e-mail possui formato válido.

✅ Existe um PDF anexado.

✅ O assunto foi preenchido.

✅ O corpo do e-mail foi gerado.

Caso alguma validação falhe, o envio será bloqueado.

---

# 📤 Processo de Envio

Após a confirmação:

1. Validar informações;
2. Gerar mensagem final;
3. Inserir anexos;
4. Enviar;
5. Aguardar confirmação do servidor;
6. Registrar o resultado.

---

# ⚠️ Tratamento de Erros

## Destinatário não encontrado

Solicitar preenchimento manual.

---

## E-mail inválido

Exibir alerta ao operador.

---

## Falha no servidor SMTP/API

Permitir nova tentativa.

Registrar o erro.

---

## PDF ausente

Bloquear envio.

Solicitar geração do documento.

---

## Erro inesperado

Registrar ocorrência.

Permitir novo envio.

---

# 📊 Registro

Cada envio deverá registrar:

- OP;
- Pedido;
- Destinatário;
- Assunto;
- Operador;
- Data;
- Hora;
- Status;
- Tempo do envio.

---

# 📚 Histórico

Será possível consultar:

- Todos os e-mails enviados;
- Destinatários;
- Assuntos;
- Horário;
- Operador responsável;
- Status do envio.

---

# 🔄 Reenvio

O operador poderá reenviar um e-mail anteriormente enviado.

O sistema utilizará o mesmo conteúdo aprovado ou permitirá alterações antes do novo envio.

---

# 🔒 Segurança

O sistema nunca enviará um e-mail automaticamente sem aprovação do operador.

Todos os envios deverão ser registrados para auditoria.

---

# 🧩 Templates

Os modelos de e-mail serão configuráveis.

Exemplo:

```text
Assunto

Retarificação da Reserva - Pedido {pedido}

-----------------------------------

Cliente

{cliente}

-----------------------------------

Valores

Wooba: {wooba}

Kontrip: {kontrip}

LATAM: {latam}

-----------------------------------

Valor Original

{valor_original}

-----------------------------------

Trecho

{trecho}

-----------------------------------

Anexo

PDF da Pesquisa
```

As variáveis serão substituídas automaticamente.

---

# 📨 Cópias (CC e CCO)

O sistema permitirá configurar destinatários adicionais.

Exemplos:

- Comercial responsável (CC);
- Equipe operacional (CC);
- Gestora do setor (CCO, se configurado).

Essa funcionalidade será opcional e totalmente configurável.

---

# 🚀 Melhorias Futuras

O módulo poderá evoluir para:

- Assinaturas personalizadas por operador;
- Templates por cliente;
- Idiomas diferentes;
- Envio em lote;
- Agendamento de envio;
- Confirmação de leitura (quando suportado pelo servidor de e-mail);
- Integração com Microsoft 365 e Google Workspace.

---

# 🔗 Integração

Recebe informações de:

- Central de Conferência;
- Motor de Busca de Dados;
- Comparador;
- Gerador de PDF.

Envia informações para:

- Registro;
- Dashboard;
- Histórico.

---

# 📌 Observações para Desenvolvimento

O módulo deverá ser independente do provedor de e-mail.

A arquitetura deverá permitir a utilização de diferentes formas de envio, como:

- SMTP;
- Microsoft 365 (Graph API);
- Gmail API;
- APIs de serviços de e-mail corporativo.

Isso garante maior flexibilidade e facilita futuras integrações.

---

# 💡 Inteligência do Módulo

Antes do envio, o sistema deverá realizar uma análise automática do conteúdo para verificar:

- Campos obrigatórios preenchidos;
- Valores inconsistentes;
- PDF anexado;
- Destinatário válido;
- Assunto preenchido;
- Informações da retarificação completas.

Caso alguma inconsistência seja identificada, o operador será alertado antes do envio.

---

# ✅ Próximo Capítulo

➡️ **11 - Gerador de PDF**

O próximo módulo detalhará como o aplicativo criará automaticamente um relatório completo da operação, consolidando todas as informações pesquisadas para anexação na OP e envio ao cliente.