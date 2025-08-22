# ⚙️ Resposta Automática de E-mail com Revisão Humana

## Descrição

Este workflow automatiza o processamento de emails recebidos. Resume o conteúdo, gera uma resposta usando IA e envia essa resposta proposta para revisão humana antes do envio final do email.

## Funcionalidades

- **Trigger:** Monitoramento automático de caixa de entrada
- **Integração:** IA para geração de respostas, sistema de emails
- **Processamento:** Resumo automático e geração de respostas profissionais
- **Saída:** Email revisado e aprovado pelo humano

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                        |
| --------- | ------ | -------------------------------- |
| `email`   | object | Email recebido com conteúdo HTML |
| `subject` | string | Assunto do email original        |
| `sender`  | string | Endereço de email do remetente   |
| `content` | string | Conteúdo HTML do email           |

## Como Funciona

1. **Detecção de Email:** Monitora caixa de entrada para iniciar automaticamente o workflow
2. **Conversão para Markdown:** Transforma conteúdo HTML em formato Markdown para análise por modelos de linguagem
3. **Resumo Automático:** Produz resumo conciso do email recebido para compreensão rápida
4. **Geração de Resposta IA:** Cria resposta profissional e concisa baseada no resumo, respeitando limite de palavras configurado
5. **Revisão Humana (Human-in-the-loop):** Envia mensagem original e resposta gerada por IA para endereço interno para aprovação
6. **Envio Condicional:** Se a resposta for aprovada, é encaminhada para o remetente original. Caso contrário, permanece pendente para revisão adicional
7. **Configuração de Remetente e Assunto:** Preserva assunto original do email (adicionando prefixo de resposta) e define remetente/destinatário usando credenciais de envio predefinidas

## Configuração

### Credenciais Necessárias

- **Email:** Servidor SMTP configurado para envio e recebimento
- **IA:** Modelo de linguagem configurado para geração de respostas
- **Revisão:** Endereço de email interno para aprovação de respostas

### Estrutura de Dados

```json
{
  "email": {
    "subject": "Consulta sobre produto",
    "sender": "cliente@email.com",
    "content": "<html>Conteúdo do email...</html>",
    "timestamp": "2025-01-21T10:00:00Z"
  },
  "ai_response": {
    "summary": "Cliente solicita informações sobre produto X",
    "response": "Resposta gerada pela IA...",
    "word_count": 150
  },
  "review_status": "pending"
}
```

## Casos de Uso

- **Suporte ao Cliente:** Respostas automáticas para consultas comuns
- **Atendimento:** Triagem inicial de emails com respostas rápidas
- **Comunicação Corporativa:** Padronização de respostas com controle humano
- **E-commerce:** Respostas automáticas para pedidos e consultas
- **Recursos Humanos:** Processamento de candidaturas e solicitações

## Dependências

- Servidor de email configurado (SMTP/IMAP)
- Modelo de IA para geração de respostas
- Sistema de revisão humana configurado
- Endereço de email interno para aprovações
- Limite de palavras configurado para respostas

## Estrutura do Workflow

1. **Email Trigger** - Monitoramento de caixa de entrada
2. **HTML to Markdown** - Conversão de formato para análise
3. **AI Summary** - Geração de resumo automático
4. **AI Response Generation** - Criação de resposta profissional
5. **Human Review** - Envio para aprovação humana
6. **Conditional Logic** - Verificação de aprovação
7. **Email Send** - Envio da resposta aprovada
8. **Status Update** - Atualização de status da revisão

## Monitoramento

- **Emails Recebidos:** Contagem de emails processados
- **Taxa de Aprovação:** Percentual de respostas aprovadas
- **Tempo de Revisão:** Tempo médio para aprovação humana
- **Qualidade IA:** Feedback sobre respostas geradas
- **Erros:** Falhas no processamento ou envio

## Tratamento de Erros

- **Email Inválido:** Validação de estrutura de dados
- **Falha IA:** Fallback para resposta padrão
- **Timeout Revisão:** Notificação para revisores
- **Falha Envio:** Retry automático com backoff
- **Formato Inválido:** Conversão para formato suportado

## Características Técnicas

### Processamento de Email

- **Formato Suportado:** HTML e texto plano
- **Conversão:** HTML → Markdown para análise IA
- **Preservação:** Assunto original com prefixo de resposta
- **Metadados:** Timestamp, remetente, destinatário

### Geração de Resposta IA

- **Modelo:** Configurável (GPT, Claude, etc.)
- **Limite de Palavras:** Configurável por tipo de email
- **Tom:** Profissional e conciso
- **Contexto:** Baseado no resumo do email original

### Sistema de Revisão Humana

- **Workflow:** Human-in-the-loop (HITL)
- **Aprovação:** Email interno para revisores
- **Status:** Pending, Approved, Rejected
- **Feedback:** Comentários opcionais dos revisores

### Configuração de Envio

- **Credenciais:** SMTP configurado
- **Remetente:** Endereço corporativo configurado
- **Assunto:** Prefixo + assunto original
- **Formato:** HTML com resposta formatada

### Segurança e Controle

- **Aprovação Obrigatória:** Sem envio automático
- **Auditoria:** Log completo de todas as ações
- **Revisão:** Controle humano sobre todas as respostas
- **Backup:** Preservação de emails originais

---

_Autor: Matheus Freitas_  
_Categoria: Automação_  
_Versão: 1.0_
