# 📱 Chatbot WhatsApp com IA para Texto, Voz, Imagens e PDFs

## Descrição

Sistema inteligente que atende mensagens recebidas via WhatsApp (texto, áudio, imagem e PDF), processa o conteúdo com modelos de IA e responde ao usuário por texto ou áudio, oferecendo uma experiência de atendimento automatizado e multimodal.

## Funcionalidades

- **Trigger:** Recepção de mensagens via WhatsApp
- **Integração:** WhatsApp, IA multimodal, transcrição de áudio, análise de imagem, processamento de PDF
- **Processamento:** Classificação automática de tipos de mídia, processamento inteligente com IA
- **Saída:** Respostas em texto ou áudio sintetizado conforme o contexto da mensagem

## Parâmetros de Entrada

| Parâmetro          | Tipo   | Descrição                                                  |
| ------------------ | ------ | ---------------------------------------------------------- |
| `whatsapp_message` | object | Mensagem recebida via WhatsApp (texto, áudio, imagem, PDF) |
| `message_type`     | string | Tipo de mídia detectado automaticamente                    |
| `user_context`     | object | Histórico de conversa e contexto do usuário                |
| `media_content`    | binary | Conteúdo da mídia (áudio, imagem, PDF)                     |

## Como Funciona

1. **WhatsApp Message Reception:** Dispara o fluxo ao receber novas mensagens via webhook
2. **Input Type Detection:** Classifica automaticamente se a mensagem é texto, áudio, imagem ou documento
3. **Text Processing:** Encaminha mensagens textuais para o modelo de linguagem para gerar respostas apropriadas
4. **Audio Transcription:** Obtém o arquivo de áudio, baixa-o e realiza transcrição para texto antes de processar com a IA
5. **Audio Response Generation:** Converte a resposta de texto em áudio (voz sintetizada) quando necessário e envia ao usuário
6. **Image Analysis:** Faz download da imagem, pede análise detalhada ao modelo de IA e formata uma descrição baseada no conteúdo e na legenda
7. **PDF Processing:** Verifica se o arquivo é PDF, baixa, extrai texto do documento e gera sumário ou respostas conforme solicitação
8. **Error and Invalid Format Handling:** Informa o usuário quando o formato enviado não é suportado ou quando apenas PDFs são aceitos no fluxo de documentos
9. **Simple Session Memory:** Mantém um histórico curto (janela) por usuário para contexto nas interações

## Configuração

### Credenciais Necessárias

- **WhatsApp Business API:** Configuração de webhook e tokens de acesso
- **IA Language Model:** Modelo de linguagem para processamento de texto e geração de respostas
- **Audio Transcription Service:** Serviço para conversão de áudio em texto
- **Image Analysis AI:** Modelo de IA para análise e descrição de imagens
- **PDF Processing Engine:** Sistema para extração e processamento de texto de PDFs
- **Text-to-Speech Service:** Serviço para síntese de voz a partir de texto

### Estrutura de Dados

```json
{
  "whatsapp_message": {
    "message_id": "msg_123456",
    "user_id": "user_789",
    "timestamp": "2025-01-15T12:00:00Z",
    "message_type": "audio",
    "content": {
      "text": "Olá, como posso ajudar?",
      "audio_url": "https://api.whatsapp.com/audio/abc123",
      "image_url": null,
      "pdf_url": null
    }
  },
  "ai_processing": {
    "input_classification": {
      "type": "audio",
      "confidence": 0.98,
      "processing_status": "success"
    },
    "audio_transcription": {
      "transcribed_text": "Olá, gostaria de saber mais sobre seus produtos",
      "transcription_confidence": 0.95,
      "language_detected": "pt-BR"
    },
    "ai_response": {
      "generated_text": "Olá! Fico feliz em ajudar com informações sobre nossos produtos...",
      "response_type": "text",
      "context_used": ["user_history", "product_catalog"]
    }
  },
  "response_generation": {
    "output_type": "audio",
    "text_to_speech": {
      "audio_url": "https://tts.service.com/audio/response_xyz",
      "duration": "00:00:15",
      "voice_used": "female_pt_br"
    },
    "whatsapp_delivery": {
      "status": "sent",
      "delivery_timestamp": "2025-01-15T12:00:30Z"
    }
  },
  "session_memory": {
    "user_id": "user_789",
    "conversation_history": [
      "2025-01-15T12:00:00Z: Usuário enviou áudio",
      "2025-01-15T12:00:30Z: Bot respondeu com áudio"
    ],
    "context_window": 10,
    "current_context": "product_inquiry"
  }
}
```

