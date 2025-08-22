# 📢 Geração Automática de Metadados para YouTube

## Descrição

Sistema inteligente que automatiza a criação e atualização de metadados de vídeos do YouTube (título, descrição, tags, hashtags e CTAs) a partir do link do vídeo, transcrição e palavras-chave focais, incorporando links de afiliado e promocionais para otimização de SEO e conversão.

## Funcionalidades

- **Trigger:** Formulário web para coleta de dados do vídeo
- **Integração:** YouTube API, IA para geração de metadados, sistemas de links promocionais
- **Processamento:** Geração inteligente de metadados, validação e estruturação, atualização automática
- **Saída:** Vídeo atualizado com metadados otimizados e confirmação ao usuário

## Parâmetros de Entrada

| Parâmetro         | Tipo   | Descrição                                    |
| ----------------- | ------ | -------------------------------------------- |
| `video_link`      | string | Link do vídeo do YouTube para atualização    |
| `transcription`   | string | Transcrição completa do conteúdo do vídeo    |
| `focal_keywords`  | array  | Palavras-chave focais para otimização SEO    |
| `affiliate_links` | object | Links de afiliados e promocionais relevantes |

## Como Funciona

1. **Coleta via Formulário:** Recebe o link do vídeo, a transcrição e as palavras-chave foco através de um formulário web
2. **Consulta de Links Promocionais:** Recupera links de afiliados, cursos e referências relevantes de um documento para usar na descrição
3. **Geração de Metadados por IA:** Utiliza um modelo de linguagem para criar título, descrição otimizada para SEO, lista de tags, hashtags e CTA
4. **Validação e Estruturação:** Converte a saída da IA para um JSON estruturado conforme esquema pré-definido para automação
5. **Extração de ID do Vídeo:** Extrai o ID do vídeo a partir do link informado para permitir a atualização via API
6. **Formatação de Tags:** Agrupa e formata as tags geradas para envio correto à plataforma de vídeo
7. **Atualização do Vídeo no YouTube:** Atualiza título, descrição, tags e hashtags do vídeo usando a API do YouTube
8. **Confirmação ao Usuário:** Exibe uma mensagem de conclusão com o título atualizado e o link do vídeo após o processamento

## Configuração

### Credenciais Necessárias

- **YouTube Data API v3:** Chave de API para acesso e atualização de vídeos
- **IA Language Model:** Modelo de linguagem para geração de metadados otimizados
- **Formulário Web:** Interface para coleta de dados de entrada
- **Sistema de Links:** Base de dados de links promocionais e afiliados
- **Documento de Referência:** Arquivo com links e referências para incorporação

### Estrutura de Dados

```json
{
  "video_input": {
    "video_link": "https://www.youtube.com/watch?v=abc123",
    "video_id": "abc123",
    "transcription": "Transcrição completa do conteúdo do vídeo...",
    "focal_keywords": ["palavra-chave1", "palavra-chave2", "palavra-chave3"],
    "current_metadata": {
      "title": "Título Atual",
      "description": "Descrição atual",
      "tags": ["tag1", "tag2"]
    }
  },
  "ai_generation": {
    "generated_title": "Título Otimizado para SEO",
    "generated_description": "Descrição otimizada com links de afiliados...",
    "generated_tags": ["tag1", "tag2", "tag3"],
    "generated_hashtags": ["#hashtag1", "#hashtag2"],
    "generated_cta": "Call-to-action otimizado",
    "seo_score": 0.95,
    "processing_status": "success"
  },
  "promotional_links": {
    "affiliate_links": [
      "https://afiliado1.com/produto",
      "https://afiliado2.com/curso"
    ],
    "course_references": ["https://curso1.com", "https://curso2.com"],
    "document_sources": ["documento_referencia.pdf"]
  },
  "youtube_update": {
    "update_status": "completed",
    "updated_fields": ["title", "description", "tags", "hashtags"],
    "api_response": "success",
    "update_timestamp": "2025-01-15T11:00:00Z"
  }
}
```

