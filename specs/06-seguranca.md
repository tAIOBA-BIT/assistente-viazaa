# 🔒 Especificação de Segurança

> Documento: 06  
> Projeto: Assistente VIAZA  
> Versão: 1.0.0

---

# Objetivo

Este documento define todas as diretrizes de segurança do Assistente VIAZA.

O objetivo é garantir a proteção das informações da empresa, dos clientes, dos operadores e dos sistemas integrados, assegurando confidencialidade, integridade, disponibilidade e rastreabilidade durante todo o ciclo de vida da aplicação.

Todas as funcionalidades do sistema deverão seguir as regras estabelecidas neste documento.

---

# Princípios

O sistema deverá seguir os seguintes princípios:

- Confidencialidade
- Integridade
- Disponibilidade
- Rastreabilidade
- Auditoria
- Menor Privilégio (Least Privilege)
- Defesa em Profundidade (Defense in Depth)
- Segurança por Padrão (Secure by Default)

---

# Controle de Acesso

O sistema deverá possuir autenticação de usuários.

Cada usuário deverá possuir:

- Nome
- Login
- Senha
- Perfil
- Status
- Último acesso

Não será permitido compartilhamento de credenciais entre operadores.

---

# Perfis

## Operador

Permissões:

- Ler OPs
- Executar pesquisas
- Comparar tarifas
- Enviar WhatsApp
- Enviar Email
- Gerar PDF
- Consultar Histórico próprio

Restrições:

- Alterar configurações
- Excluir registros
- Gerenciar usuários

---

## Supervisor

Além das permissões do Operador:

- Consultar Dashboard da equipe
- Consultar Histórico da equipe
- Consultar indicadores

---

## Gestor

Permissões completas de consulta.

Pode visualizar:

- Todas as OPs
- Dashboard Geral
- Histórico Geral
- Relatórios

---

## Administrador

Controle total do sistema.

Pode:

- Gerenciar usuários
- Configurar integrações
- Configurar regras
- Alterar parâmetros
- Visualizar logs
- Restaurar backups

---

# Autenticação

O acesso ao sistema deverá ser realizado através de login e senha.

As senhas deverão ser armazenadas utilizando algoritmos seguros de hash.

Recomendação:

- Argon2 (preferencial)
- BCrypt (alternativa)

Jamais armazenar senhas em texto puro.

---

# Sessões

Cada sessão deverá possuir:

- Identificador único
- Usuário autenticado
- Data de criação
- Última atividade
- Tempo máximo de duração

Sessões expiradas deverão ser encerradas automaticamente.

---

# Credenciais

Todas as credenciais deverão permanecer fora do código-fonte.

Utilizar:

.env

Exemplo:

DATABASE_URL

SMTP_USER

SMTP_PASSWORD

WHATSAPP_SESSION

Jamais enviar arquivos .env ao GitHub.

---

# Comunicação

Toda comunicação deverá utilizar protocolos seguros.

HTTPS

TLS

SSL

Nunca utilizar conexões não criptografadas.

---

# Integração com Portais

Os logins utilizados para acessar:

- Wooba
- Kontrip
- Companhias Aéreas

deverão utilizar a sessão autenticada do operador.

O sistema nunca deverá armazenar:

- Senhas
- Cookies
- Tokens
- Sessões

em arquivos de log.

---

# Email

As configurações SMTP deverão permanecer protegidas.

Nunca exibir:

- usuário SMTP
- senha SMTP

na interface do sistema.

---

# WhatsApp

O envio de mensagens deverá utilizar a sessão autenticada do operador.

A sessão nunca deverá ser compartilhada entre usuários.

---

# Banco de Dados

Todos os registros deverão possuir:

- ID
- Data de criação
- Data de atualização
- Usuário responsável

Os dados deverão ser protegidos contra alterações indevidas.

---

# Logs

Os logs deverão registrar:

- Login
- Logout
- Pesquisa
- Envio de Email
- Envio de WhatsApp
- Geração de PDF
- Alterações de configuração
- Erros

Nunca registrar:

- Senhas
- Tokens
- Cookies
- Dados financeiros
- Credenciais

---

# Auditoria

Toda alteração importante deverá gerar um registro contendo:

- Usuário
- Data
- Hora
- Operação executada
- Resultado
- IP (quando disponível)

---

# Tratamento de Erros

As mensagens de erro apresentadas ao usuário deverão ser amigáveis.

Jamais exibir:

- Stack Trace
- SQL
- Caminhos internos
- Tokens
- Informações sensíveis

Todos os erros deverão ser registrados nos logs internos.

---

# Backup

O sistema deverá permitir:

- Backup manual
- Backup automático
- Restauração

Itens incluídos:

- Banco
- Histórico
- Configurações
- Regras
- Logs

---

# LGPD

O sistema deverá atender aos princípios da Lei Geral de Proteção de Dados.

Os dados pessoais deverão ser utilizados exclusivamente para execução das atividades operacionais.

O sistema deverá minimizar o armazenamento de dados pessoais.

---

# Integridade

Cada operação deverá possuir:

- Identificador único
- Data
- Hora
- Operador
- Resultado

Nenhuma informação deverá ser perdida durante o processamento.

---

# Monitoramento

O sistema deverá monitorar continuamente:

- Portais indisponíveis
- Falhas de login
- Falhas de pesquisa
- Erros no envio de Email
- Erros no WhatsApp
- Erros na geração do PDF

---

# Recuperação de Falhas

Caso um portal apresente erro:

- Registrar a falha
- Continuar pesquisando os demais portais
- Exibir alerta ao operador
- Registrar evento no Dashboard

---

# Boas Práticas

- Nunca armazenar informações sensíveis em texto puro.
- Nunca compartilhar credenciais.
- Nunca utilizar senhas padrão em ambiente de produção.
- Atualizar dependências regularmente.
- Validar todas as entradas do usuário.
- Registrar eventos críticos para auditoria.
- Restringir permissões conforme o perfil do usuário.

---

# Melhorias Futuras

- Autenticação em dois fatores (2FA)
- Single Sign-On (SSO)
- Criptografia do banco de dados
- Cofre de segredos (Secrets Manager)
- Assinatura digital dos PDFs
- Monitoramento centralizado
- Detecção automática de atividades suspeitas

---

# Conclusão

Todas as funcionalidades do Assistente VIAZA deverão seguir as diretrizes estabelecidas neste documento, garantindo um ambiente seguro, confiável e adequado para o processamento das operações da empresa.