# 🎬 Criação de Vídeos POV com IA

## Descrição

Sistema automatizado para criação de vídeos curtos POV (Point of View) para plataformas como TikTok, Shorts e Reels. O workflow lê ideias de uma planilha Google Sheets, gera legendas, imagens, narração e monta um vídeo final pronto para publicação usando inteligência artificial.

## Funcionalidades

- **Trigger:** Leitura de planilha Google Sheets com ideias marcadas
- **Integração:** Google Sheets, IA para geração de conteúdo, serviços de imagem/vídeo, Google Drive, Discord
- **Processamento:** Geração automática de legendas, imagens, narração e montagem de vídeo
- **Saída:** Vídeo final renderizado e uploadado para Google Drive com notificação Discord

## Parâmetros de Entrada

| Parâmetro        | Tipo   | Descrição                                 |
| ---------------- | ------ | ----------------------------------------- |
| `spreadsheet_id` | string | ID da planilha Google Sheets              |
| `idea_data`      | object | Dados da ideia e parâmetros da planilha   |
| `api_keys`       | object | Chaves de API para serviços de IA e mídia |

## Como Funciona

1. **Carregamento de Ideias:** Lê uma linha marcada da planilha Google Sheets para obter a ideia e parâmetros
2. **Geração de Legendas:** Cria 5 legendas concisas e provocativas em primeira pessoa a partir da ideia fornecida
3. **Validação de Formato:** Verifica e transforma a resposta da legenda em uma lista estruturada para processamento
4. **Criação de Prompts de Imagem:** Expande cada legenda em um prompt foto-realista POV otimizado para o modelo de imagem
5. **Cálculo de Tokens:** Soma e registra o uso de tokens de chamada de linguagem para controle de custos
6. **Geração de Imagens:** Envia prompts para serviço de geração de imagem para criar imagens verticais em estilo influencer
7. **Conversão Imagem→Vídeo:** Transforma cada imagem em clipes curtos (5s) com controle de câmera e parâmetros de qualidade
8. **Monitoramento e Retry:** Aguarda e verifica o status das tarefas de geração, repetindo em falhas
9. **Geração de Roteiro:** Une as legendas em um roteiro curto, dividido em 5 partes para narração rápida (~15s)
10. **Síntese de Voz:** Converte o roteiro em áudio usando serviço de text-to-speech e salva o arquivo de áudio
11. **Armazenamento e Permissões:** Faz upload do áudio para Google Drive e ajusta permissões para compartilhamento público
12. **Pareamento de Mídia:** Combina os clipes de vídeo gerados com áudios e legendas correspondentes para cada cena
13. **Renderização Final:** Usa um template pré-configurado para montar o vídeo final com vídeos, áudio e textos substituídos
14. **Upload do Vídeo Final:** Baixa o render, envia para Google Drive, define permissões públicas e registra o link
15. **Atualização de Planilha e Notificação:** Atualiza a linha original com metadados (tokens, custos, link final) e notifica via webhook no Discord
16. **Agendamento e Configuração:** Permite definir chaves de API e executar o fluxo uma vez por dia automaticamente

## Configuração

### Credenciais Necessárias

- **Google Sheets API:** Acesso para leitura e atualização de planilhas
- **Google Drive API:** Upload e gerenciamento de arquivos de mídia
- **IA Language Model:** Modelo de linguagem para geração de legendas e roteiros
- **Image Generation Service:** Serviço para criação de imagens POV
- **Video Generation Service:** Serviço para conversão de imagem em vídeo
- **Text-to-Speech Service:** Serviço para síntese de voz
- **Video Rendering Service:** Serviço para montagem final do vídeo
- **Discord Webhook:** Notificações de conclusão e status

### Estrutura de Dados

```json
{
  "spreadsheet_config": {
    "spreadsheet_id": "1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms",
    "idea_column": "A",
    "status_column": "B",
    "metadata_columns": ["C", "D", "E", "F"]
  },
  "ai_generation": {
    "caption_model": "gpt-4",
    "image_model": "dall-e-3",
    "voice_model": "elevenlabs",
    "temperature": 0.8,
    "max_tokens": 1000
  },
  "video_settings": {
    "duration_per_clip": 5,
    "resolution": "1080x1920",
    "fps": 30,
    "camera_movement": "subtle_pan",
    "style": "influencer_pov"
  },
  "output_config": {
    "final_video_duration": "15-20s",
    "format": "mp4",
    "quality": "high",
    "auto_upload": true,
    "discord_notification": true
  }
}
```

