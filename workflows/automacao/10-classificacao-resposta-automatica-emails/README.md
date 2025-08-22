# ⚙️ Classificação e Resposta Automática de E-mails

## Descrição

Sistema inteligente que automatiza o processamento de e-mails recebidos, detectando e classificando mensagens por categoria, respondendo automaticamente com templates específicos, aplicando rótulos organizacionais e sincronizando contatos com sistemas de CRM/marketing por e-mail.

## Funcionalidades

- **Trigger:** Monitoramento periódico da caixa de entrada para novos e-mails
- **Integração:** Sistema de e-mail, IA para classificação, templates de resposta, CRM/marketing
- **Processamento:** Classificação inteligente, filtragem de remetentes, prevenção de threads
- **Saída:** Respostas automáticas, e-mails marcados, rótulos aplicados e contatos sincronizados

## Parâmetros de Entrada

| Parâmetro       | Tipo   | Descrição                                            |
| --------------- | ------ | ---------------------------------------------------- |
| `email_data`    | object | Dados do e-mail recebido (assunto, corpo, remetente) |
| `sender_domain` | string | Domínio do remetente para filtragem interna          |
| `subject_line`  | string | Linha do assunto para detecção de threads            |
| `email_content` | string | Conteúdo completo do e-mail para classificação       |

## Como Funciona

1. **Email Monitoring:** Verifica a caixa de entrada periodicamente para novos e-mails
2. **Internal Sender Filtering:** Identifica e-mails originados do domínio interno para tratamento separado
3. **Thread Response Prevention:** Evita responder a mensagens que já são respostas (assunto começando com "Re:")
4. **Language Model Classification:** Analisa assunto e corpo da mensagem para classificar em categorias (Guest Post, YouTube, Cursos)
5. **Automatic Response with Templates:** Envia e-mails personalizados conforme a categoria detectada (modelo para guest post, vídeo do YouTube e cadastro de cursos)
6. **Mark as Read and Apply Label:** Atualiza o estado do e-mail para lido e aplica rótulos organizacionais
7. **Contact Synchronization:** Cria ou atualiza o contato do remetente em um sistema de CRM/marketing por e-mail

## Configuração

### Credenciais Necessárias

- **Email Service:** Configuração de acesso à caixa de entrada (IMAP/POP3)
- **IA Language Model:** Modelo de linguagem para classificação de e-mails
- **Email Templates:** Templates personalizados para cada categoria de resposta
- **CRM/Marketing System:** Sistema para sincronização de contatos
- **Email Labels:** Configuração de rótulos organizacionais

### Estrutura de Dados

```json
{
  "email_processing": {
    "email_id": "msg_123456",
    "sender": {
      "email": "contato@empresa.com",
      "name": "João Silva",
      "domain": "empresa.com"
    },
    "subject": "Solicitação de Guest Post",
    "body": "Olá, gostaria de contribuir com um guest post...",
    "received_date": "2025-01-15T10:30:00Z",
    "is_thread": false
  },
  "classification_result": {
    "category": "guest_post",
    "confidence": 0.95,
    "keywords_detected": ["guest post", "contribuição", "artigo"],
    "priority": "medium"
  },
  "response_template": {
    "template_id": "guest_post_response",
    "personalization": {
      "sender_name": "João Silva",
      "company_name": "Empresa",
      "response_date": "2025-01-15"
    }
  },
  "crm_sync": {
    "contact_id": "CT_001",
    "email": "contato@empresa.com",
    "category": "guest_post",
    "last_interaction": "2025-01-15T10:30:00Z",
    "status": "responded"
  }
}
```

## Casos de Uso

- **Gestão de Guest Posts:** Classificação automática e resposta a solicitações de contribuição
- **Suporte a Cursos:** Identificação e resposta a interessados em cursos
- **Colaborações YouTube:** Processamento de propostas de parceria para vídeos
- **Filtragem Interna:** Separação automática de e-mails internos e externos
- **Prevenção de Threads:** Evita respostas automáticas em conversas já em andamento
- **Sincronização de Contatos:** Manutenção automática de base de dados de contatos
- **Organização Automática:** Aplicação de rótulos e marcação de e-mails

## Dependências

- Sistema de e-mail configurado com acesso IMAP/POP3
- Modelo de IA para classificação de linguagem natural
- Templates de e-mail personalizados para cada categoria
- Sistema de CRM ou marketing por e-mail configurado
- Configuração de rótulos e categorias organizacionais
- Acesso para envio de e-mails automáticos

## Estrutura do Workflow

1. **Email Trigger** - Monitora caixa de entrada periodicamente
2. **Sender Domain Check** - Verifica se é remetente interno ou externo
3. **Thread Detection** - Identifica se é resposta a thread existente
4. **Content Analysis** - Analisa assunto e corpo para classificação
5. **AI Classification** - Classifica e-mail usando modelo de linguagem
6. **Template Selection** - Seleciona template apropriado para categoria
7. **Response Generation** - Gera resposta personalizada
8. **Email Sending** - Envia resposta automática
9. **Status Update** - Marca e-mail como lido
10. **Label Application** - Aplica rótulos organizacionais
11. **Contact Sync** - Sincroniza contato com CRM/marketing

## Monitoramento

- **E-mails Processados:** Total de mensagens analisadas e respondidas
- **Taxa de Classificação:** Precisão da categorização automática
- **Tempo de Resposta:** Latência média entre recebimento e resposta
- **Categorias Identificadas:** Distribuição de tipos de e-mail processados
- **Contatos Sincronizados:** Total de contatos atualizados no CRM
- **Filtros Aplicados:** Eficiência na detecção de threads e remetentes internos
- **Templates Utilizados:** Frequência de uso de cada template de resposta

## Tratamento de Erros

- **Falha na Classificação:** Resposta padrão com notificação de erro
- **Template Não Encontrado:** Fallback para template genérico
- **Erro de Envio:** Retry automático com notificação de falha
- **Falha na Sincronização CRM:** Log de erro e retry posterior
- **E-mail Corrompido:** Notificação de erro e processamento manual
- **Timeout de Processamento:** Cancelamento e notificação de falha
- **Permissões Insuficientes:** Log de erro e notificação administrativa

## Características Técnicas

### Sistema de Monitoramento

- **Verificação Periódica:** Polling automático da caixa de entrada
- **Filtragem Inteligente:** Identificação automática de domínios internos
- **Detecção de Threads:** Análise de assunto para evitar respostas duplicadas
- **Processamento Assíncrono:** Tratamento não-bloqueante de múltiplos e-mails

### Classificação com IA

- **Análise de Conteúdo:** Processamento de assunto e corpo da mensagem
- **Categorização Inteligente:** Identificação automática de tipos de solicitação
- **Confiança de Classificação:** Score de precisão para cada categorização
- **Aprendizado Contínuo:** Melhoria da precisão com uso

### Sistema de Templates

- **Respostas Personalizadas:** Adaptação automática ao contexto
- **Múltiplas Categorias:** Templates específicos para cada tipo de solicitação
- **Personalização Dinâmica:** Inclusão automática de informações do remetente
- **Gestão Centralizada:** Sistema de templates organizados e versionados

### Integração CRM/Marketing

- **Sincronização Automática:** Atualização em tempo real de contatos
- **Categorização de Contatos:** Marcação automática por tipo de interesse
- **Histórico de Interações:** Rastreamento completo de comunicações
- **Segmentação Inteligente:** Agrupamento automático por categoria de interesse

---

_Autor: Matheus Freitas_  
_Categoria: Automação_  
_Versão: 1.0_
