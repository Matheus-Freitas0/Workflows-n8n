# 🌤️ Agente de Previsão do Tempo

## Descrição

Agente de inteligência artificial especializado em previsão do tempo e informações meteorológicas. Utiliza IA para processar consultas sobre condições climáticas e fornecer respostas inteligentes.

## Funcionalidades

- **Trigger:** Mensagem de chat recebida via webhook
- **Integração:** OpenAI GPT-4 + Wikipedia + Ferramentas de Previsão
- **Processamento:** Análise inteligente de consultas meteorológicas
- **Memória:** Contexto de conversa com buffer de janela
- **Ferramentas:** Acesso a dados de previsão e informações gerais

## Como Funciona

1. **Recebimento:** Webhook recebe mensagem do usuário
2. **Análise:** Agente analisa intenção da mensagem
3. **Seleção de Ferramenta:** Escolhe entre previsão do tempo ou Wikipedia
4. **Execução:** Chama ferramenta apropriada
5. **Resposta:** Gera resposta contextual para o usuário

## Configuração

### Credenciais Necessárias

- **OpenAI API:** Credenciais configuradas no n8n
- **Webhook:** Configurado para receber mensagens de chat
- **Ferramentas:** Acesso a APIs de previsão do tempo

### Modelo de IA

- **Nome:** GPT-4o Mini
- **Provedor:** OpenAI
- **Capacidades:** Processamento de linguagem natural, análise meteorológica

### Memória

- **Tipo:** Buffer Window
- **Função:** Manter contexto da conversa

## Ferramentas Disponíveis

### 1. Previsão do Tempo

- **Função:** Acessar informações sobre condições climáticas
- **Uso:** Quando usuário solicita previsão do tempo
- **Dados:** Temperatura, umidade, condições atmosféricas

### 2. Wikipedia

- **Função:** Buscar informações gerais não relacionadas ao tempo
- **Uso:** Para consultas que não envolvem meteorologia
- **Dados:** Informações enciclopédicas sobre diversos assuntos

## Estrutura do Workflow

1. **Chat Trigger** - Recebe mensagens via webhook
2. **AI Agent** - Processa mensagens e seleciona ferramentas
3. **GPT-4o Mini** - Modelo de IA para análise
4. **Memory Buffer** - Mantém contexto da conversa
5. **Ferramentas** - Wikipedia e Previsão do Tempo

## Casos de Uso

- Consultas sobre previsão do tempo
- Informações meteorológicas em tempo real
- Busca de dados climáticos por cidade
- Respostas inteligentes sobre condições atmosféricas
- Integração com sistemas de IA conversacional

## Dependências

- Credenciais da OpenAI configuradas
- Webhook configurado para receber mensagens
- Acesso a APIs de previsão do tempo
- Integração LangChain funcionando

## Monitoramento

- Verificar execuções do workflow
- Monitorar respostas do modelo de IA
- Acompanhar uso das ferramentas
- Verificar qualidade das respostas meteorológicas

## Tratamento de Erros

- **Falha na IA:** Tratamento de erro configurado
- **API indisponível:** Fallback para respostas básicas
- **Webhook indisponível:** Log de erro registrado
- **Contexto perdido:** Solicitação de informações

## Otimizações

- **Cache:** Evitar consultas repetidas ao mesmo local
- **Contexto:** Manter histórico de consultas
- **Ferramentas:** Seleção inteligente baseada no prompt
- **Respostas:** Formatação otimizada para usuário

## Limitações

- Dependência da API OpenAI
- Custo por uso do modelo
- Latência de resposta
- Necessidade de APIs de previsão funcionais

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
