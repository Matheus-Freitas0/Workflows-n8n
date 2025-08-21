# 🎓 Tutor Alunos - Enviar Dados

## Descrição

Sistema automatizado de tutoria para alunos que processa arquivos PDF de exercícios Python, extrai conteúdo e armazena em banco de dados vetorial Pinecone para consultas inteligentes.

## Funcionalidades

- **Trigger:** Execução manual
- **Integração:** Google Drive, OpenAI Embeddings, Pinecone Vector Store
- **Processamento:** Extração de PDFs, geração de embeddings, armazenamento vetorial
- **Saída:** Dados estruturados no Pinecone para consultas RAG

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                    |
| --------- | ------ | ---------------------------- |
| `manual`  | trigger| Execução manual do workflow |

## Como Funciona

1. **Download:** Arquivo PDF é baixado do Google Drive
2. **Processamento:** PDF é convertido em texto estruturado
3. **Embeddings:** OpenAI gera embeddings do conteúdo
4. **Armazenamento:** Dados são salvos no Pinecone Vector Store
5. **Indexação:** Conteúdo fica disponível para consultas RAG

## Configuração

### Credenciais Necessárias

- **Google Drive OAuth2:** Acesso ao Google Drive
- **OpenAI API:** Chave de API para embeddings
- **Pinecone API:** Chave de API para vector store

### Estrutura de Dados

```json
{
  "fileId": "ID do arquivo no Google Drive",
  "content": "Conteúdo extraído do PDF",
  "embeddings": "Vetores gerados pela OpenAI"
}
```

## Casos de Uso

- Processamento de materiais educacionais
- Criação de base de conhecimento para tutoria
- Sistema de consulta inteligente para alunos
- Automação de preparação de conteúdo educacional

## Dependências

- Credenciais Google Drive configuradas
- API OpenAI configurada
- Pinecone Vector Store configurado
- Arquivos PDF disponíveis no Drive

## Estrutura do Workflow

1. **Manual Trigger** - Inicia o workflow
2. **Google Drive** - Download do arquivo PDF
3. **Document Loader** - Processamento do PDF
4. **OpenAI Embeddings** - Geração de vetores
5. **Pinecone Vector Store** - Armazenamento dos dados

## Monitoramento

- Verificar execuções através do histórico do n8n
- Monitorar uso das APIs OpenAI e Pinecone
- Acompanhar processamento de arquivos
- Validar qualidade dos embeddings gerados

## Tratamento de Erros

- Validação do arquivo PDF
- Tratamento de falhas na API OpenAI
- Fallback para processamento manual
- Logs de execução para debugging

## Configuração do Pinecone

- **Index:** teste-n8n
- **Namespace:** exerciciospython
- **Dimensão:** Conforme configuração OpenAI

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
