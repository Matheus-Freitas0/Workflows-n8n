# 📅 Agente de Agendamento

## Descrição

Agente principal de agendamento com inteligência artificial para conversas naturais. Este workflow permite que usuários agendem, reagendem, cancelem e consultem eventos através de conversas em linguagem natural.

## Funcionalidades

- **Trigger:** Mensagem de chat recebida via webhook
- **Integração:** OpenAI GPT-4 + Cal.com API + LangChain
- **Processamento:** Conversas naturais para agendamento
- **Memória:** Contexto de conversa com buffer de janela
- **Automação:** Agendamento completo via conversa

## Como Funciona

1. **Recebimento:** Webhook recebe mensagem do usuário
2. **Análise:** Agente analisa intenção da mensagem
3. **Execução:** Executa ação apropriada (agendar, consultar, etc.)
4. **Resposta:** Gera resposta natural para o usuário
5. **Memória:** Mantém contexto da conversa

## Configuração

### Credenciais Necessárias

- **OpenAI API:** Credenciais configuradas no n8n
- **Cal.com:** API configurada para agendamentos
- **Webhook:** Configurado para receber mensagens de chat

### Modelo de IA

- **Nome:** GPT-4.1 Mini
- **Provedor:** OpenAI
- **Capacidades:** Processamento de linguagem natural, agendamento

### Memória

- **Tipo:** Buffer Window
- **Tamanho:** 7 mensagens
- **Função:** Manter contexto da conversa

## Funcionalidades Principais

### 1. Consulta de Eventos Disponíveis
- Lista todos os eventos disponíveis
- Filtra eventos ocultos
- Apresenta opções para o usuário

### 2. Verificação de Horários
- Consulta disponibilidade por data
- Converte fusos horários (UTC ↔ America/Sao_Paulo)
- Formato ISO 8601 para APIs

### 3. Agendamento de Eventos
- Coleta nome e email do usuário
- Valida dados obrigatórios
- Cria agendamento via Cal.com API
- Retorna chave da reunião

### 4. Cancelamento de Eventos
- Solicita chave secreta do evento
- Coleta razão do cancelamento
- Executa cancelamento via API
- Confirma sucesso da operação

### 5. Reagendamento
- Consulta nova data desejada
- Verifica horários disponíveis
- Converte horário para UTC
- Executa reagendamento
- Informa nova chave do evento

### 6. Consulta de Detalhes
- Solicita chave do evento
- Retorna informações completas
- Formata dados para o usuário

## Estrutura do Workflow

1. **Chat Trigger** - Recebe mensagens via webhook
2. **AI Agent** - Processa mensagens e executa ações
3. **GPT-4.1 Mini** - Modelo de IA para conversas
4. **Memory Buffer** - Mantém contexto da conversa
5. **Cal.com Tools** - Integração com API de agendamento

## Casos de Uso

- Agendamento de reuniões via chat
- Consulta de disponibilidade
- Gestão de eventos existentes
- Atendimento automatizado para agendamentos
- Integração com sistemas de calendário

## Dependências

- Credenciais da OpenAI configuradas
- API do Cal.com acessível
- Webhook configurado para receber mensagens
- Integração LangChain funcionando

## Monitoramento

- Verificar execuções do workflow
- Monitorar conversas de agendamento
- Acompanhar sucesso das operações
- Verificar uso da API Cal.com

## Tratamento de Erros

- **Dados inválidos:** Validação e solicitação de correção
- **API indisponível:** Mensagem de erro amigável
- **Fusos horários:** Conversão automática
- **Contexto perdido:** Solicitação de informações

## Segurança

- **Validação de dados:** Verificação de entrada
- **Chaves secretas:** Proteção de eventos
- **Logs de auditoria:** Todas as operações registradas
- **Controle de acesso:** Validação de permissões

---
*Autor: Matheus Freitas*  
*Categoria: Agendamento*  
*Versão: 1.0*
