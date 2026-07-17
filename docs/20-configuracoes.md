# ⚙️ Configurações do Sistema

> **Módulo:** Configurações
> **Documento:** 17
> **Versão:** 1.0.0

---

# 📖 Objetivo

O módulo de Configurações é responsável por centralizar todas as parametrizações do Assistente VIAZA.

Seu objetivo é permitir que administradores configurem o comportamento do sistema, integrações, regras de negócio, mensagens, usuários e permissões, sem necessidade de alterar o código da aplicação.

Todas as configurações deverão ser armazenadas de forma segura e aplicadas automaticamente durante a execução do sistema.

---

# 🎯 Objetivos

O módulo deverá permitir:

- Configurar usuários;
- Configurar permissões;
- Configurar portais de pesquisa;
- Configurar mensagens;
- Configurar e-mails;
- Configurar grupos de WhatsApp;
- Configurar regras do sistema;
- Configurar geração de PDF;
- Configurar Dashboard;
- Configurar Histórico;
- Configurar notificações;
- Configurar aparência do sistema.

---

# 🏗️ Estrutura Geral

```text
Configurações

│

├── Usuários

├── Permissões

├── Portais

├── Motor de Regras

├── WhatsApp

├── Email

├── PDF

├── Dashboard

├── Histórico

├── Logs

├── Notificações

├── Interface

└── Sistema
```

---

# 👤 Usuários

O administrador poderá:

- Criar usuários;
- Editar usuários;
- Bloquear usuários;
- Excluir usuários;
- Resetar senha;
- Alterar perfil de acesso.

Cada usuário deverá possuir:

- Nome;
- Login;
- Email;
- Cargo;
- Situação;
- Data de criação.

---

# 🔐 Permissões

O sistema deverá possuir controle de acesso por perfil.

## Operador

- Consultar OPs;
- Executar pesquisas;
- Enviar mensagens;
- Gerar PDFs.

---

## Supervisor

Além das permissões do Operador:

- Consultar equipe;
- Consultar Dashboard da equipe;
- Visualizar histórico da equipe.

---

## Gestor

Acesso completo ao sistema.

---

## Administrador

Controle total da aplicação.

Incluindo:

- Configurações;
- Usuários;
- Regras;
- Integrações;
- Logs.

---

# 🌐 Configuração dos Portais

Cada portal poderá ser configurado individualmente.

Exemplo:

```
Portal

Nome

URL

Status

Usuário

Senha

Tempo máximo

Quantidade de tentativas
```

Também deverá ser possível:

- Ativar;
- Desativar;
- Definir prioridade;
- Alterar timeout.

---

# 🧠 Motor de Regras

Toda a lógica do sistema será administrada por esta tela.

Será possível:

- Criar regras;
- Editar regras;
- Desativar regras;
- Excluir regras;
- Definir prioridades.

Exemplo:

| Nome | Tipo | Prioridade |
|-------|------|-----------:|
| Retarificação LATAM | Retarificação | 1 |
| Não Emitido | Erro | 2 |

Também deverá existir um ambiente para testar regras antes de publicá-las.

---

# 💬 WhatsApp

O administrador poderá configurar:

- Grupos;
- Telefones;
- Nome dos grupos;
- Comercial responsável;
- Mensagens padrão;
- Mensagens da gestora.

Exemplo:

```
Grupo Comercial LATAM

Grupo Comercial GOL

Grupo Gestora
```

Também será possível ativar ou desativar envios automáticos.

---

# 📧 Email

Será possível configurar:

- Servidor SMTP;
- Conta remetente;
- Assinatura;
- Modelos de email;
- Assunto padrão;
- Anexos automáticos.

Também deverão existir modelos diferentes para:

- Retarificação;
- Consulta Geral;
- Erros;
- Comunicação interna.

---

# 📄 PDF

Configurações disponíveis:

- Logo da empresa;
- Cabeçalho;
- Rodapé;
- Assinatura;
- Nome do arquivo;
- Pasta temporária;
- Qualidade do PDF.

Também será possível selecionar quais informações serão exibidas.

---

# 📊 Dashboard

Cada usuário poderá personalizar:

