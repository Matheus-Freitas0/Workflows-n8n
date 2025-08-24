# 🔍 Buscador de Palavras-Chave

## Descrição

Fluxo que detecta mensagens, busca palavras-chave, verifica correspondência e envia notificações via API externa quando encontra uma palavra-chave. O sistema monitora mensagens recebidas, consulta uma base de dados de palavras-chave e notifica automaticamente quando há correspondências.

## Funcionalidades

- **Detecção de Texto e Extração de Palavras-Chave:** Identifica se a mensagem é texto e extrai palavras-chave relevantes
- **Busca de Palavras-Chave no Texto:** Compara a mensagem com uma lista de palavras-chave para encontrar correspondências
- **Armazenamento do Resultado:** Armazena a mensagem recebida e a palavra-chave encontrada para uso posterior
- **Integração com Baserow:** Consulta a lista de palavras-chave da base de dados Baserow
- **Envio de Notificação via API Externa:** Envia a mensagem com a palavra-chave encontrada para o destinatário através de uma API externa
- **Validação de Mensagens:** Verifica se é mensagem de texto e não é mensagem própria
- **Diferenciação de Origem:** Identifica se a mensagem veio de grupo ou conversa individual
- **Notificações Inteligentes:** Envia alertas formatados com detalhes da correspondência encontrada

## Parâmetros de Entrada

| Parâmetro  | Tipo   | Descrição                          |
| ---------- | ------ | ---------------------------------- |
| `message`  | string | Mensagem de texto recebida         |
| `from`     | string | ID do remetente da mensagem        |
| `group`    | string | Indica se veio de grupo (opcional) |
| `pushName` | string | Nome do remetente                  |

## Como Funciona

1. **Execute Workflow Trigger:** Recebe mensagem via trigger externo
2. **Validação de Mensagem:** Verifica se é mensagem de texto válida
3. **Busca de Palavras-Chave:** Consulta base de dados Baserow para obter lista de palavras
4. **Preparação de Dados:** Organiza mensagem e palavras-chave para comparação
5. **Comparação Inteligente:** Executa código JavaScript para encontrar correspondências
6. **Verificação de Correspondência:** Determina se alguma palavra-chave foi encontrada
7. **Identificação de Origem:** Verifica se a mensagem veio de grupo ou conversa individual
8. **Envio de Notificação:** Envia alerta via API Evolution com detalhes da correspondência
9. **Finalização:** Conclui o processo de monitoramento

## Configuração

### Credenciais Necessárias

- **Baserow API:** Para consulta da base de dados de palavras-chave
- **Evolution API:** Para envio de notificações via WhatsApp
- **Execute Workflow Trigger:** Para recebimento de mensagens

### Estrutura de Dados

```json
{
  "workflow_trigger": {
    "body": {
      "data": {
        "key": {
          "fromMe": false,
          "participant": "5511999999999@s.whatsapp.net",
          "remoteJid": "5511999999999@s.whatsapp.net",
          "id": "message_id"
        },
        "message": {
          "conversation": "Mensagem de texto recebida"
        },
        "pushName": "Nome do Remetente"
      }
    }
  },
  "palavras_chave": [
    {
      "palavras": "palavra1",
      "id": 1
    },
    {
      "palavras": "palavra2",
      "id": 2
    }
  ],
  "resultado_comparacao": {
    "mensagem": "Mensagem recebida",
    "YES": true,
    "palavraChave": "palavra_encontrada"
  }
}
```

## Casos de Uso

- **Monitoramento de Conversas:** Detecção automática de palavras-chave em mensagens
- **Alertas de Segurança:** Notificação quando palavras sensíveis são mencionadas
- **Moderação de Conteúdo:** Identificação de conteúdo específico em grupos
- **Análise de Sentimento:** Monitoramento de termos específicos para análise
- **Compliance e Auditoria:** Rastreamento de mensagens com palavras regulamentadas
- **Suporte ao Cliente:** Detecção de palavras-chave para roteamento automático

## Dependências

- Baserow API configurada com base de dados de palavras-chave
- Evolution API para envio de notificações WhatsApp
- Execute Workflow Trigger para recebimento de mensagens
- Sistema de validação de mensagens
- Código JavaScript para comparação de palavras-chave

## Estrutura do Workflow

1. **Execute Workflow Trigger** - Recebe mensagens externas
2. **É Mensagem de Texto?** - Valida tipo e origem da mensagem
3. **Buscas Palavras** - Consulta base de dados Baserow
4. **Mensagem** - Extrai texto da mensagem recebida
5. **Palavra Chave** - Prepara lista de palavras-chave
6. **Merclar** - Combina dados para processamento
7. **Agregar** - Agrega informações para comparação
8. **Comparar** - Executa lógica de comparação JavaScript
9. **Tem a Palavra?** - Verifica se encontrou correspondência
10. **Veio de Grupo?** - Identifica origem da mensagem
11. **Evolution/Evolution1** - Envia notificações via API
12. **Fim/Fim1** - Finaliza o processo

## Monitoramento

- Status de recebimento de mensagens via trigger
- Performance da consulta à base de dados Baserow
- Taxa de sucesso na detecção de palavras-chave
- Qualidade das notificações enviadas
- Tempo de resposta do sistema
- Logs de correspondências encontradas

## Tratamento de Erros

- Validação de mensagens recebidas
- Tratamento de falhas na consulta ao Baserow
- Fallback para mensagens sem correspondência
- Validação de credenciais de APIs
- Logs de debugging para troubleshooting
- Tratamento de falhas no envio de notificações

## Configurações Avançadas

### Sistema de Detecção

- **Validação de Mensagens:** Verificação de tipo e origem
- **Filtros Inteligentes:** Exclusão de mensagens próprias
- **Diferenciação de Origem:** Identificação de grupos vs. individuais
- **Processamento Assíncrono:** Execução em background

### Base de Dados de Palavras-Chave

- **Integração Baserow:** Consulta automática de palavras-chave
- **Atualização Dinâmica:** Lista sempre atualizada
- **Estrutura Flexível:** Suporte a diferentes tipos de palavras
- **Cache Inteligente:** Otimização de consultas frequentes

### Sistema de Notificações

- **API Evolution:** Envio via WhatsApp Business
- **Formatação Rica:** Mensagens com emojis e formatação
- **Detalhes Completos:** Informações sobre correspondência encontrada
- **Diferenciação de Origem:** Notificações específicas para grupos e individuais

### Lógica de Comparação

- **Código JavaScript:** Comparação inteligente e flexível
- **Case Insensitive:** Busca independente de maiúsculas/minúsculas
- **Múltiplas Palavras:** Suporte a várias palavras-chave
- **Resultado Estruturado:** Retorno organizado para processamento

### Funcionalidades de Monitoramento

- **Trigger Externo:** Recebimento de mensagens via webhook
- **Validação em Tempo Real:** Verificação imediata de conteúdo
- **Notificação Automática:** Alerta instantâneo de correspondências
- **Rastreamento Completo:** Log de todas as atividades

### Integrações

- **Execute Workflow Trigger:** Recebimento de mensagens
- **Baserow:** Base de dados de palavras-chave
- **Evolution API:** Envio de notificações WhatsApp
- **Sistema de Validação:** Filtros e verificações automáticas

---

_Autor: Matheus Freitas_  
_Categoria: Monitoramento_  
_Versão: 1.0_
