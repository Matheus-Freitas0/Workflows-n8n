# 📢 Publicação Automática de Posts no Instagram

## Descrição

Sistema automatizado que seleciona a próxima ideia de post de uma planilha, gera conceito, prompts de imagem e legenda com modelos de IA, cria a imagem e publica no Instagram, atualizando o status do item.

## Funcionalidades

- **Trigger:** Execução automática conforme cronograma definido
- **Integração:** IA para geração de conteúdo, Instagram API, planilhas
- **Processamento:** Geração automática de conceitos, prompts e legendas
- **Saída:** Post publicado no Instagram com imagem gerada por IA

## Parâmetros de Entrada

| Parâmetro    | Tipo   | Descrição                                    |
| ------------ | ------ | -------------------------------------------- |
| `planilha`   | object | Planilha com ideias de posts (Status = 0)   |
| `topic`      | string | Tópico principal do post                     |
| `audience`   | string | Público-alvo definido                        |
| `voice`      | string | Tom de comunicação                           |
| `platform`   | string | Plataforma (Instagram)                       |

## Como Funciona

1. **Agendamento:** Executa o fluxo automaticamente conforme cronograma definido
2. **Leitura de Ideias:** Busca a próxima ideia com Status = 0 em uma planilha para processar
3. **Preparação de Variáveis:** Extrai e organiza Topic, Audience, Voice e Platform para uso nas etapas de geração
4. **Geração de Conceito Criativo:** Usa um modelo de linguagem para criar exatamente um conceito de post (formato fixo: Single Image) adaptado à plataforma
5. **Elaboração de Prompts de Imagem:** Expande o conceito e produz duas opções detalhadas de prompt otimizadas para geradores de imagem
6. **Geração de Legenda:** Cria uma legenda curta e adequada ao público e à plataforma, incluindo hashtags relevantes
7. **Criação de Imagem:** Envia o prompt selecionado a um serviço de geração de imagens e obtém a imagem final
8. **Publicação no Instagram:** Prepara os dados, cria um container de mídia, aguarda processamento e publica o post na conta conectada
9. **Atualização de Status:** Marca a ideia como processada na planilha (Status = 1) para evitar reprocessamento futuro

## Configuração

### Credenciais Necessárias

- **Instagram:** API credentials para publicação de posts
- **IA:** Modelo de linguagem configurado para geração de conteúdo
- **Geração de Imagem:** Serviço de IA para criação de imagens
- **Planilha:** Acesso a planilha com ideias de posts

### Estrutura de Dados

```json
{
  "post_idea": {
    "topic": "Dicas de produtividade",
    "audience": "Profissionais",
    "voice": "Motivacional",
    "platform": "Instagram",
    "status": 0
  },
  "generated_content": {
    "concept": "Single Image - Dicas visuais de produtividade",
    "image_prompts": [
      "Prompt detalhado 1 para geração de imagem",
      "Prompt detalhado 2 para geração de imagem"
    ],
    "caption": "Legenda com hashtags relevantes #produtividade #dicas",
    "selected_prompt": "Prompt selecionado para geração"
  },
  "instagram_post": {
    "image_url": "URL da imagem gerada",
    "caption": "Legenda final",
    "status": "published"
  }
}
```

## Casos de Uso

- **Marketing Digital:** Automação de conteúdo para redes sociais
- **Influenciadores:** Geração automática de posts consistentes
- **Empresas:** Manutenção de presença ativa no Instagram
- **Agências:** Gerenciamento de múltiplas contas de clientes
- **Conteúdo:** Criação de posts baseados em ideias pré-definidas

## Dependências

- Conta Instagram Business configurada
- API do Instagram funcionando
- Modelo de IA para geração de conteúdo
- Serviço de geração de imagens por IA
- Planilha com ideias de posts estruturadas
- Cronograma de execução configurado

## Estrutura do Workflow

1. **Schedule Trigger** - Execução automática conforme cronograma
2. **Spreadsheet Read** - Leitura da próxima ideia com Status = 0
3. **Variable Preparation** - Organização de Topic, Audience, Voice e Platform
4. **AI Concept Generation** - Geração de conceito criativo adaptado
5. **Image Prompt Creation** - Criação de dois prompts detalhados para imagem
6. **Caption Generation** - Geração de legenda com hashtags
7. **Image Creation** - Geração da imagem usando IA
8. **Instagram Publishing** - Publicação do post na conta conectada
9. **Status Update** - Atualização do status na planilha

## Monitoramento

- **Posts Gerados:** Contagem de posts criados automaticamente
- **Taxa de Sucesso:** Percentual de posts publicados com sucesso
- **Qualidade IA:** Feedback sobre conceitos e legendas gerados
- **Geração de Imagens:** Sucesso na criação de imagens por IA
- **API Instagram:** Status das publicações e erros
- **Tempo de Processamento:** Duração total do workflow

## Tratamento de Erros

- **Planilha Vazia:** Notificação de que não há ideias para processar
- **Falha IA:** Fallback para templates de conteúdo padrão
- **Erro Geração Imagem:** Retry com prompt alternativo
- **Falha Instagram API:** Retry com backoff exponencial
- **Timeout:** Cancelamento de operações longas
- **Validação:** Verificação de dados antes da publicação

## Características Técnicas

### Sistema de Agendamento
- **Cronograma:** Configurável para execução automática
- **Frequência:** Definível (diário, semanal, etc.)
- **Horários:** Otimizados para melhor engajamento

### Geração de Conteúdo IA
- **Modelo:** Configurável (GPT, Claude, etc.)
- **Formato:** Single Image (formato fixo)
- **Adaptação:** Conteúdo adaptado à plataforma Instagram
- **Tom:** Consistente com voice definido

### Criação de Imagens
- **Serviço:** IA para geração de imagens
- **Prompts:** Dois prompts detalhados por post
- **Otimização:** Prompts otimizados para geradores de imagem
- **Qualidade:** Imagens de alta resolução para Instagram

### Gestão de Planilha
- **Status Tracking:** Controle de posts processados
- **Evitar Duplicação:** Status = 1 após processamento
- **Estrutura:** Campos organizados (Topic, Audience, Voice, Platform)
- **Sincronização:** Atualização automática de status

### Integração Instagram
- **API:** Publicação via Instagram Graph API
- **Container de Mídia:** Criação e processamento
- **Aguardar Processamento:** Validação antes da publicação
- **Status de Publicação:** Confirmação de sucesso

### Segurança e Controle
- **Validação:** Verificação de dados antes da publicação
- **Logs:** Auditoria completa de todas as ações
- **Fallbacks:** Mecanismos de recuperação para falhas
- **Rate Limiting:** Respeito aos limites da API do Instagram

---

_Autor: Matheus Freitas_  
_Categoria: Marketing_  
_Versão: 1.0_
