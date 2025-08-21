# 💾 Backup Workflow Google Drive

## Descrição

Sistema automatizado para backup de workflows n8n no Google Drive. Cria cópias de segurança organizadas por data para garantir recuperação em caso de falhas.

## Funcionalidades

- **Trigger:** Execução manual ou agendada
- **Integração:** n8n API + Google Drive
- **Processamento:** Backup automático de todos os workflows
- **Organização:** Estrutura de pastas por data
- **Segurança:** Cópias de segurança estruturadas

## Como Funciona

1. **Inicialização:** Cria pasta de backup com data atual
2. **Coleta:** Obtém todos os workflows da instância n8n
3. **Processamento:** Converte cada workflow para formato JSON
4. **Upload:** Salva arquivos no Google Drive organizadamente
5. **Confirmação:** Registra sucesso da operação

## Configuração

### Credenciais Necessárias

- **Google Drive OAuth2:** Configurado para acesso
- **n8n API:** Credenciais para acesso aos workflows
- **Pasta de Destino:** Configurada no Google Drive

### Estrutura de Backup

- **Pasta Raiz:** "Backups Workflows"
- **Subpastas:** Por data (ex: "Backup dia 27/01/2025")
- **Arquivos:** Cada workflow como arquivo JSON separado

## Estrutura do Workflow

1. **Manual Trigger** - Inicia processo de backup
2. **Google Drive** - Cria pasta com data atual
3. **n8n API** - Obtém todos os workflows
4. **Processamento** - Converte para arquivos JSON
5. **Upload** - Salva no Google Drive

## Casos de Uso

- Backup regular de workflows
- Recuperação após falhas
- Migração entre instâncias
- Versionamento de configurações
- Auditoria de mudanças

## Dependências

- Google Drive configurado
- n8n API funcionando
- Pasta de destino criada
- Permissões adequadas

## Monitoramento

- Verificar execuções do backup
- Monitorar criação de pastas
- Acompanhar upload de arquivos
- Verificar integridade dos backups

## Tratamento de Erros

- **API indisponível:** Retry automático
- **Permissões:** Verificação de acesso
- **Espaço insuficiente:** Notificação de erro
- **Falha no upload:** Log de erro detalhado

---
*Autor: Matheus Freitas*  
*Categoria: Backup*  
*Versão: 1.0*
