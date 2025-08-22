# 📊 Registro de Uso e Custo de IA por Cliente

## Descrição

Sistema automatizado que registra o uso de tokens e calcula custos por cliente ao processar CVs em PDF, salvando os dados em uma planilha e possibilitando envio de faturas mensais para controle financeiro e auditoria.

## Funcionalidades

- **Trigger:** Formulário de upload de CVs com aceitação de termos de cobrança
- **Integração:** Upload de PDFs, processamento com IA, planilhas para registro, sistema de faturas
- **Processamento:** Extração de texto, estruturação de dados, cálculo de custos por cliente
- **Saída:** Registro detalhado de uso, cálculo de custos e envio de faturas mensais

## Parâmetros de Entrada

| Parâmetro       | Tipo    | Descrição                                |
| --------------- | ------- | ---------------------------------------- |
| `pdf_file`      | file    | Arquivo PDF do CV para processamento     |
| `client_info`   | object  | Informações do cliente (ID, nome, email) |
| `billing_terms` | boolean | Aceitação dos termos de cobrança         |
| `workflow_id`   | string  | Identificador único do workflow          |

## Como Funciona

1. **CV Upload Form:** Permite que usuários enviem PDFs e aceitem termos de cobrança
2. **PDF Text Extraction:** Converte o arquivo PDF enviado em texto bruto para processamento
3. **JSON Data Extraction:** Estrutura o conteúdo do currículo em um esquema JSON definido
4. **Logging Attribute Capture:** Anexa identificadores como `workflow_id`, `execution_id` e `client_id` aos registros
5. **LLM Model Usage Measurement:** Intercepta metadados de uso (tokens de entrada/saída) para cada chamada ao modelo
6. **Cost Calculation per Call:** Converte tokens em custo usando taxas configuradas por milhão de tokens e soma custos totais
7. **Spreadsheet Logging:** Anexa linhas com data, IDs, tokens e custos em uma planilha para auditoria e cobrança
8. **Monthly Aggregation:** Filtra registros do mês atual e soma tokens e custos para cálculo
9. **Email Invoice Sending:** Gera um e-mail com total de impostos e valor a pagar, enviando para o cliente
10. **User Result Display:** Retorna o JSON estruturado do currículo para o usuário que enviou o arquivo

## Configuração

### Credenciais Necessárias

- **PDF Processing Service:** Serviço para extração de texto de PDFs
- **IA Language Model:** Modelo de linguagem para estruturação de dados de CV
- **Google Sheets API:** Acesso para registro de dados em planilhas
- **SMTP Server:** Servidor para envio de faturas por e-mail
- **Database/Storage:** Sistema para armazenamento de metadados e histórico

### Estrutura de Dados

```json
{
  "client_management": {
    "client_id": "CLI_001",
    "client_name": "Empresa ABC Ltda",
    "client_email": "financeiro@empresaabc.com",
    "billing_terms_accepted": true,
    "billing_frequency": "monthly"
  },
  "ai_usage_tracking": {
    "workflow_id": "WF_201",
    "execution_id": "EX_20250115_001",
    "input_tokens": 1500,
    "output_tokens": 800,
    "total_tokens": 2300,
    "model_used": "gpt-4",
    "cost_per_1k_tokens": 0.03
  },
  "cost_calculation": {
    "total_cost": 0.069,
    "currency": "USD",
    "tax_rate": 0.2,
    "tax_amount": 0.0138,
    "final_amount": 0.0828
  },
  "billing_data": {
    "invoice_period": "2025-01",
    "total_clients": 15,
    "total_usage": 45000,
    "total_cost": 1.35,
    "total_tax": 0.27,
    "grand_total": 1.62
  }
}
```

## Casos de Uso

- **Controle de Custos:** Monitoramento preciso de gastos com APIs de IA por cliente
- **Faturamento Automático:** Geração e envio automático de faturas mensais
- **Auditoria Financeira:** Rastreamento completo de uso para fins contábeis
- **Gestão de Clientes:** Controle de consumo e limites por cliente
- **Análise de ROI:** Medição do retorno sobre investimento em IA
- **Compliance:** Documentação para requisitos fiscais e legais

## Dependências

- Serviço de processamento de PDFs configurado
- Modelo de IA configurado para extração de dados de CV
- Conta Google com APIs habilitadas (Sheets)
- Servidor SMTP para envio de e-mails
- Sistema de armazenamento para metadados
- Configuração de taxas de cobrança por modelo de IA

## Estrutura do Workflow

1. **Form Upload Trigger** - Recebe upload de CV e aceitação de termos
2. **PDF Processing** - Extrai texto do arquivo PDF
3. **AI Data Extraction** - Estrutura dados usando modelo de IA
4. **Usage Metadata Capture** - Captura metadados de uso da IA
5. **Token Calculation** - Calcula total de tokens utilizados
6. **Cost Calculation** - Converte tokens em custos monetários
7. **Spreadsheet Logging** - Registra dados na planilha de controle
8. **Monthly Aggregation** - Agrega dados do mês atual
9. **Invoice Generation** - Gera fatura com totais calculados
10. **Email Sending** - Envia fatura por e-mail para o cliente
11. **Result Return** - Retorna dados estruturados para o usuário

## Monitoramento

- **Uso por Cliente:** Total de tokens e custos por cliente
- **Eficiência de Processamento:** Taxa de sucesso na extração de dados
- **Custos por Modelo:** Distribuição de gastos por modelo de IA utilizado
- **Volume Mensal:** Total de CVs processados e custos incorridos
- **Tempo de Processamento:** Latência média por CV processado
- **Taxa de Erro:** Percentual de falhas no processamento

## Tratamento de Erros

- **PDF Corrompido:** Notificação de erro e solicitação de reenvio
- **Falha na IA:** Processamento manual com notificação de cliente
- **Erro de Planilha:** Retry automático com fallback para backup
- **Falha no Envio de E-mail:** Retry com notificação de erro
- **Timeout de Processamento:** Cancelamento e notificação de falha
- **Dados Inválidos:** Validação e correção automática quando possível

## Características Técnicas

### Sistema de Tracking de Uso

- **Interceptação Automática:** Captura automática de metadados de uso da IA
- **Identificação Única:** Rastreamento por workflow_id e execution_id
- **Granularidade Detalhada:** Separação de tokens de entrada e saída
- **Timestamp Preciso:** Registro de data e hora de cada execução

### Cálculo de Custos

- **Taxas Configuráveis:** Preços por milhão de tokens configuráveis por modelo
- **Cálculo Automático:** Conversão automática de tokens em valores monetários
- **Suporte a Múltiplas Moedas:** Configuração de moeda base
- **Cálculo de Impostos:** Aplicação automática de taxas fiscais

### Sistema de Faturamento

- **Agregação Mensal:** Consolidação automática de custos por período
- **Geração de Faturas:** Criação automática de documentos de cobrança
- **Envio Automático:** Distribuição automática por e-mail
- **Histórico Completo:** Rastreamento de todas as faturas enviadas

### Integração e Armazenamento

- **Google Sheets Integration:** Registro automático em planilhas
- **Backup Automático:** Sistema de backup para dados críticos
- **API Rate Limiting:** Controle de taxa para evitar sobrecarga
- **Logging Completo:** Registro detalhado para debugging e auditoria

---

_Autor: Matheus Freitas_  
_Categoria: Monitoramento_  
_Versão: 1.0_
