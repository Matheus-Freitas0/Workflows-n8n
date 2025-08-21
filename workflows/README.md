# 🚀 Workflows n8n - Estrutura Organizacional

Esta pasta contém todos os workflows organizados por categorias funcionais, onde cada workflow possui sua própria pasta com documentação completa.

## 📁 Estrutura de Pastas

### 📅 [Agendamento](./agendamento/)

Workflows relacionados ao agendamento de eventos e reuniões.

- **01-agente-agendamento-agendar/** - Agendamento via API Cal.com
- **02-agendar-evento-whatsapp/** - Agendamento via WhatsApp
- **03-agente-agendamento/** - Agente principal de agendamento
- **04-agente-agendamento-reagendamento/** - Reagendamento de eventos
- **05-agente-agendamento-detalhes-evento/** - Consulta de detalhes
- **06-agente-agendamento-cancelar-evento/** - Cancelamento de eventos
- **07-agente-gestao-calendario/** - Gestão de calendário

### 🤖 [IA e Agentes](./ia-agentes/)

Workflows de inteligência artificial e agentes automatizados.

- **01-agente-grok4/** - Agente de IA com Grok 4
- **02-agente-selecao-modelos/** - Agente de seleção de modelos
- **03-agente-ia-postgres/** - Agente de IA com PostgreSQL
- **04-agente-previsao-tempo/** - Agente de previsão do tempo
- **05-agente-previsao-tempo-pegar-previsao/** - Pegar previsão do tempo
- **06-agente-ideias-conteudo-yt/** - Agente de ideias de conteúdo YT
- **07-agente-ideias-conteudo-yt-titulos/** - Geração de títulos YT
- **08-agente-ideias-conteudo-yt-thumb/** - Ideias de thumbnails YT
- **09-agente-ideias-conteudo-yt-roteiro/** - Geração de roteiros YT
- **10-agente-ideias-conteudo-yt-pesquisa/** - Pesquisa para conteúdo YT
- **11-ai-nodes/** - AI Nodes especializados
- **12-ai-agent-configs/** - Configurações de agentes de IA
- **13-agentes-ia-mais-precisos/** - Agentes de IA mais precisos
- **14-multiagent-post-blog-corpo/** - Multiagent para post de blog
- **15-integracao-perplexity/** - Integração com Perplexity
- **16-integracao-deepseek/** - Integração com DeepSeek
- **17-integracao-gemini-flash/** - Integração com Gemini Flash
- **18-hitl-exemplo-telegram/** - HITL exemplo com Telegram
- **19-tutor-alunos-enviar-dados/** - Sistema de tutoria para alunos
- **20-tutor-alunos-agente/** - Agente de tutoria educacional
- **21-rag-pipeline-chatbot-reranker/** - Pipeline RAG com chatbot e reranker
- **22-rag-agente-auto-aprendizado/** - Agente RAG com auto-aprendizado
- **23-propriedade-agentes/** - Sistema de propriedade e gestão de agentes
- **24-primeiro-agente-ia/** - Primeiro agente de IA básico
- **25-orquestracao-agentes/** - Orquestração de múltiplos agentes
- **26-n8n-gemini/** - Integração n8n com Google Gemini
- **27-multiagent-post-blog/** - Sistema multiagent para blog
- **28-multiagent-post-blog-titulos/** - Multiagent para títulos de blog

### 📊 [Monitoramento](./monitoramento/)

Workflows de tracking, monitoramento e análise de dados.

- **01-agent-tracker/** - Tracking de execuções de agentes
- **02-error-logger/** - Sistema de log de erros automatizado
- **03-seguranca-webhook/** - Sistema de segurança para webhooks

### 💰 [Financeiro](./financeiro/)

Workflows relacionados a gestão financeira e controle de despesas.

- **01-agente-despesas-pessoais-adicionar/** - Adicionar despesas pessoais
- **02-agentes-despesas-pessoais/** - Agentes de despesas pessoais

### 📱 [WhatsApp](./whatsapp/)

Workflows específicos para integração com WhatsApp.

- **01-agente-catalogo-produtos/** - Catálogo automático de produtos
- **02-agente-ia-whatsapp/** - Agente de IA com WhatsApp
- **03-agente-whatsapp-agendamento/** - Agente WhatsApp de agendamento
- **04-teste-whatsapp-p1/** - Teste e validação WhatsApp

### 📢 [Marketing](./marketing/)

Workflows relacionados a marketing digital e redes sociais.

- **01-criacao-postagem-redes-sociais/** - Criação de postagem redes sociais
- **02-criacao-postagem-redes-sociais-com-logs/** - Criação com sistema de logs

### ⚙️ [Automação](./automacao/)

Workflows de automação geral e processamento inteligente.

- **01-classificador-emails/** - Classificador de e-mails
- **02-funcionalidades-novas-198/** - Funcionalidades novas versão 1.98
- **03-funcionalidades-novas-1102/** - Funcionalidades novas versão 1.102+
- **04-funcionalidades-novas-1101/** - Funcionalidades novas versão 1.101
- **05-funcionalidades-novas-1100/** - Funcionalidades novas versão 1.100

### 💾 [Backup](./backup/)

Workflows de backup e segurança de dados.

- **01-backup-workflow-gdrive/** - Backup workflow Google Drive
- **02-backup-workflow-credenciais-gdrive/** - Backup workflow e credenciais

### 👔 [Recursos Humanos](./recursos-humanos/)

Workflows relacionados a gestão de recursos humanos.

- **01-analisador-curriculo/** - Analisador de currículo

## 🔄 Workflows Disponíveis

| Categoria        | Nome                                                                                                  | Descrição                         |
| ---------------- | ----------------------------------------------------------------------------------------------------- | --------------------------------- |
| Agendamento      | [01-agente-agendamento-agendar](./agendamento/01-agente-agendamento-agendar/)                         | Agendamento via API Cal.com       |
| Agendamento      | [02-agendar-evento-whatsapp](./agendamento/02-agendar-evento-whatsapp/)                               | Agendamento via WhatsApp          |
| Agendamento      | [03-agente-agendamento](./agendamento/03-agente-agendamento/)                                         | Agente principal de agendamento   |
| Agendamento      | [04-agente-agendamento-reagendamento](./agendamento/04-agente-agendamento-reagendamento/)             | Reagendamento de eventos          |
| Agendamento      | [05-agente-agendamento-detalhes-evento](./agendamento/05-agente-agendamento-detalhes-evento/)         | Consulta de detalhes              |
| Agendamento      | [06-agente-agendamento-cancelar-evento](./agendamento/06-agente-agendamento-cancelar-evento/)         | Cancelamento de eventos           |
| Agendamento      | [07-agente-gestao-calendario](./agendamento/07-agente-gestao-calendario/)                             | Gestão de calendário              |
| IA e Agentes     | [01-agente-grok4](./ia-agentes/01-agente-grok4/)                                                      | Agente de IA com Grok 4           |
| IA e Agentes     | [02-agente-selecao-modelos](./ia-agentes/02-agente-selecao-modelos/)                                  | Agente de seleção de modelos      |
| IA e Agentes     | [03-agente-ia-postgres](./ia-agentes/03-agente-ia-postgres/)                                          | Agente de IA com PostgreSQL       |
| IA e Agentes     | [04-agente-previsao-tempo](./ia-agentes/04-agente-previsao-tempo/)                                    | Agente de previsão do tempo       |
| IA e Agentes     | [05-agente-previsao-tempo-pegar-previsao](./ia-agentes/05-agente-previsao-tempo-pegar-previsao/)      | Pegar previsão do tempo           |
| IA e Agentes     | [06-agente-ideias-conteudo-yt](./ia-agentes/06-agente-ideias-conteudo-yt/)                            | Agente de ideias de conteúdo YT   |
| IA e Agentes     | [07-agente-ideias-conteudo-yt-titulos](./ia-agentes/07-agente-ideias-conteudo-yt-titulos/)            | Geração de títulos YT             |
| IA e Agentes     | [08-agente-ideias-conteudo-yt-thumb](./ia-agentes/08-agente-ideias-conteudo-yt-thumb/)                | Ideias de thumbnails YT           |
| IA e Agentes     | [09-agente-ideias-conteudo-yt-roteiro](./ia-agentes/09-agente-ideias-conteudo-yt-roteiro/)            | Geração de roteiros YT            |
| IA e Agentes     | [10-agente-ideias-conteudo-yt-pesquisa](./ia-agentes/10-agente-ideias-conteudo-yt-pesquisa/)          | Pesquisa para conteúdo YT         |
| Monitoramento    | [01-agent-tracker](./monitoramento/01-agent-tracker/)                                                 | Tracking de execuções             |
| WhatsApp         | [01-agente-catalogo-produtos](./whatsapp/01-agente-catalogo-produtos/)                                | Catálogo automático de produtos   |
| Financeiro       | [01-agente-despesas-pessoais-adicionar](./financeiro/01-agente-despesas-pessoais-adicionar/)          | Adicionar despesas pessoais       |
| WhatsApp         | [02-agente-ia-whatsapp](./whatsapp/02-agente-ia-whatsapp/)                                            | Agente de IA com WhatsApp         |
| WhatsApp         | [03-agente-whatsapp-agendamento](./whatsapp/03-agente-whatsapp-agendamento/)                          | Agente WhatsApp de agendamento    |
| WhatsApp         | [04-teste-whatsapp-p1](./whatsapp/04-teste-whatsapp-p1/)                                            | Teste e validação WhatsApp        |
| Marketing        | [01-criacao-postagem-redes-sociais](./marketing/01-criacao-postagem-redes-sociais/)                   | Criação de postagem redes sociais |
| Marketing        | [02-criacao-postagem-redes-sociais-com-logs](./marketing/02-criacao-postagem-redes-sociais-com-logs/) | Criação com sistema de logs       |
| Automação        | [01-classificador-emails](./automacao/01-classificador-emails/)                                       | Classificador de e-mails          |
| Backup           | [01-backup-workflow-gdrive](./backup/01-backup-workflow-gdrive/)                                      | Backup workflow Google Drive      |
| Backup           | [02-backup-workflow-credenciais-gdrive](./backup/02-backup-workflow-credenciais-gdrive/)              | Backup workflow e credenciais     |
| Recursos Humanos | [01-analisador-curriculo](./recursos-humanos/01-analisador-curriculo/)                                | Analisador de currículo           |
| IA e Agentes     | [11-ai-nodes](./ia-agentes/11-ai-nodes/)                                                              | AI Nodes especializados           |
| IA e Agentes     | [12-ai-agent-configs](./ia-agentes/12-ai-agent-configs/)                                              | Configurações de agentes de IA    |
| IA e Agentes     | [13-agentes-ia-mais-precisos](./ia-agentes/13-agentes-ia-mais-precisos/)                              | Agentes de IA mais precisos       |
| IA e Agentes     | [14-multiagent-post-blog-corpo](./ia-agentes/14-multiagent-post-blog-corpo/)                          | Multiagent para post de blog     |
| IA e Agentes     | [15-integracao-perplexity](./ia-agentes/15-integracao-perplexity/)                                    | Integração com Perplexity         |
| IA e Agentes     | [16-integracao-deepseek](./ia-agentes/16-integracao-deepseek/)                                        | Integração com DeepSeek           |
| IA e Agentes     | [17-integracao-gemini-flash](./ia-agentes/17-integracao-gemini-flash/)                                | Integração com Gemini Flash       |
| IA e Agentes     | [18-hitl-exemplo-telegram](./ia-agentes/18-hitl-exemplo-telegram/)                                    | HITL exemplo com Telegram         |
| IA e Agentes     | [19-tutor-alunos-enviar-dados](./ia-agentes/19-tutor-alunos-enviar-dados/)                            | Sistema de tutoria para alunos    |
| IA e Agentes     | [20-tutor-alunos-agente](./ia-agentes/20-tutor-alunos-agente/)                                        | Agente de tutoria educacional     |
| IA e Agentes     | [21-rag-pipeline-chatbot-reranker](./ia-agentes/21-rag-pipeline-chatbot-reranker/)                    | Pipeline RAG com chatbot          |
| IA e Agentes     | [22-rag-agente-auto-aprendizado](./ia-agentes/22-rag-agente-auto-aprendizado/)                        | Agente RAG com auto-aprendizado   |
| IA e Agentes     | [23-propriedade-agentes](./ia-agentes/23-propriedade-agentes/)                                        | Sistema de propriedade de agentes |
| IA e Agentes     | [24-primeiro-agente-ia](./ia-agentes/24-primeiro-agente-ia/)                                         | Primeiro agente de IA básico      |
| IA e Agentes     | [25-orquestracao-agentes](./ia-agentes/25-orquestracao-agentes/)                                      | Orquestração de múltiplos agentes |
| IA e Agentes     | [26-n8n-gemini](./ia-agentes/26-n8n-gemini/)                                                        | Integração n8n com Gemini         |
| IA e Agentes     | [27-multiagent-post-blog](./ia-agentes/27-multiagent-post-blog/)                                     | Sistema multiagent para blog      |
| IA e Agentes     | [28-multiagent-post-blog-titulos](./ia-agentes/28-multiagent-post-blog-titulos/)                     | Multiagent para títulos           |
| Monitoramento    | [02-error-logger](./monitoramento/02-error-logger/)                                                   | Sistema de log de erros           |
| Monitoramento    | [03-seguranca-webhook](./monitoramento/03-seguranca-webhook/)                                         | Sistema de segurança para webhooks|
| Automação        | [02-funcionalidades-novas-198](./automacao/02-funcionalidades-novas-198/)                             | Funcionalidades novas 1.98       |
| Automação        | [03-funcionalidades-novas-1102](./automacao/03-funcionalidades-novas-1102/)                           | Funcionalidades novas 1.102+     |
| Automação        | [04-funcionalidades-novas-1101](./automacao/04-funcionalidades-novas-1101/)                           | Funcionalidades novas 1.101      |
| Automação        | [05-funcionalidades-novas-1100](./automacao/05-funcionalidades-novas-1100/)                           | Funcionalidades novas 1.100      |
| Financeiro       | [02-agentes-despesas-pessoais](./financeiro/02-agentes-despesas-pessoais/)                            | Agentes de despesas pessoais      |

## 📋 Convenções de Nomenclatura

### Estrutura de Pastas

```
categoria/
├── XX-nome-descritivo/
│   ├── README.md          # Documentação completa do workflow
│   └── workflow.json      # Arquivo do workflow n8n
```

### Nomenclatura

- **XX:** Número sequencial da categoria (01, 02, 03...)
- **nome:** Nome descritivo em minúsculas
- **descritivo:** Palavras separadas por hifens

## 🛠️ Como Usar

1. **Navegue** para a categoria desejada
2. **Acesse** a pasta do workflow específico
3. **Leia** o README.md para entender completamente o workflow
4. **Importe** o arquivo `workflow.json` no n8n
5. **Configure** as credenciais necessárias
6. **Execute** o workflow conforme as instruções

## 🔧 Configuração

Cada workflow possui seu próprio README com:

- **Descrição detalhada** da funcionalidade
- **Instruções de uso** passo a passo
- **Dependências** necessárias
- **Casos de uso** específicos
- **Estrutura de dados** esperada
- **Configurações** de credenciais
- **Monitoramento** e troubleshooting

## 📚 Documentação

- **README Principal:** Este arquivo (visão geral)
- **READMEs de Workflow:** Documentação específica de cada workflow
- **Workflows:** Arquivos .json prontos para importação
- **Estrutura Organizada:** Fácil navegação e manutenção
- **[Padrão de Organização](./PADRAO-ORGANIZACAO.md):** Guia para organizar novos workflows
- **[Exemplo Prático](./EXEMPLO-ORGANIZACAO.md):** Demonstração do processo de organização

## 🚨 Importante

- **Sempre leia** o README do workflow antes de usar
- **Configure as credenciais** necessárias antes da execução
- **Teste em ambiente** de desenvolvimento antes de usar em produção
- **Mantenha a estrutura** organizacional ao adicionar novos workflows
- **Cada workflow** tem sua própria pasta com documentação completa

## 📁 Estrutura Detalhada

```
workflows/
├── README.md                          # Este arquivo
├── agendamento/
│   ├── 01-agente-agendamento-agendar/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 02-agendar-evento-whatsapp/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 03-agente-agendamento/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 04-agente-agendamento-reagendamento/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 05-agente-agendamento-detalhes-evento/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 06-agente-agendamento-cancelar-evento/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 07-agente-gestao-calendario/
│       ├── README.md
│       └── workflow.json
├── ia-agentes/
│   ├── 01-agente-grok4/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 02-agente-selecao-modelos/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 03-agente-ia-postgres/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 04-agente-previsao-tempo/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 05-agente-previsao-tempo-pegar-previsao/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 06-agente-ideias-conteudo-yt/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 07-agente-ideias-conteudo-yt-titulos/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 08-agente-ideias-conteudo-yt-thumb/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 09-agente-ideias-conteudo-yt-roteiro/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 10-agente-ideias-conteudo-yt-pesquisa/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 11-ai-nodes/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 12-ai-agent-configs/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 13-agentes-ia-mais-precisos/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 14-multiagent-post-blog-corpo/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 15-integracao-perplexity/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 16-integracao-deepseek/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 17-integracao-gemini-flash/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 18-hitl-exemplo-telegram/
│       ├── README.md
│       └── workflow.json
│   ├── 19-tutor-alunos-enviar-dados/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 20-tutor-alunos-agente/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 21-rag-pipeline-chatbot-reranker/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 22-rag-agente-auto-aprendizado/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 23-propriedade-agentes/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 24-primeiro-agente-ia/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 25-orquestracao-agentes/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 26-n8n-gemini/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 27-multiagent-post-blog/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 28-multiagent-post-blog-titulos/
│       ├── README.md
│       └── workflow.json
├── financeiro/
│   ├── 01-agente-despesas-pessoais-adicionar/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 02-agentes-despesas-pessoais/
│       ├── README.md
│       └── workflow.json
├── monitoramento/
│   ├── 01-agent-tracker/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 02-error-logger/
│       ├── README.md
│       └── workflow.json
│   └── 03-seguranca-webhook/
│       ├── README.md
│       └── workflow.json
├── whatsapp/
│   ├── 01-agente-catalogo-produtos/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 02-agente-ia-whatsapp/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 03-agente-whatsapp-agendamento/
│       ├── README.md
│       └── workflow.json
│   └── 04-teste-whatsapp-p1/
│       ├── README.md
│       └── workflow.json
├── marketing/
│   ├── 01-criacao-postagem-redes-sociais/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 02-criacao-postagem-redes-sociais-com-logs/
│       ├── README.md
│       └── workflow.json
├── automacao/
│   ├── 01-classificador-emails/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 02-funcionalidades-novas-198/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 03-funcionalidades-novas-1102/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 04-funcionalidades-novas-1101/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 05-funcionalidades-novas-1100/
│       ├── README.md
│       └── workflow.json
├── backup/
│   ├── 01-backup-workflow-gdrive/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 02-backup-workflow-credenciais-gdrive/
│       ├── README.md
│       └── workflow.json
└── recursos-humanos/
    └── 01-analisador-curriculo/
        ├── README.md
        └── workflow.json
```

---

_Autor: Matheus Freitas_  
_Última atualização: Janeiro 2025_
