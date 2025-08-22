# 🚀 Workflows-n8n

> **Uma coleção organizada e documentada de workflows do n8n para automação de processos empresariais**

![n8n](https://img.shields.io/badge/n8n-Workflows-blue?style=for-the-badge&logo=n8n)
![Status](https://img.shields.io/badge/Status-Ativo-brightgreen?style=for-the-badge)
![Workflows](https://img.shields.io/badge/Workflows-76+-orange?style=for-the-badge)
![Categorias](https://img.shields.io/badge/Categorias-10+-purple?style=for-the-badge)

---

## 📋 Índice

- [🎯 Sobre o Projeto](#-sobre-o-projeto)
- [🏗️ Estrutura do Projeto](#️-estrutura-do-projeto)
- [🚀 Como Usar](#-como-usar)
- [📚 Workflows Disponíveis](#-workflows-disponíveis)
- [🔧 Tecnologias](#-tecnologias)
- [📖 Padrão de Documentação](#-padrão-de-documentação)
- [🤝 Contribuindo](#-contribuindo)
- [📞 Suporte](#-suporte)

---

## 🎯 Sobre o Projeto

Este repositório centraliza uma coleção organizada de **76+ workflows** do n8n, cada um meticulosamente documentado com funcionalidades, configurações e casos de uso específicos. Nossa missão é facilitar a implementação de automações robustas e escaláveis para diferentes cenários empresariais.

### ✨ Características Principais

- 🎯 **Workflows Especializados**: Soluções específicas para diferentes domínios
- 📚 **Documentação Completa**: Cada workflow possui documentação detalhada
- 🔧 **Configuração Simples**: Setup rápido e intuitivo
- 📊 **Monitoramento**: Logs e métricas para acompanhamento
- 🚀 **Pronto para Produção**: Testado e validado em ambientes reais
- 🤖 **IA Integrada**: Múltiplos modelos de inteligência artificial
- 📱 **Multimodal**: Suporte para texto, voz, imagem e PDF
- 🔄 **Automação Inteligente**: Processos automatizados com aprovação humana

---

## 🏗️ Estrutura do Projeto

```
workflows/
├── 📅 agendamento/           # Gestão de calendários e eventos (7 workflows)
├── 🤖 automacao/             # Automações gerais e inteligentes (11 workflows)
├── 💾 backup/                # Soluções de backup e recuperação (3 workflows)
├── 💰 financeiro/            # Gestão financeira e contábil (2 workflows)
├── 🧠 ia-agentes/            # Agentes de IA e machine learning (29 workflows)
├── 🔗 integracao/            # Conectores e sincronização entre sistemas (1 workflow)
├── 📢 marketing/             # Marketing digital e CRM (6 workflows)
├── 📊 monitoramento/         # Monitoramento e alertas (4 workflows)
├── 👥 recursos-humanos/      # Gestão de RH e recrutamento (1 workflow)
└── 📱 whatsapp/              # Integrações com WhatsApp (7 workflows)
```

---

## 🚀 Como Usar

### 1️⃣ **Navegação**

Explore os diretórios organizados por categoria para encontrar o workflow ideal para sua necessidade.

### 2️⃣ **Seleção**

Escolha o workflow desejado e leia a documentação completa para entender suas funcionalidades.

### 3️⃣ **Importação**

Importe o arquivo JSON no n8n através da interface de importação.

### 4️⃣ **Configuração**

Configure as credenciais e parâmetros conforme suas necessidades específicas.

### 5️⃣ **Execução**

Ative o workflow e monitore sua execução através dos logs e métricas disponíveis.

---

## 📚 Workflows Disponíveis

### 📅 **Agendamento & Calendário** (7 workflows)

Sistema inteligente de agendamento e gestão de calendários com integração WhatsApp.

- [Agente de Agendamento](./workflows/agendamento/) - Sistema inteligente de agendamento
- [Agendar Evento WhatsApp](./workflows/agendamento/) - Agendamento via WhatsApp
- [Gestão de Calendário](./workflows/agendamento/) - Administração completa de calendários
- [Reagendamento Automático](./workflows/agendamento/) - Sistema de reagendamento inteligente
- [Detalhes de Eventos](./workflows/agendamento/) - Gestão detalhada de eventos
- [Cancelamento de Eventos](./workflows/agendamento/) - Sistema de cancelamento automatizado

### 🤖 **Automação & IA** (11 workflows)

Automações inteligentes com IA para classificação, resposta e organização de emails.

- [Classificador de Emails](./workflows/automacao/) - Categorização automática de emails
- [Funcionalidades Novas](./workflows/automacao/) - Demonstração de recursos das versões 1.98-1.102+
- [Assistente Email IA Outlook](./workflows/automacao/) - Assistente inteligente para Outlook
- [Resposta Automática com Aprovação](./workflows/automacao/) - Sistema de aprovação humana
- [Classificação e Resposta Automática](./workflows/automacao/) - Processamento completo de emails
- [Autocategorização Outlook](./workflows/automacao/) - Categorização automática inteligente

### 🧠 **IA & Agentes Inteligentes** (29 workflows)

Soluções avançadas com múltiplos modelos de IA, multiagentes e sistemas RAG.

- [Agente Grok 4](./workflows/ia-agentes/) - Chat com IA Grok
- [Seleção de Modelos](./workflows/ia-agentes/) - Sistema inteligente de seleção
- [Agente IA PostgreSQL](./workflows/ia-agentes/) - Integração IA com banco de dados
- [Previsão do Tempo](./workflows/ia-agentes/) - Sistema meteorológico com IA
- [Geração de Conteúdo YouTube](./workflows/ia-agentes/) - Criação automática de conteúdo
- [Multiagent para Blog](./workflows/ia-agentes/) - Geração colaborativa de conteúdo
- [Integrações IA](./workflows/ia-agentes/) - Perplexity, DeepSeek, Gemini Flash
- [HITL com Telegram](./workflows/ia-agentes/) - Human-in-the-Loop automatizado
- [Sistema Educacional](./workflows/ia-agentes/) - Tutoria e agentes educacionais
- [Pipeline RAG Avançado](./workflows/ia-agentes/) - Chatbot com reranker e auto-aprendizado
- [Orquestração de Agentes](./workflows/ia-agentes/) - Coordenação de múltiplos agentes
- [Criação de Vídeos POV](./workflows/ia-agentes/) - Geração automática de vídeos
- [Curadoria Automática](./workflows/ia-agentes/) - Seleção inteligente de conteúdo

### 📢 **Marketing & Redes Sociais** (6 workflows)

Automação de marketing digital, redes sociais e otimização de conteúdo.

- [Criação de Postagens](./workflows/marketing/) - Automação de conteúdo para redes sociais
- [Gestão de Campanhas](./workflows/marketing/) - Otimização de campanhas de marketing
- [Publicador Automático WordPress](./workflows/marketing/) - Publicação automática no WordPress
- [Respostas Automáticas Instagram](./workflows/marketing/) - Sistema de comentários inteligente
- [Geração de Metadados YouTube](./workflows/marketing/) - Otimização automática de SEO

### 📱 **WhatsApp & Comunicação** (7 workflows)

Soluções completas para WhatsApp com IA multimodal e automação de vendas.

- [Catálogo de Produtos](./workflows/whatsapp/) - Gestão de produtos via WhatsApp
- [Agente IA WhatsApp](./workflows/whatsapp/) - Atendimento inteligente automatizado
- [Agendamento WhatsApp](./workflows/whatsapp/) - Sistema de agendamento integrado
- [Testes WhatsApp](./workflows/whatsapp/) - Validação e testes de integração
- [Assistente Multimodal](./workflows/whatsapp/) - Suporte para múltiplos tipos de mídia
- [Chatbot IA Multimodal](./workflows/whatsapp/) - Processamento de texto, voz, imagem e PDF

### 📊 **Monitoramento & Logs** (4 workflows)

Sistemas de monitoramento, tracking e segurança para workflows.

- [Agent Tracker](./workflows/monitoramento/) - Tracking de execuções de agentes
- [Error Logger](./workflows/monitoramento/) - Sistema automatizado de log de erros
- [Segurança Webhook](./workflows/monitoramento/) - Sistema de segurança para webhooks
- [Registro de Uso e Custo IA](./workflows/monitoramento/) - Controle de custos de IA por cliente

### 💰 **Financeiro** (2 workflows)

Automações para gestão financeira e controle de despesas.

- [Gestão de Despesas](./workflows/financeiro/) - Controle de despesas pessoais
- [Agentes Financeiros](./workflows/financeiro/) - Automações para gestão financeira

### 💾 **Backup & Segurança** (3 workflows)

Soluções de backup automatizado e gestão de credenciais.

- [Backup para Google Drive](./workflows/backup/) - Soluções de backup automatizado
- [Gestão de Credenciais](./workflows/backup/) - Segurança e backup de credenciais
- [Backup Automático GitLab](./workflows/backup/) - Backup automático de repositórios

### 🔗 **Integração** (1 workflow)

Conectores e sincronização entre sistemas.

- [Sincronizador Playlist](./workflows/integracao/) - Sincronização Spotify-YouTube

### 👥 **Recursos Humanos** (1 workflow)

Processamento inteligente de candidatos e gestão de RH.

- [Análise de Currículos](./workflows/recursos-humanos/) - Processamento inteligente de candidatos

---

## 🔧 Tecnologias

| Tecnologia                                  | Descrição                            | Versão     |
| ------------------------------------------- | ------------------------------------ | ---------- |
| [n8n](https://n8n.io/)                      | Plataforma de automação de workflows | Latest     |
| [OpenAI GPT](https://openai.com/)           | Modelos de linguagem avançados       | GPT-4      |
| [Claude AI](https://claude.ai/)             | Assistente IA conversacional         | Claude 3   |
| [Google Gemini](https://gemini.google.com/) | Modelo multimodal do Google          | Gemini Pro |
| [Perplexity AI](https://perplexity.ai/)     | IA para pesquisa e análise           | Latest     |
| [DeepSeek](https://deepseek.com/)           | Modelo de linguagem especializado    | Latest     |
| [Markdown](https://www.markdownguide.org/)  | Documentação estruturada             | -          |
| [JSON](https://www.json.org/)               | Arquivos de workflow exportáveis     | -          |
| [Git](https://git-scm.com/)                 | Controle de versão                   | -          |

---

## 📖 Padrão de Documentação

Cada workflow segue um padrão de documentação consistente e profissional:

### 📋 **Estrutura Padrão**

- **📝 Descrição**: Visão geral clara do propósito
- **⚡ Funcionalidades**: Lista detalhada de recursos principais
- **🔧 Pré-requisitos**: Configurações e dependências necessárias
- **⚙️ Configuração**: Passos detalhados para setup
- **🚀 Uso**: Instruções de execução e monitoramento
- **🔍 Troubleshooting**: Problemas comuns e soluções
- **📊 Logs**: Estrutura de logs para monitoramento

### 🎨 **Formatação**

- Emojis para melhor visualização
- Código formatado com syntax highlighting
- Estrutura hierárquica clara
- Links internos para navegação

---

## 🤝 Contribuindo

### 📝 **Como Contribuir**

1. **Fork** o repositório
2. **Clone** para sua máquina local
3. **Crie** uma branch para sua feature (`git checkout -b feature/nova-feature`)
4. **Desenvolva** seguindo os padrões estabelecidos
5. **Teste** suas alterações
6. **Commit** suas mudanças (`git commit -m 'Adiciona nova feature'`)
7. **Push** para a branch (`git push origin feature/nova-feature`)
8. **Abra** um Pull Request

### 📋 **Diretrizes para Novos Workflows**

- ✅ Crie um diretório na categoria apropriada
- ✅ Adicione o arquivo JSON do workflow
- ✅ Crie um README.md seguindo o template padrão
- ✅ Atualize este README principal
- ✅ Teste o workflow antes de submeter
- ✅ Documente todas as funcionalidades

---

## 📊 Estatísticas do Projeto

- **Total de Workflows**: 76+
- **Categorias**: 10
- **Workflows com IA**: 29+
- **Integrações**: 15+
- **Documentação**: 100% coberta
- **Status**: Ativo e em crescimento

---

## 📞 Suporte

### 🆘 **Precisa de Ajuda?**

- 📧 **Email**: [moncaomatheus@gmail.com](mailto:moncaomatheus@gmail.com)
- 📚 **Documentação**: [Wiki do Projeto](./workflows/README.md)

### 🔗 **Links Úteis**

- [Documentação Oficial do n8n](https://docs.n8n.io/)
- [Comunidade n8n](https://community.n8n.io/)
- [Marketplace n8n](https://n8n.io/integrations)

---

## 👨‍💻 Autor

**Matheus Freitas** - [GitHub](https://github.com/Matheus-Freitas0) | [LinkedIn](https://www.linkedin.com/in/matheus-m-freitas)

---

<div align="center">

**⭐ Se este projeto te ajudou, considere dar uma estrela! ⭐**

_Última atualização: Janeiro 2025_  
_Versão: 3.0.0_

</div>
