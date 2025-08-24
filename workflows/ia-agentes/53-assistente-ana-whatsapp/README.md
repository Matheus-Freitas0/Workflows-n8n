# 🤖 Assistente Ana

## Descrição

Fluxo que recebe mensagens via WhatsApp, processa áudio, imagem e texto, utiliza IA para transcrição, explicação de imagens, resumo e geração de mensagens, mantém memória de conversas e coordena tarefas como leitura/criação de eventos no calendário, envio de e-mails e consultas na web, respondendo ao usuário com o Assistente Ana.

## Funcionalidades

- **Detecção e Roteamento de Mensagens:** Identifica o tipo de conteúdo (áudio, imagem, vídeo, texto) e encaminha para as etapas correspondentes
- **Transcrição de Áudio:** Transcreve arquivos de áudio para texto usando IA
- **Explicação de Imagem:** Descreve imagens enviadas e extrai texto visível
- **Resumo de Mensagens:** Gera resumos de textos recebidos
- **Memória de Conversa:** Armazena o histórico de chat em Postgres para contexto
- **Busca Semântica e Recuperação de Informações:** Usa um vector store (Supabase) e embeddings para localizar contatos, templates e conteúdos relevantes
- **Gerenciamento de Calendário:** Lê e cria eventos no Google Calendar
- **Envio/Aprovação de Emails com Templates:** Consulta templates na vector store e envia emails via Gmail
- **Resposta ao Usuário via WhatsApp:** Envia mensagens com conteúdo gerado pelo fluxo
- **Roteamento por Tipo de Conteúdo:** Utiliza um switch para tratar áudio, vídeo, imagem e texto
- **Integração com Modelos de Linguagem:** Utiliza modelos OpenAI para geração de respostas e conteúdos
- **Armazenamento de Memória de Chat por Sessão:** Utiliza chave de sessão personalizada para manter contexto

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                                    |
| --------- | ------ | -------------------------------------------- |
| `message` | object | Mensagem recebida via WhatsApp               |
| `type`    | string | Tipo de conteúdo (audio, image, video, text) |
| `from`    | string | ID do usuário que enviou a mensagem          |
| `caption` | string | Legenda da mensagem (quando aplicável)       |

## Como Funciona

1. **Trigger WhatsApp:** Recebe mensagem do usuário via WhatsApp
2. **Identificação de Tipo:** Identifica se é áudio, imagem, vídeo ou texto
3. **Download de Mídia:** Baixa arquivos de áudio e imagem para processamento
4. **Processamento Específico:**
   - **Áudio:** Transcreve para texto usando IA
   - **Imagem:** Descreve conteúdo e extrai texto visível
   - **Texto:** Gera resumo do conteúdo
5. **Preparação de Dados:** Organiza informações para processamento
6. **Assistente Ana:** Processa solicitações e coordena ações
7. **Execução de Tarefas:** Realiza ações solicitadas (calendário, emails, consultas web)
8. **Resposta ao Usuário:** Envia resposta via WhatsApp
9. **Memória de Conversa:** Armazena histórico em Postgres para contexto futuro

## Configuração

### Credenciais Necessárias

- **WhatsApp Business API:** Para recebimento e envio de mensagens
- **OpenAI API:** Para processamento de linguagem natural, transcrição e análise de imagem
- **PostgreSQL:** Para armazenamento de memória de chat
- **Supabase:** Para vector store e busca semântica
- **Google Calendar:** Para gestão de eventos
- **Gmail:** Para envio de emails
- **SerpAPI:** Para consultas na web

### Estrutura de Dados

```json
{
  "whatsapp_message": {
    "type": "audio|image|video|text",
    "from": "123456789",
    "text": "Mensagem de texto",
    "audio": {
      "id": "audio_id",
      "caption": "Legenda do áudio"
    },
    "image": {
      "id": "image_id",
      "caption": "Legenda da imagem"
    }
  },
  "processed_content": {
    "transcription": "Texto transcrito do áudio",
    "image_description": "Descrição da imagem",
    "text_summary": "Resumo do texto"
  },
  "user_context": {
    "session_key": "123456789",
    "conversation_history": ["mensagens anteriores"],
    "user_preferences": {}
  }
}
```

