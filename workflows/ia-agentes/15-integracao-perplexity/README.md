# 🔍 Integração com Perplexity

## Descrição

Workflow de integração com a API Perplexity para pesquisa e busca de informações em tempo real. Este sistema combina um agente de IA com a capacidade de pesquisa da Perplexity para fornecer respostas baseadas em informações atualizadas.

## Funcionalidades

- **Trigger:** Chat message received, Manual execution
- **Integração:** OpenAI GPT-4.1-mini, Perplexity API, LangChain Agent
- **Processamento:** Pesquisa inteligente com IA
- **Saída:** Respostas baseadas em pesquisa em tempo real

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                    |
| --------- | ------ | ---------------------------- |
| `message` | string | Mensagem/pergunta do usuário |

## Como Funciona

1. **Recebimento:** Mensagem é recebida via chat ou execução manual
2. **Processamento:** Agente de IA processa a pergunta
3. **Pesquisa:** Perplexity API busca informações atualizadas
4. **Síntese:** IA combina pesquisa com conhecimento para resposta final
5. **Saída:** Resposta completa é fornecida ao usuário

## Configuração

### Credenciais Necessárias

- **OpenAI API:** Chave de API configurada no n8n
- **Perplexity API:** Chave de API configurada no n8n
- **LangChain Agent:** Configuração do agente para pesquisa

### Estrutura de Dados

```json
{
  "message": "Pergunta ou solicitação do usuário"
}
```

## Casos de Uso

- Pesquisa de informações atualizadas
- Assistente de pesquisa inteligente
- Sistema de Q&A baseado em dados recentes
- Análise de informações em tempo real

## Dependências

- Credenciais OpenAI configuradas
- Credenciais Perplexity configuradas
- Agente LangChain configurado
- Webhook configurado para chat

## Estrutura do Workflow

1. **Chat Trigger** - Recebe mensagens de chat
2. **AI Agent** - Processa e coordena a pesquisa
3. **OpenAI Chat Model** - Modelo de linguagem GPT-4.1-mini
4. **Perplexity Tool** - API de pesquisa em tempo real
5. **Manual Trigger** - Execução manual para testes

## Monitoramento

- Verificar execuções através do histórico do n8n
- Monitorar uso das APIs OpenAI e Perplexity
- Acompanhar qualidade das respostas geradas

## Tratamento de Erros

- Validação das mensagens recebidas
- Tratamento de falhas nas APIs
- Logs de execução para debugging
- Fallback para respostas sem pesquisa

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
