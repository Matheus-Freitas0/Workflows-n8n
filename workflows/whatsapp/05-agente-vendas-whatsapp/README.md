# 📱 Agente de Vendas via WhatsApp

## Descrição

Sistema inteligente de agente de vendas que responde automaticamente a clientes via WhatsApp, consultando um catálogo de produtos extraído de brochura PDF da Yamaha para fornecer respostas precisas e direcionamentos baseados em conhecimento factual.

## Funcionalidades

- **Trigger:** Recebimento de mensagens de clientes via WhatsApp
- **Integração:** WhatsApp API, IA com memória, processamento de PDF, vetores semânticos
- **Processamento:** Análise de mensagens, consulta ao catálogo vetorial, geração de respostas inteligentes
- **Saída:** Respostas automáticas com informações precisas sobre produtos

## Parâmetros de Entrada

| Parâmetro    | Tipo   | Descrição                                 |
| ------------ | ------ | ----------------------------------------- |
| `message`    | object | Mensagem recebida do cliente via WhatsApp |
| `session_id` | string | ID da sessão para manutenção de contexto  |
| `user_info`  | object | Informações do usuário/cliente            |

## Como Funciona

1. **Importação de Brochura:** Download automático de PDF da Yamaha e extração de texto
2. **Processamento de Texto:** Divisão do conteúdo em segmentos para indexação eficiente
3. **Geração de Vetores:** Conversão de texto em vetores semânticos para busca inteligente
4. **Criação de Catálogo:** Armazenamento dos vetores em repositório de busca
5. **Recebimento de Mensagens:** Trigger via WhatsApp para mensagens de clientes
6. **Filtro de Mídia:** Aceita apenas mensagens de texto, notifica para outros tipos
7. **Processamento com IA:** Agente com memória processa mensagem e histórico da conversa
8. **Consulta ao Catálogo:** Busca informações precisas sobre produtos 2024 quando necessário
9. **Geração de Resposta:** Criação de resposta contextual e informativa
10. **Envio Automático:** Resposta enviada de volta ao cliente via WhatsApp
11. **Upload Manual:** Possibilidade de execução manual para atualizações do catálogo

## Configuração

### Credenciais Necessárias

- **WhatsApp Business API:** Configuração de webhook e tokens
- **IA Model:** Modelo de linguagem configurado para processamento
- **Storage:** Repositório de vetores para catálogo de produtos
- **PDF Processing:** Acesso para download e processamento de brochuras

### Estrutura de Dados

```json
{
  "whatsapp_message": {
    "from": "5511999999999",
    "body": "Olá, gostaria de saber sobre motos 2024",
    "timestamp": "2024-01-15T10:30:00Z",
    "type": "text"
  },
  "catalog_data": {
    "brochure_url": "https://yamaha.com/brochure-2024.pdf",
    "vector_store": "product_catalog_vectors",
    "last_updated": "2024-01-15T09:00:00Z"
  },
  "ai_agent": {
    "model": "gpt-4",
    "memory_enabled": true,
    "context_window": 4000,
    "temperature": 0.7
  }
}
```

## Casos de Uso

- **Atendimento Automático:** Respostas instantâneas a consultas sobre produtos
- **Vendas 24/7:** Disponibilidade contínua para clientes em diferentes fusos horários
- **Catálogo Inteligente:** Consulta automática a informações atualizadas de produtos
- **Gestão de Conversas:** Manutenção de contexto entre mensagens
- **Escalabilidade:** Atendimento simultâneo a múltiplos clientes
- **Atualizações de Produto:** Facilidade para atualizar catálogo com novos produtos

## Dependências

- API do WhatsApp Business configurada e ativa
- Modelo de IA com capacidade de processamento de linguagem natural
- Sistema de armazenamento de vetores semânticos
- Acesso à brochura PDF da Yamaha (ou similar)
- Processador de PDF para extração de texto
- Sistema de memória para manutenção de contexto de conversas

## Estrutura do Workflow

1. **PDF Import Node** - Download e processamento de brochura
2. **Text Chunking** - Divisão do texto em segmentos indexáveis
3. **Embedding Generation** - Conversão de texto em vetores semânticos
4. **Vector Store** - Armazenamento e indexação dos vetores
5. **WhatsApp Trigger** - Recebimento de mensagens de clientes
6. **Message Filter** - Validação de tipo de mensagem
7. **AI Agent Processing** - Processamento inteligente com memória
8. **Catalog Search** - Consulta ao catálogo vetorial quando necessário
9. **Response Generation** - Criação de resposta contextual
10. **WhatsApp Send** - Envio da resposta ao cliente
11. **Manual Upload Trigger** - Execução manual para atualizações

## Monitoramento

- **Mensagens Recebidas:** Contagem total de mensagens processadas
- **Taxa de Resposta:** Percentual de mensagens respondidas automaticamente
- **Tempo de Resposta:** Latência média para geração de respostas
- **Consultas ao Catálogo:** Frequência de uso do sistema de vetores
- **Qualidade das Respostas:** Feedback sobre precisão das informações
- **Uso de Memória:** Eficiência na manutenção de contexto

## Tratamento de Erros

- **PDF Indisponível:** Notificação e fallback para catálogo existente
- **Falha na IA:** Resposta padrão com redirecionamento para atendente humano
- **Erro de WhatsApp:** Retry automático com backoff exponencial
- **Vetores Corrompidos:** Regeneração automática do catálogo
- **Timeout de Resposta:** Cancelamento e notificação de erro
- **Permissões Insuficientes:** Log de erro e notificação administrativa

## Características Técnicas

### Sistema de Vetores

- **Embedding Model:** Conversão de texto em vetores de alta dimensionalidade
- **Similarity Search:** Busca por similaridade semântica entre consultas e produtos
- **Index Optimization:** Índice otimizado para consultas rápidas
- **Update Mechanism:** Sistema de atualização incremental do catálogo

### Processamento de IA

- **Memory Management:** Manutenção de contexto entre mensagens
- **Context Window:** Janela de contexto configurável para conversas longas
- **Response Quality:** Controle de temperatura para respostas consistentes
- **Fallback Logic:** Sistema de fallback para casos de erro

### Integração WhatsApp

- **Webhook Security:** Validação de origem das mensagens
- **Rate Limiting:** Controle de taxa de envio para evitar bloqueios
- **Message Types:** Suporte a diferentes tipos de mídia
- **Delivery Confirmation:** Confirmação de entrega das mensagens

### Gestão de Catálogo

- **Automatic Updates:** Atualização automática baseada em mudanças na brochura
- **Version Control:** Controle de versão para diferentes edições do catálogo
- **Backup System:** Sistema de backup para preservar dados históricos
- **Performance Metrics:** Métricas de performance para otimização

---

_Autor: Matheus Freitas_  
_Categoria: WhatsApp_  
_Versão: 1.0_