- Widgets;
- Gráficos;
- Atualização automática;
- Tema;
- Layout;
- Ordem dos painéis.

---

# 📚 Histórico

Configurações disponíveis:

- Tempo de armazenamento;
- Paginação;
- Quantidade de registros por página;
- Exportação;
- Pesquisa inteligente.

---

# 📋 Logs

Será possível configurar:

- Nível dos logs;
- Retenção;
- Exportação;
- Exclusão automática.

Exemplo:

```
Informação

Aviso

Erro

Crítico
```

---

# 🔔 Notificações

O administrador poderá escolher quais eventos gerarão notificações.

Exemplo:

- Nova retarificação;
- Portal indisponível;
- Falha no envio de email;
- Falha no WhatsApp;
- Erro de login;
- Erro na geração do PDF.

---

# 🎨 Interface

Cada usuário poderá escolher:

- Tema Claro;
- Tema Escuro;
- Idioma;
- Tamanho da fonte;
- Escala da interface;
- Sons do sistema.

---

# ⚙️ Configurações Gerais

O sistema deverá permitir configurar:

- Atualizações automáticas;
- Diretório de arquivos temporários;
- Banco de dados;
- Backup automático;
- Limpeza automática;
- Tempo máximo das pesquisas;
- Quantidade de pesquisas simultâneas.

---

# 💾 Backup

O sistema deverá permitir:

- Backup manual;
- Backup automático;
- Restauração;
- Exportação das configurações;
- Importação das configurações.

---

# 📤 Importação e Exportação

Será possível exportar:

- Regras;
- Usuários;
- Configurações;
- Dashboard;
- Modelos de Email;
- Modelos de PDF.

Também será possível importar essas configurações em outra instalação.

---

# 🔒 Segurança

O módulo deverá registrar:

- Quem alterou uma configuração;
- Data;
- Hora;
- Valor anterior;
- Novo valor.

Nenhuma configuração crítica poderá ser alterada sem permissão administrativa.

---

# 🚀 Melhorias Futuras

O módulo poderá evoluir para incluir:

- Sincronização em nuvem;
- Perfis personalizados;
- Configuração por equipe;
- Configuração por cliente;
- Múltiplos ambientes (Desenvolvimento, Homologação e Produção);
- Integração com Active Directory;
- Configuração remota.

---

# 🔗 Dependências

Este módulo poderá fornecer configurações para todos os módulos do Assistente VIAZA.

Receberá informações de:

- Usuários;
- Administradores.

Fornecerá parâmetros para:

- Leitura Automática;
- Motor de Análise;
- Motor de Regras;
- Classificação;
- Pesquisa Automática;
- Consulta Inteligente;
- Comparador;
- WhatsApp;
- Email;
- PDF;
- Registro;
- Histórico;
- Dashboard.

---

# 📝 Observações para Desenvolvimento

As configurações deverão ser carregadas durante a inicialização do sistema e armazenadas em cache para reduzir consultas desnecessárias.

Sempre que uma configuração for alterada, o sistema deverá verificar se ela pode ser aplicada imediatamente ou se exigirá reinicialização do aplicativo.

Também deverá existir uma opção para restaurar as configurações padrão da aplicação.

---

# 💡 Central Administrativa

Além das configurações tradicionais, o Assistente VIAZA deverá possuir uma Central Administrativa.

Essa central permitirá ao administrador acompanhar:

- Status dos portais;
- Usuários conectados;
- Últimas alterações nas configurações;
- Saúde do sistema;
- Consumo de recursos;
- Erros recentes;
- Regras mais utilizadas;
- Mensagens não reconhecidas pelo Motor de Regras;
- Estatísticas de utilização.

A Central Administrativa será o principal ambiente de gerenciamento do Assistente VIAZA, reunindo todas as funções administrativas em um único local.

---

# ✅ Próximo Capítulo

➡️ **18 - Arquitetura Geral do Sistema**

No próximo documento será apresentada a arquitetura completa do Assistente VIAZA, detalhando todos os módulos, o fluxo de comunicação entre eles, as tecnologias recomendadas, os padrões de desenvolvimento e a estrutura técnica da aplicação.