## Casos de Uso

- **Otimização de SEO:** Geração automática de títulos e descrições otimizados para mecanismos de busca
- **Gestão de Conteúdo:** Atualização em massa de metadados de múltiplos vídeos
- **Marketing de Afiliados:** Incorporação automática de links promocionais relevantes
- **Padronização:** Manutenção de consistência na qualidade dos metadados
- **Escalabilidade:** Processamento automatizado para canais com muitos vídeos
- **A/B Testing:** Geração de múltiplas versões de metadados para teste de performance
- **Compliance:** Garantia de que todos os vídeos seguem padrões de qualidade

## Dependências

- Acesso configurado à YouTube Data API v3 com permissões adequadas
- Modelo de IA configurado para geração de metadados otimizados
- Sistema de formulários web para coleta de dados
- Base de dados de links promocionais e afiliados
- Documento de referência com links relevantes
- Capacidade de processamento de transcrições de vídeo

## Estrutura do Workflow

1. **Web Form Trigger** - Coleta dados do vídeo via formulário
2. **Promotional Links Query** - Consulta links de afiliados e referências
3. **AI Metadata Generation** - Gera metadados otimizados usando IA
4. **Output Validation** - Valida e estrutura a saída da IA
5. **Video ID Extraction** - Extrai ID do vídeo do link
6. **Tag Formatting** - Formata tags para envio à API
7. **YouTube API Update** - Atualiza metadados do vídeo
8. **User Confirmation** - Confirma conclusão do processamento

## Monitoramento

- **Vídeos Processados:** Total de vídeos com metadados atualizados
- **Taxa de Sucesso:** Percentual de atualizações bem-sucedidas
- **Tempo de Processamento:** Latência média por vídeo
- **Qualidade dos Metadados:** Score de otimização SEO gerado
- **Performance da API:** Tempo de resposta da YouTube API
- **Links Incorporados:** Total de links promocionais adicionados
- **Erros de Atualização:** Falhas na atualização e tipos de erro

## Tratamento de Erros

- **Falha na Geração IA:** Fallback para metadados padrão com notificação
- **Erro de API YouTube:** Retry automático com notificação de falha
- **Link Inválido:** Validação e skip de links corrompidos
- **Transcrição Vazia:** Notificação de erro e processamento manual
- **Permissões Insuficientes:** Log de erro e notificação administrativa
- **Timeout de Processamento:** Cancelamento e notificação de falha
- **Formato de Dados Inválido:** Validação e correção automática

## Características Técnicas

### Geração Inteligente de Metadados

- **Modelo de Linguagem:** Utiliza IA para criação de conteúdo otimizado
- **SEO Optimization:** Foco em palavras-chave e estrutura otimizada
- **Personalização Contextual:** Adapta metadados ao conteúdo específico
- **Consistência de Marca:** Mantém padrões de comunicação

### Integração YouTube

- **API v3:** Utiliza a versão mais recente da YouTube Data API
- **Atualização em Tempo Real:** Modifica metadados instantaneamente
- **Validação de Campos:** Verifica formato e limites da plataforma
- **Tratamento de Erros:** Gerenciamento robusto de falhas de API

### Sistema de Links Promocionais

- **Base de Dados Centralizada:** Gestão organizada de links afiliados
- **Relevância Contextual:** Seleção inteligente baseada no conteúdo
- **Rastreamento de Performance:** Monitoramento de cliques e conversões
- **Atualização Automática:** Sincronização com sistemas externos

### Automação Inteligente

- **Processamento em Lote:** Capacidade de múltiplos vídeos
- **Validação Automática:** Verificação de qualidade dos metadados
- **Fallback Inteligente:** Alternativas em caso de falha
- **Logging Completo:** Registro detalhado de todas as operações

---

_Autor: Matheus Freitas_  
_Categoria: Marketing_  
_Versão: 1.0_
