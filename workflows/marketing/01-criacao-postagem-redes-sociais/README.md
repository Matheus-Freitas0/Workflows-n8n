# 📱 Criação de Postagem Redes Sociais

## Descrição

Workflow automatizado para criação de posts para redes sociais utilizando inteligência artificial. Este sistema gera conteúdo otimizado baseado em assuntos fornecidos pelo usuário.

## Funcionalidades

- **Trigger:** Formulário web para entrada de dados
- **Integração:** OpenAI GPT-4 + Tavily Search + Geração de imagens
- **Processamento:** Criação automática de texto e imagens para posts
- **Pesquisa:** Busca de informações atualizadas sobre o assunto
- **Saída:** Conteúdo completo para redes sociais

## Como Funciona

1. **Recebimento:** Usuário preenche formulário com assunto e orientações
2. **Pesquisa:** Sistema busca informações recentes sobre o tema
3. **Geração:** IA cria texto otimizado para redes sociais
4. **Imagem:** Gera imagem relacionada ao conteúdo
5. **Resultado:** Retorna post completo com texto e imagem

## Configuração

### Credenciais Necessárias

- **OpenAI API:** Credenciais configuradas no n8n
- **Tavily Search:** API key para busca de informações
- **Formulário Web:** Webhook configurado para receber dados

### Modelo de IA

- **Nome:** GPT-4o Mini
- **Provedor:** OpenAI
- **Capacidades:** Criação de conteúdo, otimização para redes sociais

### Campos do Formulário

| Campo | Tipo | Descrição |
|-------|------|-----------|
| **Assunto do Post** | string | Tema principal da postagem |
| **Orientações adicionais** | textarea | Detalhes sobre o estilo e tom desejado |

## Estrutura do Workflow

1. **Form Trigger** - Recebe dados do formulário
2. **Tavily Search** - Busca informações atualizadas
3. **OpenAI Chat Model** - Gera texto otimizado
4. **Geração de Imagem** - Cria visual relacionado
5. **Formatação** - Estrutura conteúdo final

## Casos de Uso

- Criação de posts para Instagram
- Conteúdo para Facebook
- Posts para LinkedIn
- Marketing digital automatizado
- Gestão de redes sociais

## Dependências

- Credenciais da OpenAI configuradas
- API do Tavily funcionando
- Formulário web configurado
- Acesso à internet para busca

## Monitoramento

- Verificar execuções do workflow
- Monitorar qualidade do conteúdo gerado
- Acompanhar uso das APIs
- Verificar geração de imagens

## Tratamento de Erros

- **API indisponível:** Fallback para conteúdo básico
- **Formulário inválido:** Validação de campos obrigatórios
- **Falha na IA:** Notificação de erro ao usuário
- **Busca sem resultados:** Conteúdo baseado apenas no prompt

## Otimizações

- **Cache:** Evitar pesquisas repetidas sobre mesmo tema
- **Templates:** Estruturas pré-definidas para diferentes redes
- **Validação:** Verificação de qualidade do conteúdo gerado
- **Personalização:** Adaptação ao tom da marca

---
*Autor: Matheus Freitas*  
*Categoria: Marketing*  
*Versão: 1.0*