## Casos de Uso

- **Assistente Pessoal:** Gestão de calendário, emails e tarefas via WhatsApp
- **Atendimento ao Cliente:** Suporte automatizado com IA para diferentes tipos de mídia
- **Processamento Multimodal:** Análise de áudio, imagem e texto com IA
- **Automação de Escritório:** Gestão de compromissos e comunicação
- **Suporte Remoto:** Assistência para usuários em campo ou viagem
- **Integração de Sistemas:** Ponte entre WhatsApp e ferramentas de produtividade

## Dependências

- WhatsApp Business API configurada
- OpenAI API para processamento de IA
- PostgreSQL para memória de conversa
- Supabase para vector store e embeddings
- Google Calendar para gestão de eventos
- Gmail para envio de emails
- SerpAPI para consultas na web
- Sistema de processamento multimodal

## Estrutura do Workflow

1. **WhatsApp Trigger1** - Recebe mensagens do usuário
2. **Identify and ReRoute Message Types** - Identifica tipo de conteúdo e roteia
3. **Get Audio/Image URL** - Obtém URLs de mídia
4. **Download Audio/Image** - Baixa arquivos para processamento
5. **Audio Transcriber** - Transcreve áudio para texto
6. **Image Explainer** - Descreve conteúdo de imagens
7. **Text Summarizer** - Resume textos recebidos
8. **Get User's Message** - Prepara dados para processamento
9. **Assistent Ana** - Processa solicitações e coordena ações
10. **Postgres Chat Memory** - Mantém contexto da conversa
11. **Vector Store Tool** - Busca semântica de informações
12. **Respond to User** - Envia respostas via WhatsApp

## Monitoramento

- Status de recebimento de mensagens WhatsApp
- Performance do processamento multimodal (áudio, imagem, texto)
- Taxa de sucesso na transcrição e análise de conteúdo
- Qualidade da manutenção de contexto
- Tempo de resposta para o usuário
- Performance da busca semântica

## Tratamento de Erros

- Validação de tipos de mídia recebidos
- Tratamento de falhas no download de arquivos
- Fallback para processamento de texto quando mídia falha
- Validação de credenciais de APIs
- Logs de debugging para troubleshooting
- Tratamento de falhas na memória de conversa

## Configurações Avançadas

### Processamento Multimodal

- **Áudio:** Transcrição automática com OpenAI Whisper
- **Imagem:** Análise visual com OpenAI Vision
- **Vídeo:** Processamento de frames para análise
- **Texto:** Resumo e análise de conteúdo

### Sistema de Memória

- **Postgres Chat Memory:** Armazenamento persistente de conversas
- **Session Key:** Identificação única por usuário
- **Context Window:** Manutenção de histórico relevante
- **Vector Embeddings:** Busca semântica de informações

### Ferramentas Integradas

- **Calendar Events:** Leitura e criação de eventos no Google Calendar
- **Email Management:** Criação e aprovação de emails com templates
- **Web Search:** Consultas na web via SerpAPI
- **Contact Database:** Busca de informações de contatos

### Capacidades de IA

- **Transcrição de Áudio:** Conversão de voz para texto
- **Análise de Imagem:** Descrição e extração de texto visual
- **Processamento de Linguagem Natural:** Compreensão e geração de respostas
- **Busca Semântica:** Localização inteligente de informações

### Funcionalidades de Comunicação

- **Respostas Contextuais:** Manutenção de histórico de conversa
- **Processamento Assíncrono:** Execução de tarefas em background
- **Notificações Inteligentes:** Alertas baseados em contexto
- **Integração Multicanal:** Suporte a diferentes tipos de mídia

### Integrações

- **WhatsApp:** Interface principal de comunicação
- **OpenAI:** Processamento de IA para múltiplas modalidades
- **PostgreSQL:** Armazenamento de memória de conversa
- **Supabase:** Vector store para busca semântica
- **Google Services:** Calendar e Gmail para automação
- **SerpAPI:** Consultas na web para informações atualizadas

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
