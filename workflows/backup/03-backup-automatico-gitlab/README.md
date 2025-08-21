# 💾 Backup Automático para GitLab

## Descrição

Workflow automatizado que exporta periodicamente e por execução manual os workflows e credenciais para um repositório Git, garantindo cópias versionadas e enviadas ao remoto. O sistema executa backups automáticos em horários programados e permite execuções manuais quando necessário.

## Funcionalidades

- **Agendamento de Backups:** Executa o processo automaticamente em 00:00 e 06:00
- **Backup Manual:** Permite iniciar a exportação e envio manualmente através de um gatilho
- **Exportação de Workflows:** Gera arquivos de backup dos workflows em uma pasta do repositório (repo/workflows/)
- **Exportação de Credenciais:** Gera arquivos de backup das credenciais em uma pasta do repositório (repo/credentials/)
- **Versionamento e Envio:** Adiciona as alterações, realiza commit com mensagem contendo timestamp ISO e faz push para o repositório remoto

## Parâmetros de Entrada

| Parâmetro           | Tipo   | Descrição                                    |
| ------------------- | ------ | -------------------------------------------- |
| `git_repository`   | string | URL do repositório GitLab para backup        |
| `git_branch`       | string | Branch do repositório (padrão: main)         |
| `backup_path`      | string | Caminho local para armazenamento temporário  |
| `schedule_times`   | array  | Horários para execução automática            |

## Como Funciona

### 1. **Agendamento Automático**
- **00:00:** Execução automática do backup
- **06:00:** Execução automática do backup
- **12:00 e 18:00:** Execuções adicionais programadas

### 2. **Processo de Backup**
- Exporta todos os workflows ativos do n8n
- Exporta todas as credenciais configuradas
- Organiza arquivos em estrutura de pastas local

### 3. **Versionamento Git**
- Adiciona alterações ao repositório local
- Cria commit com timestamp ISO da execução
- Envia alterações para o repositório remoto

### 4. **Backup Manual**
- Gatilho disponível para execução sob demanda
- Mesmo processo de exportação e versionamento
- Útil para backups antes de mudanças importantes

## Configuração

### Credenciais Necessárias

- **GitLab:** Token de acesso pessoal ou credenciais SSH
- **n8n:** Acesso aos workflows e credenciais do sistema
- **Sistema:** Permissões de escrita no diretório de backup

### Estrutura do Repositório

```
repo/
├── workflows/
│   ├── workflow1.json
│   ├── workflow2.json
│   └── ...
├── credentials/
│   ├── credential1.json
│   ├── credential2.json
│   └── ...
└── README.md
```

### Configurações de Agendamento

```json
{
  "schedule": {
    "00:00": "Backup diário matinal",
    "06:00": "Backup diário vespertino",
    "12:00": "Backup adicional",
    "18:00": "Backup adicional"
  },
  "manual_trigger": true,
  "retention_days": 30
}
```

## Casos de Uso

- **Backup Regular:** Proteção contra perda de configurações
- **Versionamento:** Controle de mudanças nos workflows
- **Recuperação:** Restauração de configurações anteriores
- **Auditoria:** Histórico de alterações para compliance
- **Migração:** Transferência de configurações entre ambientes

## Dependências

- Repositório GitLab configurado e acessível
- Credenciais de acesso ao GitLab válidas
- Permissões de escrita no diretório de backup
- n8n configurado com workflows e credenciais
- Acesso à API do n8n para exportação

## Estrutura do Workflow

### Nós Principais
1. **Schedule Trigger** - Execução periódica automática
2. **Manual Trigger** - Execução manual sob demanda
3. **n8n API** - Exportação de workflows
4. **n8n API** - Exportação de credenciais
5. **File System** - Organização de arquivos
6. **Git Operations** - Adição, commit e push
7. **Error Handling** - Tratamento de falhas

### Fluxo de Execução
```
Trigger → Export Workflows → Export Credentials → Organize Files → Git Add → Git Commit → Git Push → Success/Error
```

## Monitoramento

- **Logs de Execução:** Acompanhar sucessos e falhas via n8n
- **Histórico Git:** Verificar commits e alterações no repositório
- **Status de Backup:** Monitorar execuções agendadas
- **Tamanho dos Backups:** Acompanhar crescimento do repositório
- **Tempo de Execução:** Métricas de performance do processo

## Tratamento de Erros

- **Falhas de API:** Retry automático com backoff exponencial
- **Problemas de Git:** Rollback em caso de falha no push
- **Falhas de Sistema:** Notificação de erros críticos
- **Conflitos de Merge:** Resolução automática quando possível
- **Timeout de Rede:** Tratamento de conexões lentas

## Implementação Técnica

- **Processamento Assíncrono:** Execução não-bloqueante
- **Cache de Dados:** Evita reprocessamento desnecessário
- **Validação de Arquivos:** Verificação de integridade antes do commit
- **Logs Estruturados:** Rastreamento detalhado de execuções
- **Compressão:** Otimização de tamanho dos arquivos de backup

## Personalização

- **Frequência de Backup:** Horários configuráveis
- **Retenção de Dados:** Política de limpeza de backups antigos
- **Filtros de Conteúdo:** Seleção específica de workflows/credenciais
- **Notificações:** Alertas por email, Slack ou Telegram
- **Backup Incremental:** Apenas alterações desde último backup

## Segurança e Compliance

- **Criptografia:** Proteção de credenciais sensíveis
- **Logs de Auditoria:** Rastreamento de todas as operações
- **Controle de Acesso:** Permissões baseadas em roles
- **Conformidade GDPR:** Tratamento adequado de dados pessoais
- **Backup Offsite:** Cópia em localização remota

## Manutenção

- **Limpeza Automática:** Remoção de backups antigos
- **Verificação de Integridade:** Validação periódica dos arquivos
- **Atualização de Dependências:** Manutenção das bibliotecas Git
- **Monitoramento de Espaço:** Controle do uso de disco
- **Backup do Sistema:** Proteção do próprio workflow de backup

---

_Autor: Matheus Freitas_  
_Categoria: Backup_  
_Versão: 1.0_
