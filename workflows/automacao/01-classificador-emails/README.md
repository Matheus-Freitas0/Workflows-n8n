# 📧 Classificador de E-mails

## Descrição

Sistema automatizado para classificação inteligente de e-mails utilizando inteligência artificial. Analisa conteúdo, remetente e contexto para determinar importância e aplicar ações automáticas.

## Funcionalidades

- **Trigger:** Verificação automática de novos e-mails
- **Integração:** Gmail + OpenAI + Sistema de etiquetas
- **Processamento:** Análise inteligente de conteúdo e contexto
- **Classificação:** Categorização automática por importância
- **Ações:** Marcação como lido, aplicação de etiquetas

## Como Funciona

1. **Monitoramento:** Verifica novos e-mails a cada minuto
2. **Análise:** IA analisa assunto, remetente e conteúdo
3. **Classificação:** Determina importância do e-mail
4. **Ação:** Aplica etiquetas e marcações apropriadas
5. **Organização:** Mantém caixa de entrada organizada

## Configuração

### Credenciais Necessárias

- **Gmail OAuth2:** Configurado para acesso à conta
- **OpenAI API:** Credenciais configuradas no n8n
- **Etiquetas:** Sistema de labels configurado no Gmail

### Modelo de IA

- **Nome:** GPT-4o Mini
- **Provedor:** OpenAI
- **Capacidades:** Análise de e-mails, classificação inteligente

### Categorias de Classificação

- **Importante:** E-mails relevantes, mantidos não lidos
- **Não Relevante:** E-mails de baixa prioridade, marcados como lidos
- **Revisar Manualmente:** Casos duvidosos para análise humana

## Estrutura do Workflow

1. **Gmail Trigger** - Monitora novos e-mails
2. **AI Agent** - Analisa e classifica conteúdo
3. **GPT-4o Mini** - Modelo de IA para análise
4. **Gmail Tools** - Aplica ações (marcar lido, etiquetas)

## Casos de Uso

- Organização automática de caixa de entrada
- Filtragem de spam e e-mails irrelevantes
- Priorização de mensagens importantes
- Redução de tempo gasto com e-mails
- Gestão eficiente de comunicação

## Dependências

- Credenciais do Gmail configuradas
- OpenAI API funcionando
- Sistema de etiquetas configurado
- Acesso à conta de e-mail

## Monitoramento

- Verificar execuções automáticas
- Monitorar classificação de e-mails
- Acompanhar aplicação de etiquetas
- Verificar precisão das classificações

## Tratamento de Erros

- **API indisponível:** Log de erro registrado
- **E-mail inválido:** Tratamento de formato
- **Falha na classificação:** Fallback para categoria padrão
- **Permissões:** Verificação de acesso ao Gmail

---
*Autor: Matheus Freitas*  
*Categoria: Automação*  
*Versão: 1.0*
