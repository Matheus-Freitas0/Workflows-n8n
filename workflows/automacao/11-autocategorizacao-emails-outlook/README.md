# ⚙️ Autocategorização de E-mails Outlook

## Descrição

Sistema inteligente que automatiza a leitura e categorização de e-mails do Outlook usando um modelo de linguagem para determinar categoria/subcategoria, atualizar rótulos e mover mensagens para pastas apropriadas de forma organizada e eficiente.

## Funcionalidades

- **Trigger:** Monitoramento automático de e-mails não categorizados no Outlook
- **Integração:** Outlook, IA para classificação, sistema de pastas e rótulos
- **Processamento:** Sanitização de conteúdo, classificação inteligente, organização automática
- **Saída:** E-mails categorizados, rotulados e movidos para pastas apropriadas

## Parâmetros de Entrada

| Parâmetro          | Tipo   | Descrição                                        |
| ------------------ | ------ | ------------------------------------------------ |
| `outlook_emails`   | array  | Lista de e-mails não categorizados do Outlook    |
| `email_content`    | object | Conteúdo do e-mail (assunto, corpo, remetente)   |
| `folder_structure` | object | Estrutura de pastas disponíveis para organização |
| `ai_model_config`  | object | Configuração do modelo de IA para classificação  |

## Como Funciona

1. **Monitoring with Filter:** Busca e processa e-mails não assinalados e sem categoria definida
2. **Batch Processing:** Itera sobre itens retornados para processar múltiplas mensagens de forma controlada
3. **Email Body Sanitization:** Converte HTML/markdown para texto limpo, removendo tags, links, imagens, tabelas e caracteres indesejados
4. **Variable Preparation:** Captura e organiza campos importantes do e-mail (assunto, remetente, corpo, ID) para uso no agente de IA
5. **AI Classification:** Envia o e-mail ao agente com instruções rígidas de saída para obter um JSON com subject, category, subCategory e análise
6. **Output Validation and Conversion:** Extrai e converte a resposta do agente em JSON com captura de erros para garantir continuidade do fluxo
7. **Category Mapping:** Rotula a mensagem com a categoria retornada pelo agente e aplica transformações (capitalização) quando necessário
8. **Folder Movement:** Move mensagens para pastas específicas (ex.: Actioned, Receipt, Junk, SaaS, Community, Business) conforme a categoria
9. **Read Verification:** Checa se o e-mail já foi lido e, se aplicável, realiza a ação de movimentação para pasta de mensagens processadas
10. **Error Handling:** Captura e registra erros do agente sem interromper o processamento de outros itens

## Configuração

### Credenciais Necessárias

- **Outlook API:** Configuração de acesso ao Outlook com permissões adequadas
- **IA Language Model:** Modelo de linguagem para classificação e categorização de e-mails
- **Folder Structure:** Configuração das pastas de destino para cada categoria
- **Label System:** Sistema de rótulos para organização dos e-mails
- **Error Logging:** Sistema para registro de erros e monitoramento

### Estrutura de Dados

```json
{
  "outlook_processing": {
    "email_id": "msg_123456",
    "subject": "Relatório Mensal de Vendas",
    "sender": "vendas@empresa.com",
    "body_content": "Conteúdo limpo do e-mail...",
    "received_date": "2025-01-15T10:30:00Z",
    "is_read": false,
    "current_category": null
  },
  "ai_classification": {
    "model_response": {
      "subject": "Relatório Mensal de Vendas",
      "category": "Business",
      "subCategory": "Reports",
      "analysis": "E-mail relacionado a relatórios de negócios",
      "confidence": 0.95
    },
    "processing_status": "success",
    "error_details": null
  },
  "folder_mapping": {
    "Business": "Business",
    "SaaS": "SaaS",
    "Community": "Community",
    "Receipt": "Receipt",
    "Junk": "Junk",
    "Actioned": "Actioned"
  },
  "email_organization": {
    "final_category": "Business",
    "applied_label": "Business_Reports",
    "destination_folder": "Business",
    "movement_status": "completed",
    "processing_timestamp": "2025-01-15T10:35:00Z"
  }
}
```

