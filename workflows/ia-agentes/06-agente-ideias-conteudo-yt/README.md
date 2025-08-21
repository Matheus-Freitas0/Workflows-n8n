# 🎥 Agente de Ideias de Conteúdo YT

## Descrição

Agente de inteligência artificial especializado em criar ideias de conteúdo para YouTube. Este workflow coordena múltiplos agentes especializados para gerar conteúdo completo incluindo pesquisa, títulos, thumbnails e roteiros.

## Funcionalidades

- **Trigger:** Mensagem do Telegram
- **Integração:** OpenAI GPT-4 + Múltiplos Agentes Especializados
- **Processamento:** Criação completa de ideias de conteúdo
- **Coordenação:** Orquestração de agentes especializados
- **Saída:** Conteúdo estruturado para YouTube

## Como Funciona

1. **Recebimento:** Bot do Telegram recebe solicitação do usuário
2. **Análise:** Agente principal analisa o assunto solicitado
3. **Coordenação:** Executa agentes especializados em sequência
4. **Consolidação:** Reúne todas as informações geradas
5. **Resposta:** Envia conteúdo completo via Telegram

## Configuração

### Credenciais Necessárias

- **OpenAI API:** Credenciais configuradas no n8n
- **Telegram Bot:** Bot configurado para receber mensagens
- **Agentes Especializados:** Workflows de apoio funcionando

### Modelo de IA

- **Nome:** GPT-4.1 Mini
- **Provedor:** OpenAI
- **Capacidades:** Coordenação de agentes, criação de conteúdo

## Agentes Especializados

### 1. ResearchAgent

- **Função:** Pesquisa sobre o assunto solicitado
- **Execução:** Primeiro (dependência para próximas etapas)
- **Dados:** Informações base para criação de conteúdo

### 2. ThumbnailAgent

- **Função:** Gera ideias para thumbnails
- **Execução:** Segundo
- **Dados:** Conceitos visuais para o vídeo

### 3. TitleAgent

- **Função:** Cria títulos atrativos
- **Execução:** Terceiro
- **Dados:** Títulos otimizados para SEO

### 4. ScriptAgent

- **Função:** Desenvolve roteiro do vídeo
- **Execução:** Quarto
- **Dados:** Estrutura narrativa completa

## Estrutura do Workflow

1. **Telegram Trigger** - Recebe mensagens do usuário
2. **AI Agent** - Coordena agentes especializados
3. **GPT-4.1 Mini** - Modelo de IA para coordenação
4. **Agentes Especializados** - Executam tarefas específicas
5. **Telegram Response** - Envia resultado final

## Casos de Uso

- Criação de ideias para vídeos do YouTube
- Desenvolvimento de conteúdo estruturado
- Otimização de títulos e thumbnails
- Pesquisa automatizada para conteúdo
- Roteiros para vídeos educativos

## Dependências

- Credenciais da OpenAI configuradas
- Bot do Telegram funcionando
- Agentes especializados configurados
- Integração LangChain funcionando

## Monitoramento

- Verificar execuções do workflow
- Monitorar coordenação dos agentes
- Acompanhar qualidade do conteúdo gerado
- Verificar respostas do Telegram

## Tratamento de Erros

- **Falha na IA:** Tratamento de erro configurado
- **Agente indisponível:** Fallback para funcionalidade básica
- **Telegram indisponível:** Log de erro registrado
- **Conteúdo incompleto:** Notificação ao usuário

## Otimizações

- **Sequenciamento:** Execução otimizada dos agentes
- **Cache:** Evitar reprocessamento de assuntos similares
- **Paralelização:** Execução simultânea quando possível
- **Qualidade:** Validação do conteúdo gerado

## Limitações

- Dependência da API OpenAI
- Custo por uso do modelo
- Latência de resposta
- Necessidade de todos os agentes funcionando

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
