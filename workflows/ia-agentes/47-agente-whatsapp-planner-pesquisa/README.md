# 🤖 Agente WhatsApp com Planner e Pesquisa

## Descrição

Fluxo que recebe mensagens via WhatsApp, utiliza um Planner AI para estruturar solicitações, pesquisa informações na web em tempo real com SerpAPI, e responde de volta via WhatsApp, mantendo memória de contexto da conversa.

## Funcionalidades

- **Recepção de mensagens via WhatsApp:** dispara o fluxo quando há uma mensagem recebida
- **Planejamento de tarefas:** usa o Planner para estruturar a solicitação recebida
- **Pesquisa em tempo real:** utiliza SerpAPI para buscar informações relevantes
- **Uso de modelos de linguagem:** emprega Groq e OpenAI para raciocínio e geração de respostas
- **Memória de contexto:** mantém memória de sessão para melhorar as respostas
- **Resposta via WhatsApp:** envia a resposta com o conteúdo planejado ao usuário

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                      |
| --------- | ------ | ------------------------------ |
| `message` | string | Mensagem recebida via WhatsApp |
| `wa_id`   | string | ID do usuário WhatsApp         |

## Como Funciona

1. **Trigger WhatsApp:** Recebe mensagem via webhook do WhatsApp
2. **Planner AI:** DeepSeek R1 estrutura e planeja a solicitação recebida
3. **Pesquisa Web:** Research Agent usa SerpAPI para buscar informações relevantes
4. **Processamento:** OpenAI GPT-4o Mini processa e organiza os resultados
5. **Memória:** Window Buffer Memory mantém contexto da conversa
6. **Resposta:** Envia resposta estruturada de volta via WhatsApp

## Configuração

### Credenciais Necessárias

- **WhatsApp Business API:** Configurado no n8n
- **SerpAPI:** API key para pesquisas na web
- **OpenAI:** API key para processamento de linguagem
- **Groq:** API key para modelo DeepSeek R1

### Estrutura de Dados

```json
{
  "messages": [
    {
      "text": {
        "body": "Mensagem do usuário"
      }
    }
  ],
  "contacts": [
    {
      "wa_id": "ID do usuário WhatsApp"
    }
  ]
}
```

## Casos de Uso

- Planejamento de viagens com pesquisa de hotéis e restaurantes
- Organização de eventos com busca de locais e serviços
- Pesquisa de informações em tempo real para tomada de decisões
- Assistente pessoal com memória de contexto
- Suporte ao cliente com informações atualizadas

## Dependências

- WhatsApp Business API configurado
- SerpAPI para pesquisas na web
- Modelos de IA (OpenAI, Groq) configurados
- Sistema de memória para contexto de conversa

## Estrutura do Workflow

1. **WhatsApp Trigger** - Recebe mensagens via webhook
2. **DeepSeek R1 Planner** - Estrutura e planeja solicitações
3. **Window Buffer Memory** - Mantém memória de contexto
4. **Research Agent** - Pesquisa e processa informações
5. **SerpAPI** - Ferramenta de pesquisa na web
6. **OpenAI Chat Model** - Processamento de linguagem
7. **WhatsApp Business Cloud** - Envia respostas

## Monitoramento

- Logs de execução do WhatsApp Trigger
- Status das chamadas de API (SerpAPI, OpenAI, Groq)
- Métricas de uso de memória de contexto
- Performance dos agentes de IA

## Tratamento de Erros

- Validação de mensagens recebidas
- Fallback para modelos de IA alternativos
- Tratamento de erros de API externas
- Logs de debugging para troubleshooting

## Configurações Avançadas

### Modelos de IA

- **Planner:** DeepSeek R1 via Groq para raciocínio estruturado
- **Research:** GPT-4o Mini via OpenAI para processamento de pesquisa
- **Memória:** Window Buffer com chave personalizada baseada no ID do usuário

### Integrações

- **WhatsApp:** Webhook para recebimento e API para envio
- **SerpAPI:** Pesquisa em tempo real na web
- **Sistema de Memória:** Buffer de janela para contexto persistente

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
