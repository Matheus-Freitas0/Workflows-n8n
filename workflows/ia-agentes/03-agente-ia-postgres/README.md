# 🤖 Agente de IA com PostgreSQL

## Descrição

Agente de inteligência artificial com memória persistente em PostgreSQL. Este workflow permite que o agente mantenha contexto de conversas através de armazenamento persistente no banco de dados.

## Funcionalidades

- **Trigger:** Mensagem de chat recebida via webhook
- **Integração:** OpenAI API + PostgreSQL + LangChain
- **Memória:** Armazenamento persistente de conversas
- **Processamento:** Respostas contextuais com histórico
- **Persistência:** Contexto mantido entre sessões

## Como Funciona

1. **Recebimento:** Webhook recebe mensagem de chat
2. **Processamento:** Agente analisa mensagem com contexto
3. **Memória:** Consulta histórico no PostgreSQL
4. **Geração:** Gera resposta baseada no contexto completo
5. **Armazenamento:** Salva nova interação no banco

## Configuração

### Credenciais Necessárias

- **OpenAI API:** Credenciais configuradas no n8n
- **PostgreSQL:** Conexão configurada no n8n
- **Webhook:** Configurado para receber mensagens de chat

### Modelo de IA

- **Nome:** GPT-4o Mini
- **Provedor:** OpenAI
- **Capacidades:** Processamento de linguagem natural, contexto

### Banco de Dados

- **Tipo:** PostgreSQL
- **Função:** Armazenamento de memória de conversas
- **Integração:** LangChain Memory Postgres

## Estrutura do Workflow

1. **Chat Trigger** - Recebe mensagens via webhook
2. **AI Agent** - Processa mensagens com contexto
3. **OpenAI Chat Model** - Modelo de IA para geração
4. **Postgres Chat Memory** - Armazenamento persistente

## Casos de Uso

- Chatbots com memória persistente
- Assistentes virtuais com contexto
- Suporte ao cliente com histórico
- Conversas contínuas e inteligentes
- Aplicações que precisam de memória

## Dependências

- Credenciais da OpenAI configuradas
- Conexão PostgreSQL funcionando
- Webhook configurado para receber mensagens
- Integração LangChain configurada

## Recursos Avançados

- **Memória Persistente:** Contexto mantido no banco
- **Histórico de Conversas:** Acesso a interações anteriores
- **Contexto Inteligente:** Respostas baseadas em histórico
- **Escalabilidade:** Suporte a múltiplos usuários

## Configuração do Webhook

- **ID:** a3b53ca8-fb08-4c7d-a69c-d5cae418e12c
- **Método:** POST
- **Formato:** Mensagens de chat
- **Segurança:** Configurar conforme necessário

## Monitoramento

- Verificar execuções do workflow
- Monitorar respostas do modelo de IA
- Acompanhar uso da memória PostgreSQL
- Verificar qualidade das respostas contextuais

## Tratamento de Erros

- **Falha na IA:** Tratamento de erro configurado
- **Problemas no PostgreSQL:** Retry automático
- **Webhook indisponível:** Log de erro registrado
- **Contexto perdido:** Fallback para memória local

## Otimizações

- **Cache de Memória:** Otimizar consultas ao banco
- **Limpeza de Contexto:** Remover conversas antigas
- **Compressão:** Otimizar armazenamento de dados
- **Índices:** Melhorar performance das consultas

## Limitações

- Dependência da API OpenAI
- Custo por uso do modelo
- Latência de resposta
- Necessidade de PostgreSQL

---
*Autor: Matheus Freitas*  
*Categoria: IA e Agentes*  
*Versão: 1.0*
