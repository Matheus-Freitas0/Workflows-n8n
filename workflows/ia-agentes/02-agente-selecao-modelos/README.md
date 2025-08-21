# 🤖 Agente de Seleção de Modelos

## Descrição

Agente inteligente que seleciona automaticamente o melhor modelo de IA para uma tarefa específica. Utiliza uma planilha do Google com modelos disponíveis e seleciona o mais adequado baseado no prompt do usuário.

## Funcionalidades

- **Trigger:** Mensagem de chat recebida via webhook
- **Integração:** OpenRouter API + Google Sheets + LangChain
- **Processamento:** Análise inteligente de prompts para seleção de modelos
- **Saída:** Nome do modelo selecionado no formato padrão

## Como Funciona

1. **Recebimento:** Webhook recebe mensagem de chat do usuário
2. **Análise:** Agente analisa o prompt para entender a tarefa
3. **Seleção:** Consulta planilha do Google com modelos disponíveis
4. **Escolha:** Seleciona o modelo mais adequado para a tarefa
5. **Resposta:** Retorna o nome do modelo no formato padrão

## Configuração

### Credenciais Necessárias

- **OpenRouter API:** Credenciais configuradas no n8n
- **Google Sheets:** OAuth2 configurado no n8n
- **Webhook:** Configurado para receber mensagens de chat

### Modelo de IA

- **Nome:** Google Gemini 2.0 Flash
- **Provedor:** OpenRouter
- **Capacidades:** Análise de prompts, seleção inteligente

### Planilha Google Sheets

- **ID:** 1toBxA_8Cq59amJji_rwN32mV5yLaR0MBd8JTM3wTTJ8
- **Página:** Modelos_de_Destaque
- **Função:** Lista de modelos disponíveis para seleção

## Estrutura do Workflow

1. **Chat Trigger** - Recebe mensagens via webhook
2. **AI Agent** - Processa mensagens e seleciona modelo
3. **OpenRouter Chat Model** - Modelo de IA para análise
4. **Google Sheets Tool** - Acesso à planilha de modelos

## Casos de Uso

- Seleção automática de modelos de IA
- Otimização de recursos computacionais
- Recomendação inteligente de modelos
- Gestão de modelos disponíveis

## Dependências

- Credenciais do OpenRouter configuradas
- Google Sheets configurado com lista de modelos
- Webhook configurado para receber mensagens
- Integração LangChain funcionando

## Formato de Saída

O agente retorna o nome do modelo no formato:
```
qwen/qwen3-235b-a22b:free
```

## Monitoramento

- Verificar execuções do workflow
- Monitorar seleções de modelos
- Acompanhar qualidade das escolhas
- Verificar acesso à planilha

## Tratamento de Erros

- Validação de prompts de entrada
- Tratamento de falhas na planilha
- Logs de seleção de modelos
- Fallback para modelos padrão

---
*Autor: Matheus Freitas*  
*Categoria: IA e Agentes*  
*Versão: 1.0*