## Casos de Uso

- **Atendimento ao Cliente:** Respostas automáticas para dúvidas e solicitações
- **Suporte Técnico:** Análise de imagens e documentos para resolução de problemas
- **Vendas e Marketing:** Processamento de consultas sobre produtos e serviços
- **Educação:** Análise de PDFs e geração de resumos educativos
- **Acessibilidade:** Conversão de texto em áudio para usuários com necessidades especiais
- **Documentação:** Processamento automático de documentos PDF enviados
- **Análise de Conteúdo:** Interpretação inteligente de imagens e áudios

## Dependências

- Acesso configurado à WhatsApp Business API com webhook ativo
- Modelos de IA configurados para processamento multimodal
- Serviço de transcrição de áudio configurado
- Sistema de análise de imagem com IA
- Engine de processamento de PDF
- Serviço de Text-to-Speech
- Sistema de memória de sessão para contexto

## Estrutura do Workflow

1. **WhatsApp Webhook Trigger** - Recebe mensagens via webhook
2. **Message Type Detection** - Classifica automaticamente o tipo de mídia
3. **Content Download** - Baixa arquivos de áudio, imagem ou PDF
4. **AI Processing Pipeline** - Processa conteúdo com modelos apropriados
5. **Response Generation** - Gera resposta contextual usando IA
6. **Output Formatting** - Formata resposta (texto ou áudio)
7. **WhatsApp Response** - Envia resposta de volta ao usuário
8. **Session Memory Update** - Atualiza histórico da conversa

## Monitoramento

- **Mensagens Processadas:** Total de mensagens recebidas e respondidas
- **Taxa de Sucesso:** Percentual de processamentos bem-sucedidos
- **Tempo de Resposta:** Latência média entre recebimento e resposta
- **Distribuição de Tipos:** Percentual de cada tipo de mídia processado
- **Qualidade da Transcrição:** Precisão da conversão de áudio para texto
- **Performance da IA:** Tempo de resposta dos modelos de IA
- **Erros de Processamento:** Falhas e tipos de erro encontrados

## Tratamento de Erros

- **Formato Não Suportado:** Notificação clara sobre tipos aceitos
- **Falha na Transcrição:** Fallback para processamento manual
- **Erro de IA:** Resposta padrão com notificação de problema
- **Falha no Download:** Retry automático com notificação
- **Timeout de Processamento:** Cancelamento e notificação de falha
- **Permissões Insuficientes:** Log de erro e notificação administrativa
- **Formato de Arquivo Inválido:** Validação e skip de arquivos corrompidos

## Características Técnicas

### Processamento Multimodal

- **Classificação Automática:** Identificação inteligente de tipos de mídia
- **Pipeline Adaptativo:** Processamento específico para cada tipo de conteúdo
- **Contexto Inteligente:** Manutenção de histórico para conversas contínuas
- **Fallback Robusto:** Alternativas em caso de falha de processamento

### Integração WhatsApp

- **Webhook em Tempo Real:** Recepção instantânea de mensagens
- **Resposta Automática:** Envio automático de respostas geradas
- **Suporte a Mídia:** Processamento de todos os tipos de conteúdo
- **Gestão de Sessão:** Controle de contexto por usuário

### Processamento com IA

- **Modelos Especializados:** IA específica para cada tipo de mídia
- **Análise Contextual:** Compreensão do contexto da conversa
- **Geração Inteligente:** Respostas contextualmente apropriadas
- **Aprendizado Contínuo:** Melhoria da qualidade com uso

### Sistema de Memória

- **Histórico de Conversa:** Rastreamento de interações anteriores
- **Janela de Contexto:** Manutenção de contexto relevante
- **Personalização:** Adaptação baseada no histórico do usuário
- **Limpeza Automática:** Gestão de memória para otimização

---

_Autor: Matheus Freitas_  
_Categoria: WhatsApp_  
_Versão: 1.0_
