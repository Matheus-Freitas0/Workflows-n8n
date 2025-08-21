# 🌤️ Agente de Previsão do Tempo - Pegar Previsão

## Descrição

Workflow para obter previsão do tempo específica de uma cidade. Este workflow é executado pelo agente principal de previsão do tempo e retorna dados meteorológicos detalhados.

## Funcionalidades

- **Trigger:** Executado por outro workflow
- **Integração:** APIs de previsão do tempo
- **Processamento:** Consulta de dados meteorológicos
- **Validação:** Verificação de cidade fornecida
- **Resposta:** Dados climáticos estruturados

## Parâmetros de Entrada

| Parâmetro | Tipo   | Descrição                              |
| --------- | ------ | -------------------------------------- |
| `city`    | string | Nome da cidade para consultar previsão |

## Como Funciona

1. **Recebimento:** Workflow recebe nome da cidade
2. **Validação:** Verifica se o parâmetro está presente
3. **Consulta:** Acessa API de previsão do tempo
4. **Processamento:** Formata dados meteorológicos
5. **Resposta:** Retorna previsão estruturada

## Configuração

### Credenciais Necessárias

- **API de Previsão:** Configurada para acesso meteorológico
- **Formato de Cidade:** Padrão de nomenclatura de cidades

### Dados Retornados

A API retorna informações meteorológicas, incluindo:

- **Temperatura:** Atual e prevista
- **Condições:** Clima (ensolarado, nublado, chuvoso)
- **Umidade:** Percentual de umidade relativa
- **Vento:** Velocidade e direção
- **Precipitação:** Probabilidade de chuva

## Casos de Uso

- Consulta de previsão do tempo por cidade
- Integração com agentes de IA meteorológicos
- Sistemas de alerta climático
- Aplicações de previsão do tempo
- Informações meteorológicas para usuários

## Dependências

- API de previsão do tempo configurada
- Workflow pai que execute este workflow
- Nome de cidade válido
- Acesso à internet para consultas

## Estrutura do Workflow

1. **Execute Workflow Trigger** - Recebe nome da cidade
2. **Consulta Meteorológica** - Acessa API de previsão
3. **Formatação** - Estrutura dados para resposta

## Tratamento de Erros

- **Cidade inválida:** Verificação de formato
- **API indisponível:** Tratamento de erro de conexão
- **Dados incompletos:** Fallback para informações básicas
- **Timeout:** Retry automático em caso de falha

## Monitoramento

- Verificar execuções do workflow
- Monitorar respostas da API meteorológica
- Acompanhar consultas realizadas
- Verificar logs de erro

## Validações Importantes

- **Formato da cidade:** Verificar estrutura do nome
- **Cidade existente:** Confirmar se cidade é válida
- **Dados meteorológicos:** Verificar completude das informações
- **Formato de resposta:** Garantir estrutura consistente

## Segurança

- **Validação de entrada:** Verificação de parâmetros
- **Controle de acesso:** Validação de permissões
- **Logs de auditoria:** Registro de consultas
- **Rate Limiting:** Respeitar limites da API

## Integração

- **Workflow Pai:** Fornece nome da cidade
- **API Meteorológica:** Retorna dados do tempo
- **Sistema de Resposta:** Formata dados para usuário
- **Logs:** Registra consulta para auditoria

## Performance

- **Cache:** Evitar consultas repetidas para mesma cidade
- **Timeout:** Configuração de timeout da API
- **Retry:** Tentativas automáticas em caso de falha
- **Rate Limiting:** Respeitar limites da API meteorológica

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
