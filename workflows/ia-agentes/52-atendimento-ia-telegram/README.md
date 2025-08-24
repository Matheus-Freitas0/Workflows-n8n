# 🤖 Atendimento IA via Telegram

## Descrição

O workflow atua como um agente de IA para responder mensagens via Telegram. Ele executa várias ações, incluindo envio de emails, verificação de emails não lidos, gestão de tarefas e reuniões, criação de eventos de calendário e realização de chamadas, tudo utilizando ferramentas externas integradas.

## Funcionalidades

- **Detecção de Mensagens Telegram:** Inicia a automação ao receber uma mensagem do usuário via Telegram Trigger
- **Manutenção de Contexto:** Usa "Window Buffer Memory" para preservar o estado da conversa entre mensagens
- **Interpretação de Comandos IA e Ativação de Ferramentas:** Identifica ações solicitadas (como email, emails não lidos, tarefa, reunião, etc.) e invoca a ferramenta externa correspondente
- **Envio de Emails:** Utiliza ferramenta de envio de email para despachar mensagens, incluindo destinatário, assunto e conteúdo
- **Recuperação de Emails Não Lidos:** Consulta a caixa de entrada para exibir mensagens não lidas
- **Gestão de Reuniões:** Permite verificar reuniões de hoje e criar novos eventos de calendário
- **Criação de Eventos de Calendário:** Agenda novos compromissos, especificando horários de início e fim, participantes, descrição e resumo
- **Gestão de Tarefas:** Lista tarefas de hoje e permite adicionar novas tarefas
- **Acesso a Dados de Contato:** Consulta informações de contato de um banco de dados ou vector store
- **Busca Semântica com Embeddings:** Emprega embeddings OpenAI e Pinecone para melhorar a correspondência de contatos
- **Transcrição de Áudio:** Converte mensagens de voz em texto para processamento
- **Envio de Respostas Telegram:** Retorna informações ou confirmações ao usuário via chat
- **Execução de Chamadas Telefônicas:** Inicia chamadas telefônicas quando solicitado

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                           |
| --------- | ------ | ----------------------------------- |
| `message` | string | Mensagem recebida via Telegram      |
| `chat_id` | string | ID do chat do usuário               |
| `user_id` | string | ID do usuário que enviou a mensagem |

## Como Funciona

1. **Trigger Telegram:** Recebe mensagem do usuário via Telegram
2. **Validação de Mensagem:** Verifica se a mensagem contém texto ou é mensagem de voz
3. **Processamento de Áudio:** Converte mensagens de voz em texto quando necessário
4. **Interpretação de Comando:** IA identifica a ação solicitada pelo usuário
5. **Ativação de Ferramentas:** Invoca a ferramenta externa apropriada
6. **Execução da Ação:** Realiza a tarefa solicitada (email, calendário, tarefas, etc.)
7. **Resposta ao Usuário:** Envia confirmação ou resultado via Telegram
8. **Manutenção de Contexto:** Preserva histórico da conversa para continuidade

## Configuração

### Credenciais Necessárias

- **Telegram API:** Para recebimento e envio de mensagens
- **OpenAI API:** Para processamento de linguagem natural e embeddings
- **Pinecone:** Para armazenamento e busca vetorial de contatos
- **Ferramentas de Workflow:** Para execução de ações específicas

### Estrutura de Dados

```json
{
  "telegram_message": {
    "chat_id": "123456789",
    "user_id": "987654321",
    "text": "Envie um email para joao@email.com",
    "voice": null
  },
  "ai_interpretation": {
    "action": "send_email",
    "parameters": {
      "recipient": "joao@email.com",
      "subject": "Assunto do email",
      "content": "Conteúdo da mensagem"
    }
  },
  "context_memory": {
    "session_key": "123456789",
    "conversation_history": ["mensagens anteriores"]
  }
}
```

## Casos de Uso

- **Assistente Pessoal:** Gestão de emails, calendário e tarefas via Telegram
- **Atendimento ao Cliente:** Suporte automatizado com IA para consultas comuns
- **Automação de Escritório:** Gestão de compromissos e comunicação
- **Suporte Remoto:** Assistência para usuários em campo ou viagem
- **Integração de Sistemas:** Ponte entre Telegram e ferramentas de produtividade

## Dependências

- Telegram Bot API configurada
- OpenAI API para processamento de linguagem natural
- Pinecone para busca vetorial de contatos
- Ferramentas de workflow para ações específicas
- Sistema de memória para contexto de conversa

## Estrutura do Workflow

1. **Telegram Trigger** - Recebe mensagens do usuário
2. **If** - Valida se é mensagem de texto ou voz
3. **OpenAI** - Processa mensagens de voz (transcrição)
4. **Edit Fields** - Prepara dados para processamento
5. **AI Agent** - Interpreta comandos e executa ações
6. **Window Buffer Memory** - Mantém contexto da conversa
7. **Ferramentas Específicas** - Executa ações solicitadas
8. **Telegram** - Envia respostas ao usuário

## Monitoramento

- Status de recebimento de mensagens Telegram
- Performance da interpretação de comandos com IA
- Taxa de sucesso na execução de ações
- Qualidade da manutenção de contexto
- Tempo de resposta para o usuário

## Tratamento de Erros

- Validação de mensagens recebidas
- Tratamento de falhas na transcrição de áudio
- Fallback para comandos padrão em caso de erro
- Logs de debugging para troubleshooting
- Validação de credenciais de APIs

## Configurações Avançadas

### Ferramentas Integradas

- **send_email:** Envio de emails com destinatário, assunto e conteúdo
- **retrieve_unread_emails:** Consulta de emails não lidos na caixa de entrada
- **get_todays_meetings:** Verificação de reuniões agendadas para hoje
- **create_calendar_event:** Criação de novos eventos no calendário
- **add_to_do_task:** Adição de novas tarefas à lista de afazeres
- **get_todays_tasks:** Consulta de tarefas agendadas para hoje
- **database:** Busca de informações de contato via vector store
- **make_phone_call:** Execução de chamadas telefônicas

### Capacidades de IA

- **Interpretação de Comandos:** Identificação automática de ações solicitadas
- **Processamento de Linguagem Natural:** Compreensão de intenções do usuário
- **Transcrição de Áudio:** Conversão de mensagens de voz em texto
- **Busca Semântica:** Localização de contatos usando embeddings

### Funcionalidades de Comunicação

- **Respostas Contextuais:** Manutenção de histórico de conversa
- **Formatação Markdown:** Suporte a formatação rica nas respostas
- **Processamento Assíncrono:** Execução de tarefas em background
- **Notificações Inteligentes:** Alertas baseados em contexto

### Integrações

- **Telegram:** Interface principal de comunicação
- **OpenAI:** Processamento de linguagem natural e embeddings
- **Pinecone:** Armazenamento vetorial para busca de contatos
- **Ferramentas de Workflow:** Execução de ações específicas
- **Sistemas Externos:** Email, calendário, tarefas e telefonia

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
