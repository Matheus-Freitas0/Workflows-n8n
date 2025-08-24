# 📧 Processamento de Emails com Busca Vetorial e Chat

## Descrição

Este fluxo lê mensagens do Outlook, cria embeddings, armazena em vetores em Postgres PGVector e Pinecone, e usa um agente de linguagem para responder perguntas com base no conteúdo indexado, acionando pela mensagem recebida via chat.

## Funcionalidades

- **Inicia a automação ao acionar o workflow manualmente:** trigger manual para processamento de emails
- **Busca emails no Outlook recebidos após uma data específica:** consulta emails do Microsoft Outlook
- **Constrói payload com metadados do email:** Data recebida, Remetente, Assunto, ID da mensagem, Corpo
- **Gera embeddings com OpenAI e armazena nos vetores do Postgres PGVector e do Pinecone:** processamento de IA para busca vetorial
- **Processa conteúdo com modelos de linguagem via um agente LangChain para responder a perguntas com base no conteúdo indexado:** agente de IA para consultas
- **Habilita chat com gatilho para receber mensagens e consultar a memória de chat:** interface de chat com memória persistente

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                                                      |
| --------- | ------ | -------------------------------------------------------------- |
| `date`    | string | Data de início para busca de emails (ex: 2024-10-29T01:00:00Z) |
| `message` | string | Mensagem de chat para consulta ao conteúdo indexado            |

## Como Funciona

1. **Trigger Manual:** Inicia o workflow para processamento de emails
2. **Leitura Outlook:** Busca emails recebidos após data específica
3. **Processamento de Metadados:** Extrai e estrutura informações dos emails
4. **Geração de Embeddings:** OpenAI cria representações vetoriais do conteúdo
5. **Armazenamento Vetorial:** Salva embeddings no Postgres PGVector e Pinecone
6. **Agente de IA:** Processa consultas via chat usando busca vetorial
7. **Memória de Chat:** Mantém histórico de conversas no PostgreSQL

## Configuração

### Credenciais Necessárias

- **Microsoft Outlook:** Para acesso aos emails
- **OpenAI API:** Para geração de embeddings e processamento de linguagem
- **PostgreSQL com PGVector:** Para armazenamento de vetores
- **Pinecone:** Para armazenamento adicional de vetores

### Estrutura de Dados

```json
{
  "email_metadata": {
    "received_date": "2024-10-29T01:00:00Z",
    "subject": "Assunto do email",
    "from": "remetente@email.com",
    "message_id": "ID único da mensagem",
    "body": "Conteúdo do email"
  },
  "vector_storage": {
    "postgres_collection": "email_documents",
    "pinecone_index": "email_vectors"
  }
}
```

## Casos de Uso

- **Assistente de Email:** Consulta inteligente sobre histórico de emails
- **Busca Semântica:** Encontrar emails por significado, não apenas palavras-chave
- **Análise de Conteúdo:** Extrair insights de conversas por email
- **Suporte ao Cliente:** Acesso rápido a informações de emails anteriores
- **Pesquisa Corporativa:** Busca em base de conhecimento de emails

## Dependências

- Microsoft Outlook configurado
- OpenAI API para embeddings e processamento de linguagem
- PostgreSQL com extensão PGVector
- Pinecone para armazenamento de vetores
- Sistema de chat para interface de usuário

## Estrutura do Workflow

1. **When clicking 'Test workflow'** - Trigger manual para processamento
2. **Microsoft Outlook** - Busca emails após data específica
3. **Set Payload** - Estrutura metadados dos emails
4. **Embeddings OpenAI** - Gera representações vetoriais
5. **Default Data Loader** - Carrega documentos para processamento
6. **Recursive Character Text Splitter** - Divide texto em chunks
7. **Postgres PGVector Store** - Armazena vetores no PostgreSQL
8. **Pinecone Vector Store** - Armazena vetores no Pinecone
9. **AI Agent** - Agente de IA para consultas
10. **Vector Store Tool** - Ferramenta de busca vetorial
11. **Postgres Chat Memory** - Memória persistente de chat
12. **When chat message received** - Trigger de chat para consultas

## Monitoramento

- Logs de processamento de emails
- Status de geração de embeddings
- Performance de armazenamento vetorial
- Métricas de uso do agente de IA
- Monitoramento de memória de chat

## Tratamento de Erros

- Validação de credenciais do Outlook
- Tratamento de falhas na geração de embeddings
- Fallback para armazenamento em caso de erro
- Logs de debugging para troubleshooting
- Validação de dados de entrada

## Configurações Avançadas

### Modelos de IA

- **Embeddings:** text-embedding-3-small para representações vetoriais
- **Chat:** GPT-4o para processamento de linguagem natural
- **Agente:** LangChain para coordenação de ferramentas

### Armazenamento Vetorial

- **PostgreSQL PGVector:** Armazenamento principal com coleções organizadas
- **Pinecone:** Armazenamento secundário para redundância
- **Estratégia de Distância:** Cosseno para busca de similaridade

### Metadados de Email

- **Received Date:** Data de recebimento
- **Subject:** Assunto da mensagem
- **From:** Remetente
- **Message ID:** Identificador único
- **Body:** Conteúdo completo

### Funcionalidades de Chat

- **Memória Persistente:** Histórico salvo no PostgreSQL
- **Busca Vetorial:** Consultas baseadas em similaridade semântica
- **Interface Pública:** Webhook para recebimento de mensagens
- **Upload de Arquivos:** Suporte a diferentes tipos de mídia

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
