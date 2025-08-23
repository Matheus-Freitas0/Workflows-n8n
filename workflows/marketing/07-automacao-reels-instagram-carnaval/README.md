# 🎭 Automação de Reels do Instagram para Carnaval

## Descrição

Fluxo que coleta reels, analisa métricas, cria scripts e captions, e registra resultados no Airtable, com integração via Telegram. Especialmente focado em conteúdo relacionado ao Carnaval, este workflow automatiza todo o processo de análise e criação de conteúdo para redes sociais.

## Funcionalidades

- **Coleta de Reels do Instagram a partir do Airtable:** Busca registros para processamento
- **Análise de Reels com modelos de linguagem:** Extrai insights e métricas relevantes
- **Repurpose de conteúdo:** Geração de script e caption para os reels
- **Obtenção de dados de usuários/competidores:** Consulta de perfis e informações via API externa
- **Cálculo de engajamento:** Calcula percentuais com base em visualizações, compartilhamentos, etc.
- **Geração de URLs de perfis:** Criação de links diretos para usuários
- **Armazenamento/Atualização no Airtable:** Grava reels, scripts, captions e dados de competidores
- **Preparação de conteúdos para envio via Telegram:** Notificações e inputs durante o fluxo

## Parâmetros de Entrada

| Parâmetro  | Tipo   | Descrição                   |
| ---------- | ------ | --------------------------- |
| `trigger`  | manual | Trigger manual para iniciar |
| `airtable` | object | Dados dos reels do Airtable |

## Como Funciona

1. **Trigger:** Inicia o fluxo via trigger manual
2. **Coleta:** Busca reels do Instagram no Airtable para processamento
3. **Análise IA:** Usa modelos de linguagem para extrair insights dos reels
4. **Processamento:** Calcula métricas de engajamento e gera scripts/captions
5. **Competidores:** Coleta dados de usuários e perfis via API externa
6. **Consolidação:** Prepara todos os dados para armazenamento
7. **Airtable:** Atualiza registros com novos dados processados
8. **Telegram:** Envia notificações e permite inputs durante o processo

## Configuração

### Credenciais Necessárias

- **Instagram:** Acesso à API do Instagram (se aplicável)
- **Airtable:** API key e base configurada
- **Telegram:** Bot token configurado
- **Modelo de IA:** Credenciais para análise de linguagem natural

### Estrutura de Dados

```json
{
  "reelData": {
    "id": "string",
    "url": "string",
    "caption": "string",
    "metrics": {
      "views": "number",
      "likes": "number",
      "shares": "number",
      "engagement": "number"
    }
  },
  "generatedContent": {
    "script": "string",
    "caption": "string",
    "insights": "string"
  },
  "competitorData": {
    "profileUrl": "string",
    "metrics": "object"
  }
}
```

## Casos de Uso

- Análise automática de reels de Carnaval
- Criação de conteúdo baseado em tendências
- Monitoramento de competidores durante eventos sazonais
- Geração automática de scripts para novos reels
- Tracking de performance de conteúdo temático

## Dependências

- Airtable configurado com dados dos reels
- API do Instagram funcional
- Bot do Telegram configurado
- Modelo de IA para análise de linguagem
- Credenciais válidas para todos os serviços

## Estrutura do Workflow

1. **Trigger Manual** - Início do fluxo
2. **Airtable** - Coleta de reels para processamento
3. **Análise IA** - Processamento com modelos de linguagem
4. **Cálculo Métricas** - Análise de engajamento
5. **API Externa** - Coleta de dados de competidores
6. **Geração Conteúdo** - Criação de scripts e captions
7. **Atualização Airtable** - Armazenamento dos resultados
8. **Telegram** - Notificações e interação

## Monitoramento

- Status de processamento dos reels
- Qualidade dos scripts e captions gerados
- Métricas de engajamento calculadas
- Logs de erros de API
- Notificações via Telegram

## Tratamento de Erros

- Falha na coleta de dados do Airtable
- Erro na análise com modelos de IA
- Problemas de conectividade com APIs
- Falha na geração de conteúdo
- Erro na atualização do Airtable

---

_Autor: Matheus Freitas_  
_Categoria: Marketing_  
_Versão: 1.0_  
_Numeração: 07_
