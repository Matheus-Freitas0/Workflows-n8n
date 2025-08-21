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

### 🤖 [IA e Agentes](./ia-agentes/)

Workflows de inteligência artificial e agentes automatizados.

- **01-agente-grok4/** - Agente de IA com Grok 4
- **02-agente-selecao-modelos/** - Agente de seleção de modelos
- **03-agente-ia-postgres/** - Agente de IA com PostgreSQL

### 📊 [Monitoramento](./monitoramento/)

Workflows de tracking, monitoramento e análise de dados.

- **01-agent-tracker/** - Tracking de execuções de agentes

### 📱 [WhatsApp](./whatsapp/)

Workflows específicos para integração com WhatsApp.

- **01-agente-catalogo-produtos/** - Catálogo automático de produtos
- **02-agente-ia-whatsapp/** - Agente de IA com WhatsApp

## 🔄 Workflows Disponíveis

| Categoria     | Nome                                                                                          | Descrição                       |
| ------------- | --------------------------------------------------------------------------------------------- | ------------------------------- |
| Agendamento   | [01-agente-agendamento-agendar](./agendamento/01-agente-agendamento-agendar/)                 | Agendamento via API Cal.com     |
| Agendamento   | [02-agendar-evento-whatsapp](./agendamento/02-agendar-evento-whatsapp/)                       | Agendamento via WhatsApp        |
| Agendamento   | [03-agente-agendamento](./agendamento/03-agente-agendamento/)                                 | Agente principal de agendamento |
| Agendamento   | [04-agente-agendamento-reagendamento](./agendamento/04-agente-agendamento-reagendamento/)     | Reagendamento de eventos        |
| Agendamento   | [05-agente-agendamento-detalhes-evento](./agendamento/05-agente-agendamento-detalhes-evento/) | Consulta de detalhes            |
| Agendamento   | [06-agente-agendamento-cancelar-evento](./agendamento/06-agente-agendamento-cancelar-evento/) | Cancelamento de eventos         |
| IA e Agentes  | [01-agente-grok4](./ia-agentes/01-agente-grok4/)                                              | Agente de IA com Grok 4         |
| IA e Agentes  | [02-agente-selecao-modelos](./ia-agentes/02-agente-selecao-modelos/)                          | Agente de seleção de modelos    |
| IA e Agentes  | [03-agente-ia-postgres](./ia-agentes/03-agente-ia-postgres/)                                  | Agente de IA com PostgreSQL     |
| Monitoramento | [01-agent-tracker](./monitoramento/01-agent-tracker/)                                         | Tracking de execuções           |
| WhatsApp      | [01-agente-catalogo-produtos](./whatsapp/01-agente-catalogo-produtos/)                        | Catálogo automático de produtos |
| WhatsApp      | [02-agente-ia-whatsapp](./whatsapp/02-agente-ia-whatsapp/)                                    | Agente de IA com WhatsApp       |

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
│   └── 06-agente-agendamento-cancelar-evento/
│       ├── README.md
│       └── workflow.json
├── ia-agentes/
│   ├── 01-agente-grok4/
│   │   ├── README.md
│   │   └── workflow.json
│   ├── 02-agente-selecao-modelos/
│   │   ├── README.md
│   │   └── workflow.json
│   └── 03-agente-ia-postgres/
│       ├── README.md
│       └── workflow.json
├── monitoramento/
│   └── 01-agent-tracker/
│       ├── README.md
│       └── workflow.json
└── whatsapp/
    ├── 01-agente-catalogo-produtos/
    │   ├── README.md
    │   └── workflow.json
    └── 02-agente-ia-whatsapp/
        ├── README.md
        └── workflow.json
```

---

_Autor: Matheus Freitas_  
_Última atualização: Janeiro 2025_
