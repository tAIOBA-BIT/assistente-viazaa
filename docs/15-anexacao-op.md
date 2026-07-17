# 📎 Gerenciador de Anexos da OP

> **Módulo:** Gerenciador de Anexos da OP
> **Documento:** 12
> **Versão:** 1.0.0

---

# 📖 Objetivo

O Gerenciador de Anexos da OP é responsável por anexar automaticamente todos os documentos gerados pelo aplicativo diretamente na Ordem de Produção (OP).

Esse processo garante que toda a documentação da operação permaneça armazenada no sistema da empresa, permitindo futuras consultas, auditorias e rastreamento completo da operação.

O operador não precisará realizar uploads manualmente.

---

# 🎯 Objetivos

O módulo deverá ser capaz de:

- Localizar automaticamente a área de anexos da OP;
- Inserir o PDF gerado;
- Validar se o upload foi concluído;
- Registrar a operação;
- Informar falhas ao operador;
- Permitir novos anexos futuramente.

---

# 🏗️ Fluxo Geral

```text
PDF Gerado

        │

        ▼

Abrir OP

        │

        ▼

Localizar área de anexos

        │

        ▼

Selecionar arquivo

        │

        ▼

Enviar arquivo

        │

        ▼

Validar Upload

        │

        ▼

Registrar Operação
```

---

# 📥 Informações Recebidas

O módulo receberá:

- Número da OP;
- PDF gerado;
- Operador responsável;
- Data;
- Hora.

---

# 📂 Tipos de Arquivos

Inicialmente o sistema deverá anexar:

- PDF da Pesquisa.

A arquitetura deverá permitir futuramente:

- Capturas de tela;
- Relatórios;
- Planilhas;
- Arquivos do cliente;
- Comprovantes;
- Outros documentos.

---

# 🔍 Localização da Área de Anexos

O sistema deverá identificar automaticamente o local destinado ao upload de arquivos na OP.

```text
OP

↓

Área de Anexos

↓

Selecionar Arquivo

↓

Enviar
```

Caso a estrutura da página seja alterada, apenas o conector responsável pela OP deverá ser atualizado.

---

# 📤 Processo de Upload

O sistema deverá executar as seguintes etapas:

1. Abrir a área de anexos;
2. Selecionar o PDF gerado;
3. Iniciar o upload;
4. Aguardar a conclusão;
5. Confirmar o sucesso da operação;
6. Registrar o resultado.

---

# ✔️ Validação

Após o envio, o sistema deverá confirmar:

✅ Arquivo localizado.

✅ Upload iniciado.

✅ Upload concluído.

✅ Arquivo visível na lista de anexos.

Somente após essas validações o processo será considerado concluído.

---

# ⚠️ Tratamento de Erros

## Área de anexos não encontrada

Registrar erro.

Solicitar intervenção do operador.

---

## Upload interrompido

Realizar nova tentativa automática.

Caso o erro persista, informar o operador.

---

## Arquivo inexistente

Solicitar nova geração do PDF.

---

## Sessão expirada

Solicitar novo login.

---

## Erro inesperado

Registrar:

- Data;
- Hora;
- OP;
- Operador;
- Descrição do erro.

---

# 🔄 Nova Tentativa

Em caso de falha temporária, o sistema poderá realizar novas tentativas automaticamente.

Exemplo:

```text
Tentativa 1

↓

Erro

↓

Aguardar 5 segundos

↓

Tentativa 2

↓

Erro

↓

Aguardar 10 segundos

↓

Tentativa 3

↓

Falhou

↓

Informar Operador
```

---

# 📋 Registro

Cada upload deverá registrar:

- OP;
- Pedido;
- Nome do arquivo;
- Data;
- Hora;
- Operador;
- Tempo do upload;
- Resultado.

---

# 📚 Histórico

Todas as operações deverão permanecer disponíveis para consulta.

Será possível visualizar:

- Arquivos anexados;
- Data;
- Operador;
- Status;
- Tempo do upload.

---

# 🛡️ Segurança

O sistema nunca deverá excluir anexos existentes.

Sempre que um novo documento for enviado, ele deverá ser adicionado à lista de anexos da OP.

Caso já exista um PDF semelhante, o operador poderá decidir:

- Manter ambos;
- Substituir;
- Cancelar o envio.

---

# 📦 Nome dos Arquivos

Os arquivos deverão seguir um padrão de nomenclatura.

Exemplo:

```text
Retarificacao_OP_VZ11988_Pedido_908082_2026-07-17.pdf
```

Esse padrão facilitará pesquisas futuras e evitará arquivos duplicados.

---

# 📊 Indicador de Progresso

Durante o upload, o operador deverá visualizar uma barra de progresso.

```text
Enviando...

██████████░░░░░░░░░░

52%
```

Após a conclusão:

```text
Upload realizado com sucesso.
```

---

# 🚀 Melhorias Futuras

Este módulo poderá evoluir para:

- Upload de múltiplos arquivos simultaneamente;
- Compressão automática de documentos;
- Versionamento de anexos;
- Organização automática por categorias;
- Assinatura digital dos documentos;
- Verificação automática de integridade.

---

# 🔗 Integração

Recebe informações de:

- Gerador Inteligente de Relatórios (PDF);
- Central de Conferência.

Envia informações para:

- Registro;
- Dashboard;
- Histórico;
- Encerramento da Operação.

---

# 📌 Observações para Desenvolvimento

O módulo deverá ser totalmente independente da geração do PDF.

Sua única responsabilidade será anexar documentos à OP.

Isso permitirá que, no futuro, qualquer tipo de arquivo possa ser anexado utilizando o mesmo mecanismo.

---

# 💡 Fila de Uploads

O sistema deverá possuir uma fila de uploads.

Caso mais de um arquivo precise ser anexado, eles serão enviados automaticamente em sequência.

```text
Fila

↓

PDF

↓

Print da Pesquisa

↓

Comprovante

↓

Documento do Cliente

↓

Upload Concluído
```

Essa abordagem evita conflitos e facilita futuras expansões.

---

# 📈 Benefícios

A utilização do Gerenciador de Anexos proporcionará:

- Eliminação do upload manual;
- Padronização dos documentos;
- Maior rastreabilidade;
- Redução de erros;
- Auditoria simplificada;
- Organização das OPs.

---

# ✅ Próximo Capítulo

➡️ **13 - Registro Inteligente das Operações**

O próximo módulo apresentará como o sistema registrará automaticamente todas as ações executadas durante a operação, formando uma trilha completa de auditoria.