## Casos de Uso

- **Organização Automática:** Categorização automática de e-mails recebidos
- **Gestão de Pastas:** Movimentação inteligente para pastas apropriadas
- **Filtragem de Conteúdo:** Identificação automática de tipos de e-mail
- **Sanitização de Dados:** Limpeza automática de conteúdo HTML/markdown
- **Processamento em Lote:** Tratamento eficiente de múltiplos e-mails
- **Continuidade de Processamento:** Tratamento de erros sem interrupção do fluxo
- **Auditoria e Rastreamento:** Log completo de ações realizadas

## Dependências

- Acesso configurado ao Outlook com permissões adequadas
- Modelo de IA configurado para classificação de e-mails
- Estrutura de pastas definida no Outlook
- Sistema de rótulos configurado
- Capacidade de processamento de e-mails em lote
- Sistema de logging para monitoramento e debugging

## Estrutura do Workflow

1. **Outlook Email Trigger** - Monitora e-mails não categorizados
2. **Batch Processing** - Processa múltiplos e-mails de forma controlada
3. **Content Sanitization** - Limpa conteúdo HTML/markdown
4. **Variable Extraction** - Captura campos importantes do e-mail
5. **AI Classification** - Classifica e-mail usando modelo de linguagem
6. **Response Validation** - Valida e converte resposta da IA
7. **Category Mapping** - Aplica categoria e rótulos
8. **Folder Movement** - Move e-mail para pasta apropriada
9. **Read Status Check** - Verifica status de leitura
10. **Error Handling** - Captura e registra erros
11. **Processing Log** - Registra ações realizadas

## Monitoramento

- **E-mails Processados:** Total de mensagens analisadas e categorizadas
- **Taxa de Classificação:** Precisão da categorização automática
- **Tempo de Processamento:** Latência média por e-mail processado
- **Distribuição de Categorias:** Percentual de e-mails por categoria
- **Movimentações de Pasta:** Total de e-mails movidos para cada pasta
- **Erros de Processamento:** Taxa de falhas e tipos de erro
- **Performance do Modelo IA:** Tempo de resposta e qualidade das classificações

## Tratamento de Erros

- **Falha na Classificação IA:** Log de erro e processamento manual
- **E-mail Corrompido:** Notificação de erro e skip para próximo item
- **Falha na Movimentação:** Retry automático com notificação
- **Timeout de Processamento:** Cancelamento e log de erro
- **Permissões Insuficientes:** Notificação administrativa
- **Estrutura de Pasta Inválida:** Fallback para pasta padrão
- **Erro de Validação JSON:** Log de erro e processamento manual

## Características Técnicas

### Sistema de Monitoramento

- **Filtro Inteligente:** Identificação automática de e-mails não categorizados
- **Processamento em Lote:** Tratamento eficiente de múltiplas mensagens
- **Continuidade de Fluxo:** Processamento não-bloqueante em caso de erros
- **Logging Completo:** Registro detalhado de todas as operações

### Sanitização de Conteúdo

- **Remoção de HTML:** Conversão automática para texto limpo
- **Limpeza de Markdown:** Remoção de formatação desnecessária
- **Filtragem de Links:** Identificação e tratamento de URLs
- **Processamento de Imagens:** Tratamento de conteúdo visual
- **Limpeza de Tabelas:** Conversão de dados tabulares

### Classificação com IA

- **Instruções Rígidas:** Formato de saída padronizado e validado
- **Categorização Hierárquica:** Suporte a categoria e subcategoria
- **Análise Contextual:** Compreensão do conteúdo do e-mail
- **Validação de Resposta:** Verificação de integridade dos dados

### Organização Automática

- **Mapeamento de Pastas:** Associação automática categoria-pasta
- **Sistema de Rótulos:** Aplicação inteligente de tags organizacionais
- **Movimentação Inteligente:** Transferência automática para pastas apropriadas
- **Verificação de Status:** Controle de e-mails já processados

---

_Autor: Matheus Freitas_  
_Categoria: Automação_  
_Versão: 1.0_
