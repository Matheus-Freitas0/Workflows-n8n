# 📊 Error Logger

## Descrição

Sistema automatizado de logging e monitoramento de erros em workflows do n8n. Este workflow captura erros automaticamente, registra detalhes em planilha do Google e envia notificações por email para a equipe de suporte.

## Funcionalidades

- **Trigger:** Error trigger automático
- **Integração:** Gmail, Google Sheets, n8n Error Handling
- **Processamento:** Captura e registro automático de erros
- **Saída:** Logs estruturados e notificações por email

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                    |
| --------- | ------ | ---------------------------- |
| `execution`| object | Dados da execução com erro   |
| `workflow` | object | Informações do workflow      |
| `node`     | object | Dados do nó que falhou       |

## Como Funciona

1. **Detecção:** Error trigger captura automaticamente falhas
2. **Coleta:** Dados do erro são coletados (workflow, nó, mensagem)
3. **Registro:** Informações são salvas em planilha do Google Sheets
4. **Notificação:** Email é enviado para equipe de suporte
5. **Log:** Histórico completo é mantido para análise

## Configuração

### Credenciais Necessárias

- **Gmail OAuth2:** Conta de email configurada no n8n
- **Google Sheets:** Planilha de log configurada
- **Error Trigger:** Configurado para capturar erros automaticamente

### Estrutura de Dados

```json
{
  "execution": {
    "url": "URL da execução",
    "error": {
      "node": {
        "name": "Nome do nó"
      },
      "message": "Mensagem de erro"
    }
  },
  "workflow": {
    "name": "Nome do workflow"
  }
}
```

## Casos de Uso

- Monitoramento automático de workflows
- Logging centralizado de erros
- Notificações proativas para suporte
- Análise de padrões de falha
- Auditoria de execuções

## Dependências

- Credenciais Gmail configuradas
- Planilha Google Sheets configurada
- Error trigger ativo
- Workflows configurados para captura de erros

## Estrutura do Workflow

1. **Error Trigger** - Captura erros automaticamente
2. **Gmail** - Envia notificação por email
3. **Google Sheets** - Registra erro em planilha
4. **Data Processing** - Estrutura dados para log

## Monitoramento

- Verificar execuções através do histórico do n8n
- Monitorar planilha de logs do Google Sheets
- Acompanhar emails de notificação
- Analisar padrões de erro

## Tratamento de Erros

- Validação dos dados de erro recebidos
- Fallback para notificação em caso de falha no email
- Logs de execução para debugging
- Estrutura robusta de captura de erros

## Estrutura de Log

O sistema registra as seguintes informações:

- **URL:** Link para a execução com erro
- **Workflow:** Nome do workflow que falhou
- **Node:** Nome do nó que causou o erro
- **Mensagem:** Descrição detalhada do erro
- **Horário:** Timestamp da ocorrência

## Configuração da Planilha

A planilha deve conter as seguintes colunas:
- URL da execução
- Nome do workflow
- Nome do nó
- Mensagem de erro
- Horário da ocorrência

---

_Autor: Matheus Freitas_  
_Categoria: Monitoramento_  
_Versão: 1.0_
