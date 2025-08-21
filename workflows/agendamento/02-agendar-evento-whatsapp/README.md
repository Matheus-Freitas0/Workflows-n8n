# 📱 Agendar Evento WhatsApp

## Descrição

Workflow para agendamento de eventos via WhatsApp através da API do Cal.com. Similar ao workflow de agendamento padrão, mas específico para integração com WhatsApp.

## Funcionalidades

- **Trigger:** Executado por outro workflow
- **Integração:** Cal.com API v2
- **Fuso Horário:** America/Sao_Paulo
- **Processamento:** Recebe dados de agendamento e cria eventos na plataforma
- **Especialização:** Otimizado para fluxos de WhatsApp

## Parâmetros de Entrada

| Parâmetro | Tipo | Descrição |
|-----------|------|-----------|
| `name` | string | Nome do participante |
| `email` | string | Email do participante |
| `eventTypeId` | number | ID do tipo de evento no Cal.com |
| `dateTime` | string | Data e hora do evento |

## Como Funciona

1. **Recebimento de Dados:** Workflow recebe parâmetros de agendamento
2. **Ajuste JSON:** Formata os dados para o formato esperado pela API
3. **Request de Agendamento:** Envia requisição POST para Cal.com API
4. **Criação do Evento:** Evento é criado automaticamente na plataforma

## Configuração

### Credenciais Necessárias

- **Cal.com:** Credenciais de API configuradas no n8n
- **API Version:** 2024-08-13

### Estrutura da Requisição

```json
{
  "start": "{{ dateTime }}",
  "attendee": {
    "name": "{{ name }}",
    "email": "{{ email }}",
    "timeZone": "America/Sao_Paulo"
  },
  "eventTypeId": {{ eventTypeId }}
}
```

## Casos de Uso

- Agendamento via WhatsApp Business
- Integração com chatbots de WhatsApp
- Automação de agendamentos por mensagem
- Fluxos de atendimento automatizado

## Dependências

- Credenciais do Cal.com configuradas
- API do Cal.com acessível
- Workflow pai que execute este workflow
- Integração com sistema de WhatsApp

## Estrutura do Workflow

1. **Execute Workflow Trigger** - Recebe parâmetros de entrada
2. **Set (Ajuste JSON)** - Formata dados para API
3. **HTTP Request** - Envia requisição para Cal.com

## Diferenças do Workflow Padrão

- Otimizado para fluxos de WhatsApp
- Estrutura similar mas com foco em mensagens
- Integração com sistemas de mensageria

## Tratamento de Erros

- Validação de parâmetros de entrada
- Tratamento de respostas da API
- Logs de execução para debugging
- Tratamento específico para WhatsApp

## Monitoramento

- Verificar logs de execução
- Monitorar respostas da API
- Acompanhar criação de eventos
- Monitorar fluxos de WhatsApp

## Integração WhatsApp

- Recebe dados de mensagens do WhatsApp
- Processa informações de contato
- Cria agendamentos automaticamente
- Confirma agendamento via mensagem

---
*Autor: Matheus Freitas*  
*Categoria: Agendamento*  
*Versão: 1.0*
