# 📱 Agente WhatsApp Agendamento

## Descrição

Agente de agendamento integrado com WhatsApp para processar mensagens e facilitar o agendamento de eventos. Este workflow combina funcionalidades de WhatsApp com automação de agendamentos.

## Funcionalidades

- **Trigger:** Webhook do WhatsApp
- **Integração:** WhatsApp API + Processamento de mensagens
- **Validação:** Apenas números autorizados (contém "0404")
- **Processamento:** Extração e análise de mensagens
- **Automação:** Processamento automático de solicitações

## Como Funciona

1. **Recebimento:** Webhook recebe mensagens do WhatsApp
2. **Validação:** Verifica se número está autorizado
3. **Processamento:** Extrai dados da mensagem (remetente, instância, conteúdo)
4. **Análise:** Processa mensagem para identificar intenção
5. **Resposta:** Gera resposta automática ou executa ação

## Configuração

### Credenciais Necessárias

- **WhatsApp Webhook:** Configurado para receber mensagens
- **Webhook ID:** 3ec579ac-f686-4536-8615-efffad6517d5

### Validação de Números

- **Autorizados:** Números que contêm "0404"
- **Bloqueados:** Outros números são ignorados
- **Segurança:** Controle de acesso por número

## Estrutura do Workflow

1. **Webhook** - Recebe mensagens do WhatsApp
2. **Extraindo Dados** - Mapeia campos da mensagem
3. **Validação** - Verifica autorização do número
4. **Processamento** - Analisa e processa mensagem

## Dados Processados

| Campo         | Descrição             | Fonte          |
| ------------- | --------------------- | -------------- |
| **From**      | Número do remetente   | `remoteJid`    |
| **Instance**  | Instância do WhatsApp | `instance`     |
| **Message**   | Conteúdo da mensagem  | `conversation` |
| **MessageId** | ID único da mensagem  | `key.id`       |
| **Name**      | Nome do contato       | `pushName`     |

## Casos de Uso

- Agendamento de eventos via WhatsApp
- Atendimento automatizado para agendamentos
- Processamento de mensagens de agendamento
- Integração WhatsApp com sistemas de agenda
- Suporte ao cliente para marcações

## Dependências

- Webhook do WhatsApp configurado
- Números autorizados configurados
- Acesso à API do WhatsApp
- Sistema de processamento de mensagens

## Monitoramento

- Verificar execuções do workflow
- Monitorar mensagens recebidas
- Acompanhar validações de números
- Verificar processamento de mensagens

## Tratamento de Erros

- **Números não autorizados:** Ignorados automaticamente
- **Mensagens inválidas:** Log de erro registrado
- **Falha no processamento:** Tratamento de erro configurado
- **Webhook indisponível:** Retry automático

## Segurança

- **Validação de números:** Apenas números autorizados
- **Controle de acesso:** Baseado em padrão específico
- **Logs de auditoria:** Todas as mensagens registradas
- **Isolamento:** Processamento separado por instância

## Otimizações

- **Cache:** Evitar reprocessamento de mensagens
- **Rate Limiting:** Respeitar limites do WhatsApp
- **Paralelização:** Processar múltiplas mensagens
- **Filtros:** Configurar tipos de mensagem aceitos

## Integração

- **WhatsApp:** Recebe mensagens dos usuários
- **Sistema de Agendamento:** Processa solicitações
- **IA:** Analisa intenção das mensagens
- **Notificações:** Confirma agendamentos

---

_Autor: Matheus Freitas_  
_Categoria: WhatsApp_  
_Versão: 1.0_
