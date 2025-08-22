# 🎬 Gerar Narração de Vídeo com IA e TTS

## Descrição

Sistema inteligente que extrai frames de um vídeo, utiliza um modelo multimodal para gerar um roteiro de narração em partes e converte o roteiro final em um arquivo de áudio que é salvo em nuvem.

## Funcionalidades

- **Trigger:** URL de vídeo público para processamento
- **Integração:** IA multimodal, TTS (Text-to-Speech), processamento de vídeo
- **Processamento:** Análise visual e geração de narração inteligente
- **Saída:** Arquivo de áudio MP3 com narração completa

## Parâmetros de Entrada

| Parâmetro   | Tipo   | Descrição                               |
| ----------- | ------ | --------------------------------------- |
| `video_url` | string | URL pública do vídeo para processamento |
| `config`    | object | Configurações de IA e TTS               |
| `output`    | object | Configurações de saída e armazenamento  |

## Como Funciona

1. **Download do Vídeo:** Baixa um vídeo de uma URL pública para processamento
2. **Extração de Frames:** Decodifica o vídeo e captura frames distribuídos uniformemente limitando a quantidade para desempenho
3. **Agrupamento em Lotes:** Divide os frames em batches sequenciais para enviar ao modelo multimodal sem exceder limites de entrada
4. **Redimensionamento e Conversão:** Redimensiona as imagens e converte para formato binário/jpg para envio ao modelo
5. **Geração de Roteiro por Partes:** Usa um modelo de visão+linguagem para criar trechos de narração a partir de cada lote de frames continuando a partir de iterações anteriores para coerência
6. **Combinação de Texto:** Agrega todos os trechos gerados em um roteiro completo e coeso
7. **Síntese de Voz (TTS):** Converte o roteiro final em um arquivo de áudio (mp3)
8. **Upload para Armazenamento:** Envia o arquivo de áudio final para uma pasta na nuvem
9. **Gerenciamento de Limites:** Insere esperas/pausas entre chamadas para respeitar limites de serviço e evitar rate limits

## Configuração

### Credenciais Necessárias

- **IA Multimodal:** Modelo de visão+linguagem configurado
- **TTS:** Serviço de síntese de voz configurado
- **Armazenamento:** Acesso a pasta na nuvem para upload
- **Processamento:** Recursos para decodificação de vídeo

### Estrutura de Dados

```json
{
  "video_input": {
    "url": "https://exemplo.com/video.mp4",
    "duration": 120,
    "format": "mp4",
    "resolution": "1920x1080"
  },
  "frame_processing": {
    "total_frames": 3600,
    "sampled_frames": 120,
    "batch_size": 10,
    "frame_interval": 1
  },
  "ai_generation": {
    "model": "multimodal-vision-language",
    "prompt_template": "Descreva o que está acontecendo neste frame de vídeo",
    "max_tokens": 150,
    "temperature": 0.7
  },
  "tts_output": {
    "voice": "pt-BR-Neural2-A",
    "speed": 1.0,
    "pitch": 0,
    "format": "mp3",
    "quality": "high"
  },
  "narration_script": {
    "segments": [
      {
        "frame_range": [0, 10],
        "description": "Descrição do primeiro segmento",
        "duration": 10
      }
    ],
    "full_script": "Narração completa combinada",
    "total_duration": 120
  }
}
```

## Casos de Uso

- **Criação de Conteúdo:** Geração automática de narrações para vídeos educativos
- **Acessibilidade:** Adição de narração para vídeos sem áudio
- **Marketing:** Criação de conteúdo narrado para campanhas
- **Educação:** Produção de material didático com narração automática
- **Entretenimento:** Geração de comentários para vídeos esportivos ou eventos

## Dependências

- Modelo de IA multimodal configurado
- Serviço de TTS funcionando
- Acesso a armazenamento em nuvem
- Capacidade de processamento de vídeo
- Conexão estável com internet

## Estrutura do Workflow

1. **HTTP Request** - Download do vídeo da URL fornecida
2. **Video Processing** - Decodificação e extração de frames
3. **Frame Sampling** - Seleção uniforme de frames para análise
4. **Batch Processing** - Agrupamento de frames em lotes
5. **Image Conversion** - Redimensionamento e conversão para formato adequado
6. **AI Analysis** - Geração de descrições usando modelo multimodal
7. **Script Assembly** - Combinação de trechos em roteiro completo
8. **TTS Generation** - Conversão de texto para áudio
9. **Cloud Upload** - Envio do arquivo final para armazenamento

## Monitoramento

- **Vídeos Processados:** Contagem de vídeos convertidos com sucesso
- **Tempo de Processamento:** Duração total do workflow por vídeo
- **Qualidade IA:** Feedback sobre descrições geradas
- **TTS Performance:** Sucesso na geração de áudio
- **Upload Status:** Confirmação de envio para nuvem
- **Rate Limiting:** Controle de limites de API

## Tratamento de Erros

- **URL Inválida:** Validação de URL antes do download
- **Falha Download:** Retry com backoff exponencial
- **Processamento Vídeo:** Fallback para formatos alternativos
- **Erro IA:** Notificação de falha na geração
- **Falha TTS:** Retry com configurações alternativas
- **Upload Falhou:** Retry de envio para nuvem
- **Timeout:** Cancelamento de operações longas

## Características Técnicas

### Processamento de Vídeo

- **Formato Suportado:** MP4, AVI, MOV, WebM
- **Resolução:** Adaptável (até 4K)
- **Duração:** Sem limite, com otimização automática
- **Frame Rate:** Preservação da taxa original
- **Compressão:** Otimização para processamento

### Análise IA Multimodal

- **Modelo:** Visão + Linguagem configurável
- **Contexto:** Análise sequencial de frames
- **Coerência:** Manutenção de continuidade narrativa
- **Idioma:** Suporte a múltiplos idiomas
- **Estilo:** Adaptável ao tipo de conteúdo

### Síntese de Voz (TTS)

- **Vozes:** Múltiplas opções de voz natural
- **Idiomas:** Suporte a diversos idiomas
- **Qualidade:** Áudio de alta fidelidade
- **Velocidade:** Ajustável conforme necessidade
- **Formato:** MP3 com qualidade configurável

### Gerenciamento de Recursos

- **Rate Limiting:** Respeito aos limites de API
- **Batch Processing:** Otimização de uso de recursos
- **Cache:** Armazenamento temporário de frames
- **Cleanup:** Limpeza automática de arquivos temporários
- **Monitoring:** Acompanhamento de uso de recursos

### Armazenamento em Nuvem

- **Formato:** MP3 com metadados
- **Organização:** Estrutura de pastas configurável
- **Backup:** Redundância de armazenamento
- **Acesso:** Controle de permissões
- **Versioning:** Controle de versões de arquivos

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
