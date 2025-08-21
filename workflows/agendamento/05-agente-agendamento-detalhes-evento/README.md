# 📅 Agente de Agendamento - Detalhes do Evento

## Descrição

Workflow para obter detalhes completos de um evento específico através da API do Cal.com. Este workflow é executado por outro workflow pai e retorna informações detalhadas sobre um agendamento.

## Funcionalidades

- **Trigger:** Executado por outro workflow
- **Integração:** Cal.com API v2
- **Processamento:** Consulta de detalhes de eventos
- **Validação:** Verificação de bookingUid
- **Resposta:** Dados completos do evento

## Parâmetros de Entrada

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| `bookingUid` | string | Chave única do evento a ser consultado |

## Como Funciona

1. **Recebimento:** Workflow recebe bookingUid do evento
2. **Validação:** Verifica se o parâmetro está presente
3. **Request:** Envia requisição GET para Cal.com API
4. **Processamento:** API retorna detalhes do evento
5. **Resposta:** Dados completos do agendamento

## Configuração

### Credenciais Necessárias

- **Cal.com:** Credenciais de API configuradas no n8n
- **API Version:** 2024-08-13

### Endpoint da API

```
GET https://api.cal.com/v2/bookings/{bookingUid}
```

### Headers da Requisição

```
cal-api-version: 2024-08-13
Authorization: Bearer {token}
```

## Dados Retornados

A API retorna informações completas do evento, incluindo:

- **Informações do Evento:** Nome, descrição, duração
- **Participantes:** Nome, email, timezone
- **Horário:** Data e hora de início e fim
- **Status:** Confirmação, cancelamento, etc.
- **Metadados:** Chave única, criador, etc.

## Casos de Uso

- Consulta de detalhes de reuniões
- Verificação de informações de eventos
- Confirmação de agendamentos
- Auditoria de eventos
- Suporte ao usuário

## Dependências

- Credenciais do Cal.com configuradas
- API do Cal.com acessível
- Workflow pai que execute este workflow
- BookingUid válido

## Estrutura do Workflow

1. **Execute Workflow Trigger** - Recebe bookingUid
2. **HTTP Request** - Consulta API do Cal.com

## Tratamento de Erros

- **BookingUid inválido:** Verificação de formato
- **Evento não encontrado:** Tratamento de 404
- **API indisponível:** Tratamento de erro HTTP
- **Token expirado:** Renovação de credenciais

## Monitoramento

- Verificar execuções do workflow
- Monitorar respostas da API
- Acompanhar consultas realizadas
- Verificar logs de erro

## Validações Importantes

- **Formato do UID:** Verificar estrutura do bookingUid
- **Evento existente:** Confirmar se evento ainda existe
- **Permissões:** Verificar acesso ao evento
- **Dados sensíveis:** Filtrar informações privadas se necessário

## Segurança

- **Validação de entrada:** Verificação de parâmetros
- **Controle de acesso:** Validação de permissões
- **Logs de auditoria:** Registro de consultas
- **Proteção de dados:** Filtro de informações sensíveis

## Integração

- **Workflow Pai:** Fornece bookingUid
- **Cal.com API:** Retorna dados do evento
- **Sistema de Resposta:** Formata dados para usuário
- **Logs:** Registra consulta para auditoria

## Performance

- **Cache:** Evitar consultas repetidas
- **Timeout:** Configuração de timeout da API
- **Retry:** Tentativas automáticas em caso de falha
- **Rate Limiting:** Respeitar limites da API

---
*Autor: Matheus Freitas*  
*Categoria: Agendamento*  
*Versão: 1.0*
