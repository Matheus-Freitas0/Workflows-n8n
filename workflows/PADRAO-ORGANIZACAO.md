# 📋 Padrão de Organização - Workflows n8n

Este documento define o padrão para organização de workflows vindos da pasta `novos-workflows`.

## 🎯 Objetivo

Manter consistência na organização, nomenclatura e documentação dos workflows para facilitar manutenção e uso.

## 📁 Estrutura de Organização

### 1. Análise dos Workflows

Antes de organizar, analise cada workflow para:

- **Funcionalidade principal:** O que o workflow faz?
- **Integrações:** Quais APIs/serviços utiliza?
- **Trigger:** Como é executado?
- **Categoria:** Onde se encaixa melhor?

### 2. Categorias Disponíveis

#### 📅 **agendamento/**

- Workflows de agendamento de eventos
- Integrações com calendários (Cal.com, Google Calendar)
- Automação de marcação de reuniões

#### 🤖 **ia-agentes/**

- Workflows com inteligência artificial
- Agentes de chat e conversação
- Processamento de linguagem natural
- Modelos de IA (GPT, Grok, Claude)

#### 📊 **monitoramento/**

- Tracking e métricas
- Análise de performance
- Logs e auditoria
- Dashboards e relatórios

#### 📱 **whatsapp/**

- Automações específicas do WhatsApp
- Processamento de mensagens
- Chatbots para WhatsApp
- Integrações comerciais

#### 🔔 **notificacoes/**

- Sistemas de notificação
- Alertas automáticos
- Comunicação por email/SMS

#### 🛒 **ecommerce/**

- Workflows de vendas
- Processamento de pedidos
- Gestão de produtos
- Integrações com lojas

#### 🔗 **integracao/**

- Conectores entre sistemas
- Sincronização de dados
- APIs e webhooks
- Migração de dados

#### ⚙️ **automacao/**

- Automações gerais
- Processos administrativos
- Fluxos de trabalho diversos

#### 🔄 **processamento/**

- Processamento de dados
- Transformações
- ETL (Extract, Transform, Load)
- Análise de arquivos

### 3. Criação de Nova Categoria

Se nenhuma categoria existente se adequar:

1. **Análise:** Verificar se realmente precisa de nova categoria
2. **Nome:** Usar substantivo em minúsculas
3. **Emoji:** Escolher emoji representativo
4. **Descrição:** Criar descrição clara
5. **Atualizar:** README principal

## 🏗️ Processo de Organização

### Passo 1: Análise

```bash
# Ler cada arquivo JSON da pasta novos-workflows
# Identificar:
- Nome do workflow
- Funcionalidade
- Nós utilizados
- Integrações
- Categoria adequada
```

### Passo 2: Estrutura de Pastas

```bash
# Para cada workflow, criar:
categoria/
├── XX-nome-descritivo/
│   ├── README.md          # Documentação completa
│   └── workflow.json      # Arquivo do workflow
```

### Passo 3: Nomenclatura

- **Formato:** `XX-nome-descritivo`
- **XX:** Número sequencial (01, 02, 03...)
- **nome:** Descrição em minúsculas
- **separador:** Hifens entre palavras

### Passo 4: Movimentação

```bash
# Comandos para organizar:
1. mkdir -p "workflows/categoria/XX-nome-descritivo"
2. mv "workflows/novos-workflows/[Nome Original].json" "workflows/categoria/XX-nome-descritivo/workflow.json"
3. # Criar README.md
4. rm -rf workflows/novos-workflows  # Após organizar todos
```

## 📝 Template de README

Cada workflow deve ter seu README seguindo este template:

````markdown
# [EMOJI] [Nome do Workflow]

## Descrição

[Descrição clara e concisa do que o workflow faz]

## Funcionalidades

- **Trigger:** [Como é executado]
- **Integração:** [APIs/serviços utilizados]
- **Processamento:** [O que processa]
- **Saída:** [O que produz]

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição              |
| --------- | ------ | ---------------------- |
| `param1`  | string | Descrição do parâmetro |
| `param2`  | number | Descrição do parâmetro |

## Como Funciona

1. **Passo 1:** Descrição
2. **Passo 2:** Descrição
3. **Passo 3:** Descrição

## Configuração

### Credenciais Necessárias

- **Serviço 1:** Credenciais configuradas no n8n
- **Serviço 2:** API keys necessárias

### Estrutura de Dados

```json
{
  "exemplo": "estrutura de dados"
}
```
````

## Casos de Uso

- Caso de uso 1
- Caso de uso 2
- Caso de uso 3

## Dependências

- Credenciais configuradas
- Serviços acessíveis
- Outros workflows (se aplicável)

## Estrutura do Workflow

1. **Nó 1** - Função
2. **Nó 2** - Função
3. **Nó 3** - Função

## Monitoramento

- Como monitorar execuções
- Logs importantes
- Métricas relevantes

## Tratamento de Erros

- Erros comuns
- Como resolver
- Logs de debugging

---

_Autor: Matheus Freitas_  
_Categoria: [Categoria]_  
_Versão: 1.0_

```

## 🔄 Atualização do README Principal

Após organizar workflows:

1. **Atualizar** lista de workflows disponíveis
2. **Adicionar** links para novos workflows
3. **Verificar** estrutura de categorias
4. **Manter** formatação consistente

## ✅ Checklist de Organização

- [ ] Analisar todos os workflows em `novos-workflows`
- [ ] Identificar categoria apropriada para cada um
- [ ] Criar estrutura de pastas
- [ ] Mover arquivos e renomear para `workflow.json`
- [ ] Criar README.md para cada workflow
- [ ] Atualizar README principal
- [ ] Remover pasta `novos-workflows`
- [ ] Verificar links e estrutura

## 🎨 Padrões de Estilo

### Emojis por Categoria
- 📅 Agendamento
- 🤖 IA e Agentes
- 📊 Monitoramento
- 📱 WhatsApp
- 🔔 Notificações
- 🛒 E-commerce
- 🔗 Integração
- ⚙️ Automação
- 🔄 Processamento

### Formatação
- **Negrito:** Para títulos importantes
- `Código:` Para nomes técnicos
- > Citações: Para observações importantes
- - Listas: Para enumerações
- | Tabelas | Para dados estruturados

## 📚 Exemplos de Análise

### Exemplo 1: Workflow de Agendamento
```

Nome: "[FA] Agente de Agendamento - Agendar"
Análise:

- Funcionalidade: Agendamento via Cal.com
- Categoria: agendamento
- Número: 01 (primeiro da categoria)
- Nome final: 01-agente-agendamento-agendar

```

### Exemplo 2: Workflow de IA
```

Nome: "[FA] Agente com Grok 4"
Análise:

- Funcionalidade: Chat com IA Grok
- Categoria: ia-agentes
- Número: 01 (primeiro da categoria)
- Nome final: 01-agente-grok4

```

## 🚨 Observações Importantes

1. **Sempre ler** completamente o workflow antes de categorizar
2. **Manter consistência** na nomenclatura
3. **Documentar detalhadamente** cada workflow
4. **Verificar dependências** entre workflows
5. **Testar links** no README principal
6. **Backup** antes de grandes reorganizações

---
*Autor: Matheus Freitas*
*Última atualização: Janeiro 2025*
*Versão: 1.0*
```
