# 📢 Publicador Social Automático WordPress

## Descrição

Workflow automatizado que cria e publica captions e imagens para múltiplas redes sociais baseado em posts do WordPress. Utiliza modelos de IA para gerar conteúdo otimizado e adaptado para cada plataforma, respeitando os limites de caracteres e tom apropriado.

## Funcionalidades

- **Leitura de Google Sheets:** Busca o ID do post WordPress a processar em uma planilha do Google Sheets
- **Recuperação de Post WordPress:** Obtém título, conteúdo e link do artigo WordPress especificado
- **Geração de Captions com IA:** Cria textos otimizados e adaptados para LinkedIn, Instagram, Facebook e Twitter (X), respeitando o tom e limites de caracteres de cada plataforma
- **Parser de Saída Estruturada:** Transforma a resposta do modelo de IA em campos separados por plataforma
- **Geração de Imagens com IA:** Cria imagens específicas para Instagram, Facebook e LinkedIn com tamanhos apropriados para cada plataforma
- **Publicação Automática:** Envia posts com texto e imagens para Twitter (X), LinkedIn, Facebook e Instagram via suas respectivas APIs
- **Atualização de Planilha:** Marca, por linha na planilha, quais plataformas foram publicadas com sucesso

## Parâmetros de Entrada

| Parâmetro           | Tipo   | Descrição                               |
| ------------------- | ------ | --------------------------------------- |
| `wordpress_post_id` | string | ID do post WordPress a ser processado   |
| `google_sheet_id`   | string | ID da planilha Google Sheets            |
| `ai_model`          | string | Modelo de IA para geração de conteúdo   |
| `social_platforms`  | array  | Lista de plataformas sociais a publicar |

## Como Funciona

### 1. **Leitura de Dados**

- Acessa Google Sheets para obter ID do post WordPress
- Recupera dados completos do post (título, conteúdo, link)

### 2. **Processamento com IA**

- Gera captions otimizados para cada plataforma social
- Cria imagens personalizadas com dimensões específicas
- Adapta conteúdo para limites de caracteres de cada rede

### 3. **Publicação Automática**

- Envia conteúdo para Twitter (X), LinkedIn, Facebook e Instagram
- Utiliza APIs nativas de cada plataforma
- Gerencia credenciais e autenticação

### 4. **Controle e Monitoramento**

- Atualiza planilha com status de publicação
- Registra sucessos e falhas por plataforma
- Mantém histórico de execuções

## Configuração

### Credenciais Necessárias

- **WordPress:** Acesso à API REST do WordPress
- **Google Sheets:** Credenciais de API do Google
- **Twitter (X):** API keys e tokens de acesso
- **LinkedIn:** Credenciais de API do LinkedIn
- **Facebook:** Tokens de acesso e app ID
- **Instagram:** Credenciais de API do Instagram
- **IA:** Chave de API para modelo de IA (OpenAI, Claude, etc.)

### Estrutura da Planilha Google Sheets

```csv
Post ID | Título | Status Twitter | Status LinkedIn | Status Facebook | Status Instagram | Data Publicação
123     | Exemplo| Publicado      | Publicado       | Publicado       | Publicado        | 2025-01-15
```

### Configurações de Plataforma

```json
{
  "twitter": {
    "character_limit": 280,
    "image_dimensions": "1200x675"
  },
  "linkedin": {
    "character_limit": 3000,
    "image_dimensions": "1200x627"
  },
  "facebook": {
    "character_limit": 63206,
    "image_dimensions": "1200x630"
  },
  "instagram": {
    "character_limit": 2200,
    "image_dimensions": "1080x1080"
  }
}
```

## Casos de Uso

- **Marketing Digital:** Publicação automática de conteúdo corporativo
- **Blogs e Sites:** Distribuição automática de artigos para redes sociais
- **E-commerce:** Promoção automática de produtos e ofertas
- **Conteúdo Educativo:** Compartilhamento de tutoriais e guias
- **Notícias:** Distribuição de artigos jornalísticos

## Dependências

- WordPress configurado com API REST ativa
- Planilha Google Sheets com estrutura adequada
- Contas ativas nas plataformas sociais
- API keys configuradas para todos os serviços
- Modelo de IA configurado e funcional

## Estrutura do Workflow

### Nós Principais

1. **Google Sheets** - Leitura de dados da planilha
2. **WordPress** - Recuperação de posts
3. **IA Model** - Geração de conteúdo e imagens
4. **Parser** - Estruturação de dados por plataforma
5. **Social Media APIs** - Publicação nas redes sociais
6. **Google Sheets Update** - Atualização de status

### Fluxo de Execução

```
Google Sheets → WordPress → IA Generation → Content Parsing → Social Publishing → Status Update
```

## Monitoramento

- **Logs de Execução:** Acompanhar publicações via n8n
- **Status por Plataforma:** Verificar sucesso/falha de cada rede
- **Métricas de Performance:** Tempo de execução e taxa de sucesso
- **Histórico de Publicações:** Rastrear conteúdo publicado

## Tratamento de Erros

- **Falhas de API:** Retry automático com backoff exponencial
- **Limites de Caracteres:** Validação prévia de conteúdo
- **Rate Limiting:** Respeito aos limites das APIs sociais
- **Falhas de Autenticação:** Alertas para credenciais expiradas

## Implementação Técnica

- **Processamento Assíncrono:** Publicação paralela em múltiplas plataformas
- **Cache de Conteúdo:** Evita regeneração desnecessária de conteúdo
- **Validação de Dados:** Verificação de integridade antes da publicação
- **Logs Estruturados:** Rastreamento detalhado de execuções

## Personalização

- **Templates de Caption:** Estilos personalizáveis por plataforma
- **Configuração de IA:** Parâmetros ajustáveis para geração de conteúdo
- **Horários de Publicação:** Agendamento flexível de execuções
- **Filtros de Conteúdo:** Regras para seleção de posts a publicar

---

_Autor: Matheus Freitas_  
_Categoria: Marketing_  
_Versão: 1.0_
