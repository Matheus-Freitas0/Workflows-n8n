# 📱 Resumidor de Grupos WhatsApp

## Descrição

Este fluxo coleta mensagens de grupos do WhatsApp, filtra os grupos desejados, agrega as mensagens e gera um resumo estruturado com IA. Também armazena informações em base de dados e envia o resumo final por meio de uma API externa, com gatilhos via Webhook e agendamento para automação.

## Funcionalidades

- **Coleta e Filtragem de Mensagens dos Grupos:** Busca as mensagens dos grupos escolhidos e aplica filtros
- **Agrupamento e Preparação de Dados:** Agrupa mensagens para preparação do resumo
- **Geração do Resumo com IA:** Envia o conteúdo para o modelo de linguagem gerar um resumo estruturado
- **Persistência de Dados:** Armazena informações de grupos e mensagens em uma base de dados com limpeza de mensagens antigas conforme o fluxo
- **Envio do Resumo via API Externa:** Envia o resumo final para o WhatsApp usando a API do Flux Automate
- **Gatilhos e Automação:** Inicia a automação via Webhook e agendamentos programados
- **Monitoramento de Grupos:** Acompanha atividade em múltiplos grupos simultaneamente
- **Limpeza Automática:** Remove mensagens antigas para otimizar armazenamento

## Parâmetros de Entrada

| Parâmetro  | Tipo   | Descrição                   |
| ---------- | ------ | --------------------------- |
| `grupos`   | array  | Lista de grupos a monitorar |
| `webhook`  | object | Dados recebidos via webhook |
| `schedule` | string | Horário agendado (22h30)    |
| `filtros`  | object | Critérios de filtragem      |

## Como Funciona

1. **Trigger de Agendamento:** Executa diariamente às 22h30
2. **Webhook Trigger:** Recebe mensagens em tempo real
3. **Busca de Grupos:** Consulta base de dados para grupos configurados
4. **Filtragem de Mensagens:** Aplica critérios para selecionar mensagens relevantes
5. **Loop de Processamento:** Processa cada grupo individualmente
6. **Agregação de Dados:** Combina mensagens por grupo
7. **Geração de Resumo:** IA cria resumo estruturado das conversas
8. **Armazenamento:** Salva informações na base de dados
9. **Envio de Resumo:** Envia resumo via API Evolution
10. **Limpeza Automática:** Remove mensagens antigas do banco
11. **Controle de Fluxo:** Aguarda intervalos para evitar sobrecarga

## Configuração

### Credenciais Necessárias

- **Baserow API:** Para armazenamento de grupos e mensagens
- **OpenAI API:** Para geração de resumos com IA
- **Evolution API:** Para envio de mensagens via WhatsApp
- **Webhook:** Para recebimento de mensagens em tempo real

### Estrutura de Dados

```json
{
  "grupo_config": {
    "id": "grupo_id",
    "nome": "Nome do Grupo",
    "ativo": true,
    "filtros": {
      "palavras_chave": ["palavra1", "palavra2"],
      "participantes": ["user1", "user2"]
    }
  },
  "mensagem": {
    "id": "msg_id",
    "grupo_id": "grupo_id",
    "participante": "nome_participante",
    "mensagem": "Conteúdo da mensagem",
    "data_hora": "2024-12-13T22:30:00Z"
  },
  "resumo_gerado": {
    "grupo": "Nome do Grupo",
    "periodo": "13/12/2024",
    "total_mensagens": 150,
    "participantes_ativos": 25,
    "resumo": "Resumo estruturado das conversas",
    "timestamp": "2024-12-13T22:30:00Z"
  }
}
```

## Casos de Uso

- **Monitoramento de Comunidades:** Acompanhamento de atividade em grupos de interesse
- **Relatórios Automáticos:** Geração diária de resumos de conversas
- **Análise de Engajamento:** Métricas de participação e atividade em grupos
- **Moderação de Conteúdo:** Identificação de padrões e tendências
- **Comunicação Corporativa:** Resumos de grupos de trabalho e projetos
- **Pesquisa de Mercado:** Análise de conversas para insights de negócio

## Dependências

