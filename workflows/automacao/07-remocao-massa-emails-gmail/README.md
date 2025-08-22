# 🗑️ Remoção em Massa de E-mails do Gmail

## Descrição

Sistema automatizado que busca IDs de mensagens do Gmail com uma consulta específica e as exclui em lotes, permitindo limpeza eficiente da caixa de entrada.

## Funcionalidades

- **Trigger:** Execução manual para iniciar o fluxo
- **Integração:** Gmail API, processamento em lotes
- **Processamento:** Busca inteligente e remoção em massa
- **Saída:** Caixa de entrada limpa com emails removidos

## Parâmetros de Entrada

| Parâmetro    | Tipo    | Descrição                                        |
| ------------ | ------- | ------------------------------------------------ |
| `query`      | string  | Consulta de busca para filtrar emails            |
| `batch_size` | number  | Tamanho do lote para processamento (padrão: 100) |
| `dry_run`    | boolean | Modo de teste sem remoção efetiva                |

## Como Funciona

1. **Gatilho Manual:** Inicia o fluxo ao executar manualmente
2. **Busca de Mensagens:** Pesquisa todas as mensagens do Gmail usando a query `"-in:chats unsubscribe -license -key -password"` e retorna apenas IDs
3. **Processamento em Lotes:** Divide a lista de IDs em lotes de 100 para evitar sobrecarga e controlar o ritmo de execução
4. **Exclusão de Mensagens:** Exclui cada mensagem identificada usando seu ID
5. **Iteração:** Processa iterando pelos lotes até concluir todas as remoções

## Configuração

### Credenciais Necessárias

- **Gmail API:** Credenciais OAuth2 configuradas
- **Permissões:** Acesso de leitura e exclusão de emails
- **Escopo:** `https://www.googleapis.com/auth/gmail.modify`

### Estrutura de Dados

```json
{
  "search_query": "-in:chats unsubscribe -license -key -password",
  "batch_config": {
    "size": 100,
    "delay": 1000,
    "max_retries": 3
  },
  "email_processing": {
    "total_found": 0,
    "processed": 0,
    "deleted": 0,
    "errors": 0
  },
  "query_filters": {
    "exclude_chats": true,
    "exclude_unsubscribe": true,
    "exclude_license": true,
    "exclude_key": true,
    "exclude_password": true
  }
}
```

## Casos de Uso

- **Limpeza de Caixa de Entrada:** Remoção de emails antigos e irrelevantes
- **Gestão de Spam:** Eliminação de emails não desejados em massa
- **Organização:** Limpeza de emails de marketing e notificações
- **Manutenção:** Remoção de emails com palavras-chave específicas
- **Compliance:** Limpeza de emails sensíveis (licenças, chaves, senhas)

## Dependências

- Conta Gmail configurada com API habilitada
- Credenciais OAuth2 com permissões adequadas
- Conexão estável com internet
- Limite de API do Gmail respeitado

## Estrutura do Workflow

1. **Manual Trigger** - Inicia o fluxo de limpeza
2. **Gmail Search** - Busca emails usando query específica
3. **ID Extraction** - Extrai apenas IDs das mensagens encontradas
4. **Batch Processing** - Divide IDs em lotes de 100
5. **Email Deletion** - Remove emails em lotes
6. **Progress Tracking** - Acompanha progresso da operação
7. **Error Handling** - Trata erros e falhas
8. **Completion** - Finaliza processo de limpeza

## Monitoramento

- **Emails Encontrados:** Total de mensagens que atendem aos critérios
- **Lotes Processados:** Contagem de lotes processados
- **Emails Removidos:** Total de mensagens excluídas com sucesso
- **Taxa de Sucesso:** Percentual de remoções bem-sucedidas
- **Tempo de Processamento:** Duração total da operação
- **Erros:** Contagem e tipos de erros encontrados

## Tratamento de Erros

- **API Rate Limit:** Pausas automáticas entre lotes
- **Falha de Conexão:** Retry com backoff exponencial
- **Permissões Insuficientes:** Notificação de erro de acesso
- **Email Não Encontrado:** Ignora e continua processamento
- **Timeout:** Cancelamento de operações longas
- **Validação:** Verificação de dados antes da exclusão

## Características Técnicas

### Sistema de Busca

- **Query Padrão:** `"-in:chats unsubscribe -license -key -password"`
- **Filtros:** Exclusão de chats e emails com palavras específicas
- **Flexibilidade:** Query configurável conforme necessidade
- **Eficiência:** Busca otimizada para performance

### Processamento em Lotes

- **Tamanho do Lote:** 100 emails por vez (configurável)
- **Controle de Ritmo:** Pausas entre lotes para evitar sobrecarga
- **Escalabilidade:** Processa grandes volumes de emails
- **Monitoramento:** Acompanhamento em tempo real do progresso

### Gerenciamento de API

- **Rate Limiting:** Respeita limites da API do Gmail
- **Retry Logic:** Tentativas automáticas em caso de falha
- **Backoff Exponencial:** Aumenta intervalo entre tentativas
- **Quota Management:** Controle de uso da cota da API

### Segurança e Controle

- **Validação:** Verificação de permissões antes da execução
- **Dry Run:** Modo de teste sem remoção efetiva
- **Logs:** Auditoria completa de todas as operações
- **Rollback:** Possibilidade de desfazer operações (se configurado)

### Configurações Avançadas

- **Filtros Personalizados:** Adição/remoção de critérios de busca
- **Tamanho de Lote:** Ajuste conforme capacidade do sistema
- **Delays:** Configuração de pausas entre operações
- **Notificações:** Alertas sobre progresso e conclusão

---

_Autor: Matheus Freitas_  
_Categoria: Automação_  
_Versão: 1.0_
