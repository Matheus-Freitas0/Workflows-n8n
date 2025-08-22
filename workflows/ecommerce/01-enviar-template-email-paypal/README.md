# 🛒 Enviar Template por E-mail Após Compra PayPal

## Descrição

Sistema automatizado que recebe notificações de pagamento do PayPal, valida pagamentos concluídos, obtém detalhes do pedido, baixa um template JSON e envia um e-mail personalizado com o template anexado ao comprador.

## Funcionalidades

- **Trigger:** Webhook PayPal para eventos de pagamento
- **Integração:** PayPal API, sistema de emails
- **Processamento:** Validação de pagamentos e download de templates
- **Saída:** Email personalizado com template anexado

## Parâmetros de Entrada

| Parâmetro    | Tipo   | Descrição                                  |
| ------------ | ------ | ------------------------------------------ |
| `webhook`    | object | Dados do webhook PayPal                    |
| `order_id`   | string | ID do pedido fornecido pelo PayPal         |
| `event_type` | string | Tipo de evento (PAYMENT.CAPTURE.COMPLETED) |

## Como Funciona

1. **Recebimento:** Webhook PayPal recebe notificação de pagamento via POST
2. **Validação:** Aguarda confirmação para garantir processamento completo da transação
3. **Filtragem:** Processa apenas eventos PAYMENT.CAPTURE.COMPLETED
4. **Consulta:** Recupera detalhes do pedido via API PayPal usando order_id
5. **Extração:** Obtém dados do cliente (nome, sobrenome, email) e produto comprado
6. **Filtragem:** Continua apenas se produto corresponder ao template específico
7. **Download:** Baixa arquivo JSON do template de URL externa
8. **Conversão:** Transforma JSON em arquivo binário para anexo
9. **Envio:** Envia email HTML personalizado com template anexado

## Configuração

### Credenciais Necessárias

- **PayPal:** API credentials para consulta de pedidos
- **Email:** Servidor SMTP configurado para envio
- **Webhook:** Endpoint configurado para receber notificações PayPal

### Estrutura de Dados

```json
{
  "webhook": {
    "event_type": "PAYMENT.CAPTURE.COMPLETED",
    "resource": {
      "order_id": "PAY-123456789"
    }
  },
  "order_details": {
    "customer": {
      "name": "João Silva",
      "email": "joao@email.com"
    },
    "product": "Template Premium"
  }
}
```

## Casos de Uso

- **Vendas Online:** Envio automático de produtos digitais após pagamento
- **Templates:** Distribuição de templates JSON para desenvolvedores
- **E-commerce:** Automação de entrega de produtos digitais
- **SaaS:** Ativação automática de licenças após pagamento

## Dependências

- Conta PayPal Business configurada
- Webhook endpoint acessível publicamente
- Servidor de email configurado
- URL do template JSON acessível
- Produto específico configurado para filtragem

## Estrutura do Workflow

1. **Webhook Trigger** - Recebimento de notificações PayPal
2. **Wait Node** - Pausa para confirmação da transação
3. **Filter** - Validação de tipo de evento
4. **PayPal API** - Consulta de detalhes do pedido
5. **Data Extraction** - Extração de dados do cliente e produto
6. **Product Filter** - Validação do produto específico
7. **HTTP Request** - Download do template JSON
8. **File Conversion** - Conversão para arquivo anexo
9. **Email Node** - Envio do email personalizado

## Monitoramento

- **Webhooks:** Status de recebimento das notificações
- **PayPal API:** Taxa de sucesso nas consultas
- **Downloads:** Sucesso no download dos templates
- **Emails:** Taxa de entrega dos emails
- **Erros:** Falhas na validação ou processamento

## Tratamento de Erros

- **Webhook Inválido:** Validação de estrutura de dados
- **API PayPal:** Retry com backoff exponencial
- **Download Falha:** Fallback para template padrão
- **Email Inválido:** Log de erro e notificação
- **Produto Não Encontrado:** Finalização do workflow

## Características Técnicas

### Eventos PayPal Suportados

- **PAYMENT.CAPTURE.COMPLETED:** Pagamento capturado com sucesso
- **Filtragem:** Apenas eventos de pagamento completos são processados

### Estrutura de Template

- **Formato:** Arquivo JSON
- **Origem:** URL externa configurável
- **Conversão:** Transformação para arquivo binário anexável

### Personalização de Email

- **Formato:** HTML personalizado
- **Campos:** Nome, sobrenome, email do cliente
- **Anexo:** Template JSON convertido
- **Assunto:** Personalizado com dados da compra

### Segurança

- **Validação:** Verificação de origem do webhook
- **Timeout:** Pausa para confirmação da transação
- **Filtragem:** Validação de produto específico
- **Logs:** Auditoria completa do processo

---

_Autor: Matheus Freitas_  
_Categoria: E-commerce_  
_Versão: 1.0_
