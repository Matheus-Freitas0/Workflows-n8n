# 📱 Agente Catálogo de Produtos WhatsApp

## Descrição

Agente automatizado para processar catálogo de produtos via WhatsApp. Este workflow recebe mensagens, extrai URLs de produtos, realiza web scraping e armazena dados em planilha do Google.

## Funcionalidades

- **Trigger:** Webhook do WhatsApp
- **Validação:** Apenas números autorizados (contém "0404")
- **Extração:** URLs de produtos das mensagens
- **Web Scraping:** Coleta dados de páginas de produtos
- **Processamento:** Imagens principais e texto limpo
- **Armazenamento:** Google Sheets com dados estruturados
- **Comandos:** Suporte a comandos especiais (DB:)

## Como Funciona

### Fluxo Principal

1. **Recebimento:** Webhook recebe mensagens do WhatsApp
2. **Validação:** Verifica se número está autorizado
3. **Processamento:** Identifica tipo de comando
4. **Extração:** Localiza URLs de produtos
5. **Scraping:** Acessa páginas para extrair dados
6. **Processamento:** Limpa HTML e extrai imagens
7. **Armazenamento:** Salva na planilha do Google

### Comandos Especiais

- **DB:** Inicia modo de inserção manual de dados
- **Automático:** Processa URLs automaticamente

## Estrutura do Workflow

1. **Webhook** - Recebe mensagens do WhatsApp
2. **Extraindo Dados** - Mapeia campos da mensagem
3. **Verifica Numero** - Valida autorização
4. **Switch** - Direciona fluxo por comando
5. **Extrair URL** - Identifica URLs de produtos
6. **Web Scraping** - Coleta dados das páginas
7. **Encontrar URL da Imagem** - Localiza imagem principal
8. **Remocao das Tags** - Limpa HTML
9. **Google Sheets** - Armazena dados

## Configuração

### Credenciais Necessárias

- **WhatsApp Webhook:** Configurado para receber mensagens
- **Google Sheets:** OAuth2 configurado no n8n
- **Internet:** Acesso para web scraping

### Webhook WhatsApp

- **ID:** 0e2af9f0-2509-4d72-9d15-c353d89423db
- **Método:** POST
- **Formato:** Mensagens do WhatsApp

### Planilha Google Sheets

- **ID:** 1MrMPDg8ohEbkrI_5hnT41f2ua_pZxhG1a0RVeoJLdwI
- **Nome:** Produtos WhatsApp
- **Colunas:** Link, Texto, Imagem

## Dados Processados

| Campo | Descrição | Fonte |
|-------|-----------|-------|
| **Link** | URL do produto | Extraído da mensagem |
| **Texto** | Conteúdo da página | Web scraping + limpeza |
| **Imagem** | URL da imagem principal | Extraída da página |

## Validação de Números

- **Autorizados:** Números que contêm "0404"
- **Bloqueados:** Outros números são ignorados
- **Segurança:** Controle de acesso por número

## Web Scraping

### Sites Suportados

- **Amazon:** Extração otimizada para landingImage
- **Outros:** Suporte genérico para qualquer site
- **Fallbacks:** Múltiplas estratégias de extração

### Estratégias de Extração

1. **data-a-dynamic-image:** Melhor resolução (Amazon)
2. **data-old-hires:** Resolução alta (Amazon)
3. **src:** Fallback padrão

## Limpeza de Dados

### Processo de Limpeza

1. **Remove Scripts:** Elimina código JavaScript
2. **Remove Styles:** Elimina CSS
3. **Remove Tags:** Remove todas as tags HTML
4. **Entidades HTML:** Converte &quot; etc.
5. **Normalização:** Remove espaços múltiplos

### Limite de Texto

- **Máximo:** 40.000 caracteres
- **Otimização:** Para análise e armazenamento

## Casos de Uso

- **Catálogo Automático:** Produtos processados automaticamente
- **Monitoramento de Preços:** Acompanhamento de mudanças
- **Análise de Produtos:** Dados estruturados para análise
- **E-commerce:** Integração com sistemas de vendas
- **Pesquisa:** Base de dados de produtos

## Dependências

- Webhook do WhatsApp configurado
- Credenciais do Google Sheets configuradas
- Acesso à internet para web scraping
- Planilha do Google configurada
- Números autorizados configurados

## Monitoramento

- Verificar execuções do workflow
- Monitorar mensagens recebidas
- Acompanhar dados extraídos
- Verificar armazenamento na planilha

## Tratamento de Erros

- **URLs Inválidas:** Mensagem de erro retornada
- **Falha no Scraping:** Log de erro registrado
- **Planilha Indisponível:** Retry automático
- **Timeout:** Configuração de timeouts

## Otimizações

- **Cache:** Evitar re-scraping de URLs
- **Rate Limiting:** Respeitar limites dos sites
- **Paralelização:** Processar múltiplos produtos
- **Filtros:** Configurar sites permitidos

## Segurança

- **Validação de URLs:** Verificar domínios permitidos
- **Sanitização:** Limpeza de dados de entrada
- **Rate Limiting:** Proteção contra spam
- **Logs:** Auditoria de todas as operações

---
*Autor: Matheus Freitas*  
*Categoria: WhatsApp*  
*Versão: 1.0*
