# 📅 Agente de Agendamento - Reagendamento

## Descrição

Workflow para reagendar eventos existentes através da API do Cal.com. Este workflow é executado por outro workflow pai e permite alterar a data/hora de eventos já agendados.

## Funcionalidades

- **Trigger:** Executado por outro workflow
- **Integração:** Cal.com API v2
- **Processamento:** Reagendamento de eventos existentes
- **Validação:** Verificação de dados de entrada
- **Confirmação:** Resposta de sucesso ou erro

## Parâmetros de Entrada

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| `start` | string | Nova data/hora do evento (formato ISO 8601) |
| `reason` | string | Razão para o reagendamento |
| `bookingUid` | string | Chave única do evento a ser reagendado |

## Como Funciona

1. **Recebimento:** Workflow recebe parâmetros de reagendamento
2. **Validação:** Verifica se todos os parâmetros estão presentes
3. **Request:** Envia requisição POST para Cal.com API
4. **Processamento:** API processa o reagendamento
5. **Resposta:** Retorna status da operação

## Configuração

### Credenciais Necessárias

- **Cal.com:** Credenciais de API configuradas no n8n
- **API Version:** 2024-08-13

### Estrutura da Requisição

```json
{
  "start": "{{ start }}",
  "reschedulingReason": "{{ reason }}"
}
```

### Endpoint da API

```
POST https://api.cal.com/v2/bookings/{bookingUid}/reschedule
```

## Casos de Uso

- Reagendamento de reuniões
- Alteração de horários de eventos
- Flexibilidade para participantes
- Gestão de conflitos de agenda

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
- **Conflito de horário:** Validação de disponibilidade

## Monitoramento

- Verificar execuções do workflow
- Monitorar respostas da API
- Acompanhar sucesso dos reagendamentos
- Verificar logs de erro

## Validações Importantes

- **Data futura:** Verificar se nova data é posterior à atual
- **Formato ISO:** Garantir formato correto da data
- **Razão obrigatória:** Motivo do reagendamento é obrigatório
- **Evento existente:** Verificar se bookingUid é válido

## Segurança

- **Validação de entrada:** Verificação de parâmetros
- **Logs de auditoria:** Registro de todas as operações
- **Controle de acesso:** Validação de permissões
- **Rastreabilidade:** Histórico de alterações

## Integração

- **Workflow Pai:** Recebe dados de agendamento
- **Cal.com API:** Executa reagendamento
- **Sistema de Notificação:** Confirma alteração
- **Logs:** Registra operação para auditoria

---
*Autor: Matheus Freitas*  
*Categoria: Agendamento*  
*Versão: 1.0*
