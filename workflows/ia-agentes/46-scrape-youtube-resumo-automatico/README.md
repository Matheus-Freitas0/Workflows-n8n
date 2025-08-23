# 🎥 Scrape YouTube e Resumo Automático

## Descrição

Este fluxo usa a API Apify para extrair transcrições de vídeos do YouTube, inicia uma execução de ator para processar o vídeo, gera resumos com um modelo de linguagem, divide a transcrição em seções com timestamps e prepara os dados de saída para armazenamento e uso posterior.

## Funcionalidades

- **Integração com Apify:** Busca a execução do ator e os dados do dataset para o vídeo
- **Definição de entrada:** Recebe a URL do vídeo para processar
- **Início de ator:** Inicia a execução do ator Apify com a URL do vídeo
- **Extração de transcrição:** Obtém a transcrição a partir do dataset
- **Resumo do vídeo:** Gera um resumo do conteúdo do vídeo
- **Timestamps e resumo da transcrição:** Divide a transcrição em seções com timestamps e produz um resumo por trecho
- **Preparação de saída:** Consolida ID, resumo de vídeo, resumo da transcrição e a transcrição completa
- **Preparação de input para banco de dados:** Estrutura os dados para atualização em Airtable ou similar
- **Teste rápido:** Permite testar o fluxo via trigger manual

## Parâmetros de Entrada

| Parâmetro  | Tipo   | Descrição               |
| ---------- | ------ | ----------------------- |
| `videoUrl` | string | URL do vídeo do YouTube |

## Como Funciona

1. **Trigger:** Recebe URL do vídeo via trigger manual ou webhook
2. **Inicialização Apify:** Inicia execução do ator Apify com a URL fornecida
3. **Extração:** Aguarda conclusão e extrai dados do dataset
4. **Processamento IA:** Gera resumos usando modelo de linguagem
5. **Segmentação:** Divide transcrição em seções com timestamps
6. **Consolidação:** Prepara dados estruturados para saída
7. **Armazenamento:** Estrutura dados para banco de dados

## Configuração

### Credenciais Necessárias

- **Apify:** Token de API configurado no n8n
- **Modelo de IA:** Credenciais para geração de resumos

### Estrutura de Dados

```json
{
  "videoId": "string",
  "videoUrl": "string",
  "videoSummary": "string",
  "transcriptSections": [
    {
      "timestamp": "string",
      "text": "string",
      "summary": "string"
    }
  ],
  "fullTranscript": "string"
}
```

## Casos de Uso

- Análise de conteúdo de vídeos educacionais
- Criação de resumos automáticos para pesquisa
- Extração de insights de vídeos longos
- Preparação de dados para análise de conteúdo
- Criação de índices com timestamps para vídeos

## Dependências

- API Apify configurada e funcional
- Modelo de IA para geração de resumos
- Acesso ao dataset do Apify
- Credenciais válidas para todos os serviços

## Estrutura do Workflow

1. **Trigger Manual** - Início do fluxo
2. **Apify Actor** - Inicialização da execução
3. **Apify Dataset** - Extração de dados
4. **Processamento IA** - Geração de resumos
5. **Segmentação** - Divisão por timestamps
6. **Consolidação** - Preparação de saída

## Monitoramento

- Status de execução do ator Apify
- Tempo de processamento do vídeo
- Qualidade dos resumos gerados
- Logs de erros de extração

## Tratamento de Erros

- Timeout na execução do ator
- Falha na extração de dados
- Erro na geração de resumos
- Problemas de conectividade com APIs

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
