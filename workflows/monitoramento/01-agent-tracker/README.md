# 📊 Agent Tracker

## Descrição

Sistema de tracking para monitorar execuções de agentes de IA. Este workflow coleta e registra métricas de execução em planilha do Google para análise de performance e custos.

## Funcionalidades

- **Trigger:** Executado por outro workflow
- **Integração:** Google Sheets
- **Coleta de Dados:** Métricas de execução de agentes de IA
- **Armazenamento:** Planilha estruturada para análise
- **Monitoramento:** Performance e custos em tempo real

## Dados Coletados

| Campo | Descrição | Exemplo |
|-------|-----------|---------|
| **Horário** | Timestamp da execução | 27/01/2025 14:30:25 |
| **Workflow** | Nome do workflow executado | Agente Grok 4 |
| **Entrada** | Dados de entrada processados | "Como funciona a IA?" |
| **Saída** | Resultado gerado | "A IA funciona através de..." |
| **Tokens** | Número de tokens utilizados | 1500 |
| **Custo Total** | Custo da operação | 0.003 |

## Como Funciona

1. **Execução:** Workflow é executado após agente de IA
2. **Mapeamento:** Dados são extraídos e formatados
3. **Envio:** Informações são enviadas para Google Sheets
4. **Registro:** Dados são armazenados para análise

## Configuração

### Credenciais Necessárias

- **Google Sheets:** OAuth2 configurado no n8n
- **Planilha:** Configurada com as colunas apropriadas

### Estrutura da Planilha

A planilha deve conter as seguintes colunas:
- **Horário:** Timestamp da execução
- **Workflow:** Nome do workflow executado
- **Entrada:** Dados de entrada processados
- **Saída:** Resultado gerado
- **Tokens:** Número de tokens utilizados
- **Custo Total:** Custo da operação

## Estrutura do Workflow

1. **Execute Workflow Trigger** - Recebe dados de execução
2. **Set (Mapear Campos)** - Formata dados para planilha
3. **Google Sheets** - Envia dados para planilha

## Casos de Uso

- **Monitoramento de Custos:** Acompanhar gastos com IA
- **Análise de Performance:** Medir eficiência dos workflows
- **Auditoria:** Rastrear todas as execuções
- **Otimização:** Identificar pontos de melhoria
- **Relatórios:** Gerar insights de uso

## Dependências

- Credenciais do Google Sheets configuradas
- Planilha do Google configurada com as colunas apropriadas
- Workflow pai que execute este workflow
- Acesso à internet para Google Sheets

## Configuração da Planilha

- **ID da Planilha:** 1g1mDNMnNd1qturYZpYQolS1AxJgIxdOM2QW34VXMvnM
- **Nome:** Track de Agente
- **Página:** Página1
- **Operação:** Append (adicionar novas linhas)

## Monitoramento

- Verificar execuções do workflow
- Monitorar dados enviados para planilha
- Acompanhar métricas de performance
- Verificar custos acumulados

## Análise de Dados

- **Tendências:** Evolução de custos ao longo do tempo
- **Comparações:** Performance entre diferentes workflows
- **Alertas:** Configurar limites de custo
- **Relatórios:** Exportar dados para análise

## Otimizações

- Configurar filtros de dados se necessário
- Ajustar frequência de tracking
- Implementar alertas automáticos
- Otimizar estrutura da planilha

## Segurança

- Dados são armazenados em Google Sheets
- Acesso controlado por credenciais OAuth2
- Backup automático do Google
- Conformidade com políticas de segurança

---
*Autor: Matheus Freitas*  
*Categoria: Monitoramento*  
*Versão: 1.0*