- Baserow API configurada para armazenamento
- OpenAI API para processamento de linguagem natural
- Evolution API para envio de mensagens WhatsApp
- Sistema de webhook para recebimento de mensagens
- Agendador para execução automática
- Sistema de filtragem e processamento de dados

## Estrutura do Workflow

1. **Hoje as 22h** - Trigger de agendamento diário
2. **Webhook** - Recebe mensagens em tempo real
3. **If2** - Decide entre cadastro e busca
4. **Cadastrar Grupos** - Adiciona novos grupos ao sistema
5. **Busca Grupos** - Consulta grupos configurados
6. **Filter** - Aplica filtros de mensagens
7. **Loop de Grupos** - Processa cada grupo individualmente
8. **Está Vazio?** - Verifica se há mensagens para processar
9. **Mensagem** - Formata mensagens para resumo
10. **Agrega** - Combina mensagens por grupo
11. **Mapeia Todas as Mensagens** - Prepara dados para IA
12. **OpenAI** - Modelo de linguagem para resumo
13. **Agente Resumidor** - Coordena geração de resumo
14. **Evolution** - Envia resumo via WhatsApp
15. **Aguarde 20s** - Controle de fluxo
16. **Busca Todas as Mensagens** - Consulta mensagens antigas
17. **Apaga Mensagens** - Limpeza automática do banco

## Monitoramento

- Status de execução do agendamento diário
- Performance da coleta de mensagens via webhook
- Taxa de sucesso na geração de resumos com IA
- Qualidade dos resumos gerados
- Tempo de processamento por grupo
- Status de limpeza automática do banco de dados
- Performance da API Evolution para envio

## Tratamento de Erros

- Validação de grupos configurados
- Tratamento de falhas na consulta ao Baserow
- Fallback para mensagens sem conteúdo
- Validação de credenciais de APIs
- Logs de debugging para troubleshooting
- Tratamento de falhas no envio de resumos
- Controle de sobrecarga com delays

## Configurações Avançadas

### Sistema de Coleta

- **Agendamento Inteligente:** Execução diária às 22h30
- **Webhook em Tempo Real:** Recebimento instantâneo de mensagens
- **Filtros Configuráveis:** Critérios personalizáveis por grupo
- **Processamento em Lote:** Otimização para múltiplos grupos

### Geração de Resumos

- **IA OpenAI:** Modelo de linguagem para resumos estruturados
- **Contexto Inteligente:** Manutenção de contexto entre mensagens
- **Formatação Estruturada:** Resumos organizados e legíveis
- **Personalização por Grupo:** Adaptação do formato por tipo de grupo

### Persistência de Dados

- **Base Baserow:** Armazenamento estruturado de grupos e mensagens
- **Limpeza Automática:** Remoção de mensagens antigas
- **Otimização de Storage:** Controle de volume de dados
- **Backup Automático:** Preservação de dados importantes

### Sistema de Notificações

- **API Evolution:** Envio via WhatsApp Business
- **Formatação Rica:** Resumos com emojis e estrutura clara
- **Distribuição Inteligente:** Envio para destinatários apropriados
- **Confirmação de Entrega:** Verificação de sucesso no envio

### Automação e Controle

- **Gatilhos Múltiplos:** Webhook + agendamento
- **Controle de Fluxo:** Delays para evitar sobrecarga
- **Processamento Assíncrono:** Execução em background
- **Monitoramento de Performance:** Métricas de execução

### Funcionalidades de Monitoramento

- **Coleta Contínua:** Monitoramento 24/7 via webhook
- **Processamento Diário:** Resumos automáticos agendados
- **Filtros Inteligentes:** Seleção automática de conteúdo relevante
- **Análise de Tendências:** Padrões de conversa ao longo do tempo

### Integrações

- **WhatsApp:** Coleta e envio de mensagens
- **Baserow:** Armazenamento e consulta de dados
- **OpenAI:** Processamento de linguagem natural
- **Evolution API:** Sistema de mensageria
- **Webhook:** Recebimento de dados em tempo real

---

_Autor: Matheus Freitas_  
_Categoria: Monitoramento_  
_Versão: 1.0_
