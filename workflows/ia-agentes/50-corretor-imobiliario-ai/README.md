# 🏠 Corretor Imobiliário AI

## Descrição

Este fluxo coleta dados sobre propriedades vendidas, extrai informações-chave, registra tudo em uma planilha e gera relatórios de mercado com resumos enviados via email e Slack.

## Funcionalidades

- **Trigger manual:** Inicia a automação ao clicar em "Test workflow"
- **Busca de dados imobiliários:** Obtém propriedades vendidas em San Francisco via proxy web
- **Extração de dados:** Usa IA para extrair detalhes das propriedades incluindo preço, quartos, banheiros, tamanho, data de venda, URL, corretor, tipo e preço por pé quadrado
- **Armazenamento de dados:** Salva os resultados em planilha Google Sheets com mapeamento de campos
- **Análise de mercado com IA:** Analisa o conjunto de dados e gera insights sobre tendências de mercado, oportunidades e timing
- **Geração de resumos:** Cria conteúdo de email e resumos do Slack com insights-chave
- **Entrega de resultados:** Envia o resumo via Gmail e posta o resumo no Slack
- **Integração com fontes externas:** Utiliza ferramentas adicionais (como SerpAPI) para enriquecimento de dados quando necessário

## Parâmetros de Entrada

| Parâmetro       | Tipo   | Descrição                                     |
| --------------- | ------ | --------------------------------------------- |
| `location`      | string | Localização para busca (ex: San Francisco CA) |
| `property_type` | string | Tipo de propriedade (ex: sold properties)     |
| `date_range`    | string | Período de busca de propriedades              |

## Como Funciona

1. **Trigger Manual:** Inicia o workflow para coleta de dados imobiliários
2. **Web Scraping:** Jina Fetch coleta dados de propriedades vendidas do Zillow
3. **Extração de Informações:** IA extrai detalhes estruturados de cada propriedade
4. **Processamento de Dados:** Calcula preço por pé quadrado e organiza informações
5. **Armazenamento:** Salva dados em Google Sheets com mapeamento automático
6. **Análise de Mercado:** Agente de IA analisa tendências e gera insights
7. **Distribuição:** Envia resumos via Gmail e Slack para a equipe

## Configuração

### Credenciais Necessárias

- **Jina AI:** Para web scraping de sites imobiliários
- **OpenAI API:** Para extração e análise de dados com IA
- **Google Sheets:** Para armazenamento de dados
- **Gmail:** Para envio de relatórios
- **Slack:** Para notificações da equipe
- **SerpAPI:** Para enriquecimento de dados quando necessário

### Estrutura de Dados

```json
{
  "property_data": {
    "address": "Endereço completo da propriedade",
    "price": 1500000,
    "bedrooms": 3,
    "bathrooms": 2,
    "size": 1800,
    "sale_date": "2024-12-01",
    "url": "URL da listagem",
    "realtor": "Nome do corretor/agência",
    "type": "Single-family",
    "price_per_sqft": 833.33
  },
  "market_analysis": {
    "trends": "Análise de tendências de mercado",
    "opportunities": "Oportunidades identificadas",
    "timing": "Recomendações de timing"
  }
}
```

## Casos de Uso

- **Análise de Mercado:** Monitoramento de tendências de preços em tempo real
- **Relatórios para Clientes:** Insights sobre oportunidades de investimento
- **Análise de Competição:** Monitoramento de propriedades vendidas na região
- **Timing de Vendas:** Identificação dos melhores momentos para vender
- **Relatórios para Equipe:** Compartilhamento de insights via Slack e email

## Dependências

- Jina AI para web scraping
- OpenAI para processamento de linguagem natural
- Google Sheets para armazenamento
- Gmail para envio de relatórios
- Slack para notificações da equipe
- SerpAPI para enriquecimento de dados

## Estrutura do Workflow

1. **When clicking 'Test workflow'** - Trigger manual para iniciar
2. **Jina Fetch** - Coleta dados de propriedades vendidas
3. **Information Extractor** - IA extrai informações estruturadas
4. **Split Out** - Separa resultados para processamento individual
5. **Real Estate Data** - Salva dados no Google Sheets
6. **Real Estate AI Agent** - Analisa dados e gera insights
7. **Gmail Summary** - Cria e envia relatório por email
8. **Slack Summary Team** - Posta resumo no canal da equipe

## Monitoramento

- Status de coleta de dados via web scraping
- Performance da extração de informações com IA
- Sucesso no armazenamento no Google Sheets
- Entrega de relatórios via Gmail e Slack
- Qualidade da análise de mercado gerada

## Tratamento de Erros

- Validação de dados coletados via web scraping
- Tratamento de falhas na extração de informações
- Fallback para dados padrão em caso de erro
- Logs de debugging para troubleshooting
- Validação de credenciais de APIs

## Configurações Avançadas

### Campos de Propriedade

- **Endereço:** Localização completa da propriedade
- **Preço:** Valor final de venda
- **Quartos e Banheiros:** Características principais
- **Tamanho:** Metragem quadrada
- **Data de Venda:** Quando foi vendida
- **URL:** Link para a listagem original
- **Corretor:** Responsável pela venda
- **Tipo:** Categoria da propriedade
- **Preço por Pé Quadrado:** Métrica de valor

### Ferramentas de IA

- **Information Extractor:** Extração estruturada de dados
- **Real Estate AI Agent:** Análise de mercado e insights
- **Calculator:** Cálculos automáticos de métricas
- **SerpAPI:** Pesquisa adicional quando necessário

### Integrações

- **Jina AI:** Web scraping de sites imobiliários
- **Google Sheets:** Armazenamento estruturado de dados
- **Gmail:** Distribuição de relatórios por email
- **Slack:** Notificações para a equipe
- **OpenAI:** Processamento de linguagem natural

### Funcionalidades de Relatório

- **Análise de Tendências:** Identificação de padrões de mercado
- **Oportunidades:** Propriedades com potencial de valorização
- **Timing:** Melhores momentos para compra/venda
- **Métricas:** Preços por pé quadrado e comparações
- **Distribuição:** Envio automático para stakeholders

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
