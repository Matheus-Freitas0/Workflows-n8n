# 💰 Agente de Despesas Pessoais - Adicionar

## Descrição

Workflow para adicionar despesas pessoais automaticamente em uma planilha do Google Sheets. Este workflow é executado por outro workflow pai e registra informações financeiras de forma estruturada.

## Funcionalidades

- **Trigger:** Executado por outro workflow
- **Integração:** Google Sheets API
- **Processamento:** Adição de despesas em planilha
- **Validação:** Verificação de dados de entrada
- **Organização:** Estruturação automática de dados financeiros

## Parâmetros de Entrada

| Parâmetro   | Tipo   | Descrição                         |
| ----------- | ------ | --------------------------------- |
| `data`      | string | Data da despesa                   |
| `tipo`      | string | Tipo de despesa (categoria)       |
| `valor`     | number | Valor da despesa                  |
| `sugestao`  | string | Sugestão da IA para categorização |
| `descricao` | string | Descrição detalhada da despesa    |

## Como Funciona

1. **Recebimento:** Workflow recebe parâmetros de despesa
2. **Validação:** Verifica se todos os parâmetros estão presentes
3. **Processamento:** Formata dados para inserção na planilha
4. **Inserção:** Adiciona nova linha na planilha do Google Sheets
5. **Confirmação:** Retorna status da operação

## Configuração

### Credenciais Necessárias

- **Google Sheets:** OAuth2 configurado no n8n
- **Planilha ID:** 1tBfT9bi6jnNJYNF7P1TFZwTre4d15ra0lnTspJCusJo

### Estrutura da Planilha

| Coluna              | Descrição              | Mapeamento  |
| ------------------- | ---------------------- | ----------- |
| **Descrição**       | Descrição da despesa   | `descricao` |
| **Sugestão da IA**  | Categorização sugerida | `sugestao`  |
| **Valor**           | Valor da despesa       | `valor`     |
| **Tipo de Despesa** | Categoria da despesa   | `tipo`      |
| **Data**            | Data da despesa        | `data`      |

## Casos de Uso

- Registro automático de despesas pessoais
- Categorização inteligente de gastos
- Controle financeiro automatizado
- Integração com sistemas de IA
- Relatórios financeiros estruturados

## Dependências

- Credenciais do Google Sheets configuradas
- Planilha configurada com estrutura adequada
- Workflow pai que execute este workflow
- Dados válidos de entrada

## Estrutura do Workflow

1. **Execute Workflow Trigger** - Recebe parâmetros de entrada
2. **Google Sheets** - Adiciona nova linha na planilha

## Tratamento de Erros

- **Parâmetros inválidos:** Validação de entrada
- **Planilha indisponível:** Tratamento de erro de acesso
- **Dados malformados:** Verificação de formato
- **Falha na inserção:** Retry automático

## Monitoramento

- Verificar execuções do workflow
- Monitorar inserções na planilha
- Acompanhar sucesso das operações
- Verificar logs de erro

## Validações Importantes

- **Data válida:** Verificar formato da data
- **Valor numérico:** Confirmar valor é número
- **Descrição obrigatória:** Verificar descrição presente
- **Tipo válido:** Validar categoria da despesa

## Segurança

- **Validação de entrada:** Verificação de parâmetros
- **Logs de auditoria:** Registro de todas as operações
- **Controle de acesso:** Validação de permissões
- **Rastreabilidade:** Histórico de inserções

## Integração

- **Workflow Pai:** Fornece dados da despesa
- **Google Sheets:** Armazena dados financeiros
- **Sistema de IA:** Fornece sugestões de categorização
- **Logs:** Registra operação para auditoria

## Performance

- **Timeout:** Configuração de timeout da API
- **Retry:** Tentativas automáticas em caso de falha
- **Rate Limiting:** Respeitar limites do Google Sheets
- **Cache:** Evitar consultas desnecessárias

---

_Autor: Matheus Freitas_  
_Categoria: Financeiro_  
_Versão: 1.0_