## Casos de Uso

- **Criação de Conteúdo Automático:** Geração de vídeos POV para redes sociais sem intervenção manual
- **Escalabilidade de Produção:** Criação de múltiplos vídeos a partir de ideias em lote
- **Teste de Conceitos:** Validação rápida de ideias de conteúdo antes de produção manual
- **Conteúdo para Influenciadores:** Geração automática de vídeos POV para criadores de conteúdo
- **Marketing Digital:** Criação de conteúdo promocional POV para campanhas
- **Educação e Treinamento:** Vídeos POV para demonstrações e tutoriais

## Dependências

- Conta Google com APIs habilitadas (Sheets, Drive)
- Serviços de IA configurados (OpenAI, DALL-E, ElevenLabs)
- Serviços de geração de vídeo e renderização
- Webhook Discord configurado para notificações
- Planilha Google Sheets com estrutura adequada
- Sistema de agendamento para execução automática

## Estrutura do Workflow

1. **Google Sheets Trigger** - Lê ideias marcadas da planilha
2. **Caption Generation** - Gera legendas usando IA
3. **Format Validation** - Valida e estrutura as respostas
4. **Image Prompt Creation** - Cria prompts para geração de imagens
5. **Token Calculation** - Calcula e registra uso de tokens
6. **Image Generation** - Gera imagens POV usando IA
7. **Image to Video Conversion** - Converte imagens em clipes de vídeo
8. **Generation Monitoring** - Monitora status e faz retry em falhas
9. **Script Generation** - Cria roteiro unificado para narração
10. **Voice Synthesis** - Gera áudio usando TTS
11. **Google Drive Upload** - Faz upload do áudio e ajusta permissões
12. **Media Pairing** - Combina vídeos, áudios e legendas
13. **Final Rendering** - Monta vídeo final usando template
14. **Final Video Upload** - Upload do vídeo final para Google Drive
15. **Spreadsheet Update** - Atualiza planilha com metadados
16. **Discord Notification** - Notifica conclusão via webhook

## Monitoramento

- **Vídeos Gerados:** Total de vídeos POV criados com sucesso
- **Taxa de Sucesso:** Percentual de ideias convertidas em vídeos
- **Uso de Tokens:** Controle de custos de APIs de IA
- **Tempo de Processamento:** Latência média por vídeo gerado
- **Qualidade de Saída:** Feedback sobre qualidade das imagens e áudios
- **Status de Uploads:** Confirmação de uploads para Google Drive

## Tratamento de Erros

- **Falha na Geração de IA:** Retry automático com prompts ajustados
- **Erro de Conversão de Vídeo:** Notificação e continuação com próximo item
- **Falha no Upload:** Retry com backoff exponencial
- **API Rate Limit:** Pausas automáticas entre chamadas
- **Formato Inválido:** Validação e correção automática de dados
- **Timeout de Renderização:** Cancelamento e notificação de erro

## Características Técnicas

### Geração de Conteúdo com IA

- **Modelo de Linguagem Avançado:** Geração de legendas e roteiros contextualizados
- **Modelo de Imagem Especializado:** Criação de imagens POV foto-realistas
- **Síntese de Voz Natural:** Narração com entonação e ritmo apropriados
- **Validação de Formato:** Verificação automática de estrutura de dados

### Processamento de Mídia

- **Conversão Inteligente:** Transformação de imagem em vídeo com movimento de câmera
- **Template de Renderização:** Sistema de montagem baseado em templates pré-configurados
- **Otimização de Qualidade:** Configurações de vídeo otimizadas para redes sociais
- **Formato de Saída Padrão:** Vídeos verticais prontos para TikTok/Shorts/Reels

### Integração e Automação

- **Google Sheets Integration:** Leitura e atualização automática de planilhas
- **Google Drive Management:** Upload automático com permissões configuradas
- **Discord Notifications:** Sistema de notificação em tempo real
- **Agendamento Automático:** Execução programada diária

### Controle de Custos

- **Monitoramento de Tokens:** Rastreamento preciso do uso de APIs de IA
- **Cálculo de Custos:** Estimativa de gastos por vídeo gerado
- **Otimização de Recursos:** Uso eficiente de serviços pagos
- **Relatórios de Uso:** Metadados detalhados para análise de custos

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
