# 📊 Agente Métricas Facebook com Sheets e IA

## Descrição

Fluxo que lê dados da planilha para api_meta e id_conta, consulta o Facebook Insights para campanhas e usa IA para definir o intervalo temporal adequado antes de gerar insights a partir dos dados.

## Funcionalidades

- **Leitura de dados da planilha Google Sheets:** para api_meta e id_conta
- **Consulta ao Facebook Graph API Insights:** para campanhas com campos de métricas e token de acesso
- **Definição do intervalo temporal com IA:** com base no pedido do usuário
- **Geração de insights:** por meio de modelo de linguagem
- **Acionamento da automação:** por mensagens de chat

## Parâmetros de Entrada

| Parâmetro  | Tipo   | Descrição                   |
| ---------- | ------ | --------------------------- |
| `message`  | string | Mensagem de chat recebida   |
| `api_meta` | string | Token de acesso do Facebook |
| `id_conta` | string | ID da conta do Facebook Ads |

## Como Funciona

1. **Chat Trigger:** Recebe mensagem de chat para acionar o workflow
2. **Leitura de Dados:** AI Agent acessa Google Sheets para obter credenciais
3. **Consulta Facebook:** Utiliza Facebook Graph API para buscar insights de campanhas
4. **Processamento IA:** OpenAI GPT-4o analisa dados e define intervalos temporais
5. **Geração de Insights:** Modelo de linguagem gera análises baseadas nos dados coletados

## Configuração

### Credenciais Necessárias

- **Google Sheets OAuth2:** Para acesso às planilhas
- **OpenAI API:** Para processamento de linguagem natural
- **Facebook Graph API:** Para acesso aos insights de campanhas

### Estrutura de Dados

```json
{
  "api_meta": "token_facebook_graph_api",
  "id_conta": "id_conta_facebook_ads",
  "preset": "today|yesterday|this_month|last_month|this_quarter|maximum|data_maximum|last_3d|last_7d|last_14d|last_28d|last_30d|last_90d|last_week_mon_sun|last_week_sun_sat|last_quarter|last_year|this_week_mon_today|this_week_sun_today|this_year"
}
```

## Casos de Uso

- Análise de performance de campanhas do Facebook Ads
- Relatórios automáticos de métricas publicitárias
- Otimização de campanhas baseada em insights
- Monitoramento de ROI e conversões
- Análise de tendências temporais de campanhas

## Dependências

- Google Sheets configurado com dados de credenciais
- Facebook Graph API com permissões de insights
- OpenAI API para processamento de linguagem
- Sistema de chat para acionamento

## Estrutura do Workflow

1. **When chat message received** - Trigger por mensagem de chat
2. **AI Agent1** - Agente principal que coordena todo o processo
3. **OpenAI Chat Model1** - Modelo GPT-4o para processamento
4. **dados_projeto** - Ferramenta para ler dados do Google Sheets
5. **insightsCampanha** - Ferramenta para consultar Facebook Insights

## Monitoramento

- Logs de execução do chat trigger
- Status das chamadas à API do Facebook
- Performance do modelo de IA
- Acesso aos dados do Google Sheets

## Tratamento de Erros

- Validação de credenciais do Facebook
- Verificação de permissões de acesso
- Tratamento de erros de API externas
- Fallback para intervalos temporais padrão

## Configurações Avançadas

### Campos de Métricas do Facebook

- **impressions:** Impressões das campanhas
- **clicks:** Cliques recebidos
- **campaign_name:** Nome da campanha
- **cpm:** Custo por mil impressões
- **campaign_id:** ID único da campanha
- **purchase_roas:** Retorno sobre gasto em compras
- **spend:** Valor gasto na campanha
- **actions:** Ações realizadas pelos usuários

### Presets Temporais Suportados

- **Períodos específicos:** today, yesterday, this_month, last_month
- **Trimestres:** this_quarter, last_quarter
- **Períodos customizados:** last_3d, last_7d, last_14d, last_28d, last_30d, last_90d
- **Semanas:** last_week_mon_sun, last_week_sun_sat, this_week_mon_today, this_week_sun_today
- **Anos:** this_year, last_year
- **Máximo disponível:** maximum, data_maximum

### Integrações

- **Google Sheets:** Armazenamento de credenciais e configurações
- **Facebook Graph API:** Consulta de insights e métricas
- **OpenAI:** Processamento de linguagem e geração de insights
- **Sistema de Chat:** Interface de usuário para acionamento

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
