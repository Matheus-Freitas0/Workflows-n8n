# ⚙️ Resposta Automática a E-mails com Aprovação

## Descrição

Sistema inteligente que automatiza o processamento de e-mails recebidos, resumindo o conteúdo, consultando uma base de conhecimento para enriquecer a resposta, gerando um rascunho com IA e solicitando aprovação antes de enviar a resposta final ao remetente.

## Funcionalidades

- **Trigger:** Detecção automática de e-mails recebidos via IMAP
- **Integração:** IMAP, IA para processamento, base de conhecimento vetorial (RAG), Gmail para aprovação
- **Processamento:** Resumo automático, consulta RAG, geração de resposta com IA
- **Saída:** E-mails respondidos automaticamente após aprovação humana

## Parâmetros de Entrada

| Parâmetro        | Tipo   | Descrição                                |
| ---------------- | ------ | ---------------------------------------- |
| `email_data`     | object | Dados do e-mail recebido via IMAP        |
| `knowledge_base` | object | Configuração da base de conhecimento RAG |
| `approval_email` | string | Endereço de e-mail para aprovação        |

## Como Funciona

1. **Detecção de E-mails:** Inicia o fluxo ao chegar uma nova mensagem via IMAP
2. **Conversão para Markdown:** Normaliza o conteúdo do e-mail para melhor compreensão dos modelos de linguagem
3. **Sumarização do E-mail:** Gera um resumo conciso (até 100 palavras) do conteúdo recebido
4. **Recuperação de Conhecimento (RAG):** Consulta uma base vetorial para extrair informações relevantes que embasem a resposta
5. **Geração de Resposta com LLM:** Cria uma resposta profissional e concisa (máx. 100 palavras) em formato HTML
6. **Envio de Rascunho para Aprovação:** Envia o rascunho para um endereço que permite botão de aprovação/recusa
7. **Fluxo de Aprovação:**
   - **Se aprovado:** Envia a resposta final ao remetente
   - **Se recusado:** Permite revisão/edição e reenvio para nova aprovação

## Configuração

### Credenciais Necessárias

- **IMAP Server:** Configuração para acesso aos e-mails recebidos
- **IA Language Model:** Modelo de linguagem para resumo e geração de respostas
- **Vector Database:** Base de conhecimento vetorial para consultas RAG
- **Gmail API:** Acesso para envio de rascunhos de aprovação
- **SMTP Server:** Servidor para envio das respostas finais

### Estrutura de Dados

```json
{
  "email_processing": {
    "imap_config": {
      "server": "imap.gmail.com",
      "port": 993,
      "security": "ssl",
      "check_interval": "5 minutes"
    },
    "markdown_conversion": {
      "html_to_markdown": true,
      "clean_formatting": true,
      "preserve_links": true
    }
  },
  "ai_processing": {
    "summary_model": "gpt-4",
    "response_model": "gpt-4",
    "max_summary_length": 100,
    "max_response_length": 100,
    "temperature": 0.3,
    "output_format": "html"
  },
  "rag_system": {
    "vector_database": "pinecone",
    "embedding_model": "text-embedding-ada-002",
    "similarity_threshold": 0.8,
    "max_results": 5
  },
  "approval_workflow": {
    "approval_email": "aprovacao@empresa.com",
    "approval_timeout": "24 hours",
    "retry_on_rejection": true,
    "max_approval_attempts": 3
  }
}
```

## Casos de Uso

- **Atendimento ao Cliente:** Respostas automáticas para consultas frequentes
- **Suporte Técnico:** Respostas baseadas em base de conhecimento
- **Vendas e Marketing:** Respostas personalizadas para leads e clientes
- **Recursos Humanos:** Respostas automáticas para candidatos e funcionários
- **Financeiro:** Respostas para consultas sobre faturas e pagamentos
- **Escalabilidade:** Processamento de grandes volumes de e-mails sem intervenção manual

## Dependências

- Servidor IMAP configurado e acessível
- Modelo de IA configurado para resumo e geração de texto
- Base de conhecimento vetorial (RAG) configurada
- Conta Gmail com API habilitada para aprovações
- Servidor SMTP para envio de respostas finais
- Sistema de armazenamento para rascunhos e histórico

## Estrutura do Workflow

1. **IMAP Trigger** - Detecta novos e-mails recebidos
2. **Email Content Extraction** - Extrai conteúdo e metadados do e-mail
3. **Markdown Conversion** - Converte HTML para Markdown
4. **Content Summarization** - Gera resumo conciso do e-mail
5. **Knowledge Base Query** - Consulta base vetorial para informações relevantes
6. **Response Generation** - Cria resposta usando IA e contexto RAG
7. **Draft Creation** - Gera rascunho em formato HTML
8. **Approval Email Send** - Envia rascunho para aprovação via Gmail
9. **Approval Decision** - Aguarda decisão de aprovação/rejeição
10. **Response Finalization** - Aplica aprovação ou permite edição
11. **Final Email Send** - Envia resposta final ao remetente
12. **Workflow Completion** - Registra conclusão e atualiza histórico

## Monitoramento

- **E-mails Processados:** Total de mensagens processadas automaticamente
- **Taxa de Aprovação:** Percentual de respostas aprovadas na primeira tentativa
- **Tempo de Resposta:** Latência média desde recebimento até resposta
- **Qualidade das Respostas:** Feedback sobre precisão e relevância
- **Uso da Base de Conhecimento:** Eficiência das consultas RAG
- **Taxa de Rejeição:** Frequência de respostas rejeitadas para edição

## Tratamento de Erros

- **Falha na Conexão IMAP:** Retry com backoff exponencial
- **Erro na Geração de IA:** Resposta padrão com redirecionamento para humano
- **Timeout de Aprovação:** Notificação de pendência e escalação
- **Falha no Envio:** Retry automático com notificação de erro
- **Base de Conhecimento Indisponível:** Processamento sem contexto RAG
- **Formato de E-mail Inválido:** Log de erro e processamento manual

## Características Técnicas

### Sistema de Processamento de E-mails

- **Detecção Automática:** Monitoramento contínuo via IMAP
- **Conversão Inteligente:** Transformação HTML para Markdown otimizada
- **Resumo Contextual:** Geração de resumos concisos e relevantes
- **Formatação HTML:** Saída em formato profissional e responsivo

### Sistema RAG (Retrieval-Augmented Generation)

- **Base Vetorial:** Consulta eficiente a base de conhecimento
- **Embedding Inteligente:** Representação semântica de documentos
- **Similaridade Contextual:** Busca por informações mais relevantes
- **Enriquecimento de Resposta:** Contexto adicional para melhor qualidade

### Fluxo de Aprovação

- **Sistema de Botões:** Interface intuitiva para aprovação/rejeição
- **Timeout Configurável:** Controle de tempo para decisões
- **Revisão e Edição:** Capacidade de modificar respostas rejeitadas
- **Histórico de Aprovações:** Rastreamento completo de decisões

### Integração e Automação

- **IMAP Integration:** Acesso direto aos servidores de e-mail
- **Gmail API:** Sistema robusto de aprovação via Gmail
- **SMTP Delivery:** Envio confiável de respostas finais
- **Workflow Orchestration:** Coordenação automática de todos os passos

---

_Autor: Matheus Freitas_  
_Categoria: Automação_  
_Versão: 1.0_
