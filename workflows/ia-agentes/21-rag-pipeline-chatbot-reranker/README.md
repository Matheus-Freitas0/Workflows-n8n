# 🔍 RAG Pipeline & Chatbot com Reranker

## Descrição

Sistema avançado de RAG (Retrieval-Augmented Generation) com pipeline automatizado, chatbot inteligente e reranker para melhorar a qualidade das respostas baseadas em documentos.

## Funcionalidades

- **Trigger:** Google Drive file creation
- **Integração:** Google Drive, Supabase Vector Store, OpenAI, Reranker
- **Processamento:** Pipeline RAG completo com reranking
- **Saída:** Chatbot inteligente com respostas baseadas em documentos

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                    |
| --------- | ------ | ---------------------------- |
| `fileId`  | string | ID do arquivo criado no Drive |

## Como Funciona

1. **Monitoramento:** Google Drive trigger detecta novos arquivos
2. **Download:** Arquivo é baixado automaticamente
3. **Processamento:** Conteúdo é processado e vetorizado
4. **Armazenamento:** Dados são salvos no Supabase Vector Store
5. **Reranking:** Sistema reranker melhora qualidade das consultas
6. **Chatbot:** Interface de chat para consultas aos documentos

## Configuração

### Credenciais Necessárias

- **Google Drive OAuth2:** Acesso ao Google Drive
- **Supabase API:** Chave de API para vector store
- **OpenAI API:** Chave de API para processamento
- **Reranker API:** Chave de API para reranking

### Estrutura de Dados

```json
{
  "fileId": "ID do arquivo no Google Drive",
  "content": "Conteúdo processado do arquivo",
  "embeddings": "Vetores para busca semântica",
  "metadata": "Informações do documento"
}
```

## Casos de Uso

- Sistema de FAQ automatizado
- Chatbot para suporte ao cliente
- Base de conhecimento inteligente
- Consultas a documentos corporativos
- Sistema de busca semântica avançada

## Dependências

- Credenciais Google Drive configuradas
- Supabase Vector Store configurado
- API OpenAI configurada
- Sistema de reranking configurado
- Pasta FAQ configurada no Drive

## Estrutura do Workflow

1. **Google Drive Trigger** - Monitora criação de arquivos
2. **Download File** - Baixa arquivo automaticamente
3. **Document Processing** - Processa conteúdo do arquivo
4. **Vector Store** - Armazena no Supabase
5. **Reranker** - Melhora qualidade das consultas
6. **Chatbot Interface** - Interface de usuário

## Monitoramento

- Verificar execuções através do histórico do n8n
- Monitorar processamento de arquivos
- Acompanhar qualidade das respostas do chatbot
- Validar performance do reranker

## Tratamento de Erros

- Validação de tipos de arquivo
- Tratamento de falhas no processamento
- Fallback para busca sem reranker
- Logs de execução para debugging

## Configuração do Supabase

- **Table:** faq_documents
- **Query:** match_documents
- **Vector Dimension:** Conforme configuração OpenAI

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
