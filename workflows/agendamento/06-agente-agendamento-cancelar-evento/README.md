# 📅 Agente de Agendamento - Cancelar Evento

## Descrição

Workflow para cancelar eventos existentes através da API do Cal.com. Este workflow é executado por outro workflow pai e permite cancelar agendamentos com registro da razão.

## Funcionalidades

- **Trigger:** Executado por outro workflow
- **Integração:** Cal.com API v2
- **Processamento:** Cancelamento de eventos existentes
- **Validação:** Verificação de dados de entrada
- **Auditoria:** Registro da razão do cancelamento

## Parâmetros de Entrada

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| `bookingUid` | string | Chave única do evento a ser cancelado |
| `reason` | string | Razão para o cancelamento do evento |

## Como Funciona

1. **Recebimento:** Workflow recebe parâmetros de cancelamento
2. **Validação:** Verifica se todos os parâmetros estão presentes
3. **Request:** Envia requisição POST para Cal.com API
4. **Processamento:** API processa o cancelamento
5. **Resposta:** Retorna status da operação

## Configuração

### Credenciais Necessárias

- **Cal.com:** Credenciais de API configuradas no n8n
- **API Version:** 2024-08-13

### Estrutura da Requisição

```json
{
  "cancellationReason": "{{ reason }}"
}
```

### Endpoint da API

```
POST https://api.cal.com/v2/bookings/{bookingUid}/cancel
```

### Headers da Requisição

```
cal-api-version: 2024-08-13
Authorization: Bearer {token}
```

## Casos de Uso

- Cancelamento de reuniões
- Desmarcação de eventos
- Gestão de agenda
- Registro de motivos de cancelamento
- Auditoria de operações

## Dependências

- Credenciais do Cal.com configuradas
- API do Cal.com acessível
- Workflow pai que execute este workflow
- Dados válidos de entrada

## Estrutura do Workflow

1. **Execute Workflow Trigger** - Recebe parâmetros de entrada
2. **HTTP Request** - Envia requisição para Cal.com API

## Tratamento de Erros

- **Parâmetros inválidos:** Validação de entrada
- **API indisponível:** Tratamento de erro HTTP
- **Evento não encontrado:** Verificação de bookingUid
- **Evento já cancelado:** Verificação de status

## Monitoramento

- Verificar execuções do workflow
- Monitorar respostas da API
- Acompanhar sucesso dos cancelamentos
- Verificar logs de erro

## Validações Importantes

- **Evento existente:** Verificar se bookingUid é válido
- **Evento ativo:** Confirmar se evento não foi cancelado
- **Razão obrigatória:** Motivo do cancelamento é obrigatório
- **Permissões:** Verificar se pode cancelar o evento

## Segurança

- **Validação de entrada:** Verificação de parâmetros
- **Logs de auditoria:** Registro de todas as operações
- **Controle de acesso:** Validação de permissões
- **Rastreabilidade:** Histórico de cancelamentos

## Integração

- **Workflow Pai:** Recebe dados de cancelamento
- **Cal.com API:** Executa cancelamento
- **Sistema de Notificação:** Confirma cancelamento
- **Logs:** Registra operação para auditoria

## Notificações

Após o cancelamento bem-sucedido:

- **Participantes:** Notificação automática do cancelamento
- **Organizador:** Confirmação da operação
- **Sistema:** Registro para auditoria
- **Calendário:** Atualização automática

## Recuperação

- **Reagendamento:** Evento pode ser reagendado se necessário
- **Histórico:** Razão do cancelamento fica registrada
- **Auditoria:** Rastreabilidade completa da operação
- **Relatórios:** Inclusão em relatórios de gestão

## Performance

- **Timeout:** Configuração de timeout da API
- **Retry:** Tentativas automáticas em caso de falha
- **Rate Limiting:** Respeitar limites da API
- **Cache:** Evitar consultas desnecessárias

---
*Autor: Matheus Freitas*  
*Categoria: Agendamento*  
*Versão: 1.0*
