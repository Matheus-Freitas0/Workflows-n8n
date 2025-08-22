# ⚙️ Assistente de E-mail IA para Outlook

## Descrição

Sistema inteligente que automatiza a classificação e priorização de e-mails do Outlook usando modelos de IA e dados de contato/regras de um CRM, atualizando categorias e importância conforme necessário para otimizar o fluxo de trabalho.

## Funcionalidades

- **Trigger:** Monitoramento automático de e-mails no Outlook
- **Integração:** Outlook API, IA para classificação, CRM (Monday.com), base de contatos
- **Processamento:** Classificação inteligente e priorização automática
- **Saída:** E-mails categorizados e priorizados automaticamente

## Parâmetros de Entrada

| Parâmetro      | Tipo   | Descrição                           |
| -------------- | ------ | ----------------------------------- |
| `email_data`   | object | Dados do e-mail recebido do Outlook |
| `sender_info`  | object | Informações do remetente            |
| `content_data` | object | Conteúdo e metadados do e-mail      |

## Como Funciona

1. **Monitor de E-mails:** Busca e processa mensagens do Outlook aplicando filtros para ignorar itens sinalizados ou já categorizados
2. **Sanitização do Corpo:** Converte HTML para texto/markdown e limpa conteúdo irrelevante antes da análise
3. **Integração de Contatos:** Sincroniza e consulta contatos originados do Monday.com e armazena/atualiza em uma base de contatos
4. **Carregamento de Regras:** Obtém listas de categorias e regras de exclusão de uma base para orientar a classificação
5. **Classificação por IA:** Envia o conteúdo do e-mail e contexto de contatos/regras a um modelo de linguagem para determinar categoria
6. **Validação de Saída:** Garante que a resposta da IA esteja em JSON válido e extrai informações necessárias
7. **Aplicação de Ações:** Atualiza a categoria e a prioridade (importância) do e-mail no Outlook com base no resultado da IA
8. **Processamento em Lote:** Processa mensagens em lotes e verifica e-mails periodicamente
9. **Agendamento:** Possui gatilhos para verificar e-mails periodicamente e para atualizar a lista de contatos

## Configuração

### Credenciais Necessárias

- **Outlook API:** Credenciais OAuth2 para acesso a e-mails
- **Monday.com API:** Acesso para sincronização de contatos
- **IA Model:** Modelo de linguagem configurado para classificação
- **Database:** Sistema de armazenamento para regras e contatos

### Estrutura de Dados

```json
{
  "email_processing": {
    "outlook_filters": {
      "exclude_flagged": true,
      "exclude_categorized": true,
      "process_new_only": true
    },
    "sanitization": {
      "convert_html": true,
      "remove_irrelevant": true,
      "clean_content": true
    }
  },
  "classification_rules": {
    "categories": ["Trabalho", "Pessoal", "Comercial", "Suporte", "Newsletter"],
    "exclusion_rules": ["unsubscribe", "license", "key", "password"]
  },
  "ai_classification": {
    "model": "gpt-4",
    "temperature": 0.3,
    "output_format": "json",
    "validation_required": true
  },
  "contact_integration": {
    "monday_sync": true,
    "contact_database": "local_storage",
    "auto_update": true
  }
}
```

## Casos de Uso

- **Gestão Automática de E-mails:** Classificação inteligente para organização eficiente
- **Priorização Inteligente:** Identificação automática de e-mails importantes
- **Integração CRM:** Sincronização de contatos e regras de negócio
- **Produtividade:** Redução de tempo gasto em organização manual
- **Compliance:** Aplicação consistente de regras organizacionais
- **Escalabilidade:** Processamento de grandes volumes de e-mails

## Dependências

- Conta Outlook com API habilitada
- Credenciais OAuth2 com permissões adequadas
- Acesso ao Monday.com para sincronização de contatos
- Modelo de IA configurado para classificação de texto
- Base de dados para armazenamento de regras e contatos
- Sistema de agendamento para execução periódica

## Estrutura do Workflow

1. **Email Monitor** - Busca e filtra e-mails no Outlook
2. **Content Sanitization** - Limpa e converte conteúdo HTML
3. **Contact Sync** - Integra contatos do Monday.com
4. **Rules Loading** - Carrega categorias e regras de exclusão
5. **AI Classification** - Classifica e-mail usando IA
6. **Output Validation** - Valida resposta da IA em JSON
7. **Email Update** - Aplica categoria e prioridade no Outlook
8. **Batch Processing** - Processa múltiplos e-mails
9. **Scheduled Triggers** - Execução periódica automática

## Monitoramento

- **E-mails Processados:** Total de mensagens classificadas
- **Taxa de Classificação:** Percentual de e-mails categorizados com sucesso
- **Precisão da IA:** Qualidade das classificações automáticas
- **Tempo de Processamento:** Latência média por e-mail
- **Sincronização de Contatos:** Status da integração com CRM
- **Erros de Validação:** Falhas na validação de saída da IA

## Tratamento de Erros

- **API Rate Limit:** Pausas automáticas entre lotes de processamento
- **Falha de Conexão:** Retry com backoff exponencial
- **Resposta IA Inválida:** Validação e correção de formato JSON
- **Permissões Insuficientes:** Notificação de erro de acesso
- **E-mail Não Encontrado:** Ignora e continua processamento
- **Timeout:** Cancelamento de operações longas

## Características Técnicas

### Sistema de Classificação

- **Filtros Inteligentes:** Exclusão automática de e-mails já processados
- **Sanitização Avançada:** Limpeza eficiente de conteúdo HTML
- **Regras Flexíveis:** Sistema configurável de categorias e exclusões
- **Validação Rigorosa:** Verificação de formato de saída da IA

### Integração CRM

- **Sincronização Monday.com:** Importação automática de contatos
- **Base de Contatos Local:** Armazenamento eficiente para consultas rápidas
- **Atualização Incremental:** Sincronização apenas de mudanças
- **Mapeamento Inteligente:** Correspondência entre contatos e e-mails

### Processamento de IA

- **Modelo Especializado:** IA treinada para classificação de e-mails
- **Contexto Rico:** Inclusão de dados de contatos e regras
- **Saída Estruturada:** Resposta em formato JSON validado
- **Temperatura Baixa:** Configuração para respostas consistentes

### Automação e Agendamento

- **Execução Periódica:** Verificação automática em intervalos configuráveis
- **Processamento em Lote:** Eficiência no tratamento de múltiplos e-mails
- **Gatilhos Flexíveis:** Diferentes tipos de acionamento automático
- **Recuperação de Falhas:** Sistema robusto de retry e recuperação

---

_Autor: Matheus Freitas_  
_Categoria: Automação_  
_Versão: 1.0_
