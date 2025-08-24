# 📄 Extração de Dados de PDFs com IA

## Descrição

Fluxo que observa uma pasta do Google Drive em busca de novos PDFs, converte páginas em imagens, extrai texto, identifica o tipo de documento com IA (Invoice, Resume ou Shipping Label) e extrai dados estruturados, gravando-os nas planilhas Google correspondentes.

## Funcionalidades

- **Monitorar uma pasta do Google Drive:** Inicia a automação quando um novo arquivo é criado
- **Converter páginas de PDF em imagens:** Para processamento e análise visual
- **Extrair o texto do PDF:** Para uso posterior e análise textual
- **Identificar o tipo de documento:** Invoice, Resume ou Shipping Label usando IA
- **Extrair dados estruturados relevantes:** Para cada tipo de documento específico
- **Gerar blocos de imagem:** Para múltiplas páginas quando necessário
- **Gravar os dados extraídos:** Nas planilhas Google correspondentes (Invoices, Resumes, Shipping Labels)
- **Encaminhar os dados:** Para a planilha correta com base no tipo de documento

## Parâmetros de Entrada

| Parâmetro           | Tipo   | Descrição                                  |
| ------------------- | ------ | ------------------------------------------ |
| `folder_id`         | string | ID da pasta do Google Drive para monitorar |
| `file_type`         | string | Tipo de arquivo a processar (PDF)          |
| `extraction_method` | string | Método de extração (OpenAI Vision ou Text) |

## Como Funciona

1. **Trigger Google Drive:** Monitora pasta específica para novos PDFs
2. **Download do Arquivo:** Baixa o PDF do Google Drive
3. **Conversão para Imagem:** Converte páginas PDF em imagens via PDFRest API
4. **Extração de Texto:** Extrai texto do PDF para análise
5. **Identificação de Tipo:** IA identifica se é Invoice, Resume ou Shipping Label
6. **Extração Estruturada:** IA extrai dados específicos baseado no tipo
7. **Armazenamento:** Salva dados nas planilhas Google correspondentes
8. **Processamento de Múltiplas Páginas:** Gera blocos de imagem quando necessário

## Configuração

### Credenciais Necessárias

- **Google Drive API:** Para monitoramento de pasta e download de arquivos
- **OpenAI API:** Para identificação de tipo de documento e extração de dados
- **PDFRest API:** Para conversão de PDF em imagens
- **Google Sheets:** Para armazenamento dos dados extraídos

### Estrutura de Dados

```json
{
  "document_analysis": {
    "document_type": "Invoice|Resume|Shipping Label|Unknown",
    "confidence_score": 0.95,
    "analysis_details": {
      "detected_keywords": ["invoice", "total", "due"],
      "reasoning": "Document contains invoice-specific elements",
      "timestamp": "2024-12-13T16:39:16.240Z"
    }
  },
  "extracted_data": {
    "invoice_data": {
      "invoice_number": "INV-001",
      "total_due": "$1500.00",
      "due_date": "2024-12-31"
    },
    "resume_data": {
      "full_name": "John Doe",
      "skills": ["Python", "JavaScript"]
    },
    "shipping_data": {
      "tracking_number": "123456789",
      "carrier": "UPS"
    }
  }
}
```

## Casos de Uso

- **Processamento Automático de Faturas:** Extração de dados de faturas para contabilidade
- **Análise de Currículos:** Processamento de currículos para recrutamento
- **Rastreamento de Envios:** Extração de informações de etiquetas de envio
- **Automação de Documentos:** Processamento em lote de documentos PDF
- **Integração com Sistemas:** Alimentação automática de bancos de dados

## Dependências

- Google Drive API configurada
- OpenAI API para processamento de IA
- PDFRest API para conversão de PDFs
- Google Sheets para armazenamento
- Sistema de monitoramento de pastas

## Estrutura do Workflow

1. **Google Drive Trigger** - Monitora pasta para novos PDFs
2. **Get File From Google Drive** - Baixa arquivo PDF
3. **pdfrest Convert PDF to Image** - Converte PDF em imagens
4. **Create Image Code Blocks** - Gera blocos de imagem para múltiplas páginas
5. **OpenAI Document Type Identification** - Identifica tipo de documento
6. **OpenAI Invoice Extract** - Extrai dados de faturas
7. **OpenAI Resume Extract** - Extrai dados de currículos
8. **OpenAI Shipping Label Extract** - Extrai dados de etiquetas
9. **Google Sheets Operations** - Salva dados nas planilhas correspondentes

## Monitoramento

- Status de monitoramento da pasta do Google Drive
- Performance da conversão de PDF para imagem
- Taxa de sucesso na identificação de tipos de documento
- Qualidade da extração de dados estruturados
- Sucesso no armazenamento no Google Sheets

## Tratamento de Erros

- Validação de tipos de arquivo (apenas PDFs)
- Tratamento de falhas na conversão de PDF
- Fallback para extração de texto quando visão falha
- Validação de dados extraídos antes do armazenamento
- Logs de debugging para troubleshooting

## Configurações Avançadas

### Tipos de Documento Suportados

- **Invoice:** Faturas com campos estruturados (número, data, valor, etc.)
- **Resume:** Currículos com informações profissionais e educacionais
- **Shipping Label:** Etiquetas de envio com dados de rastreamento

### Métodos de Extração

- **OpenAI Vision:** Análise visual de imagens para extração
- **Text Extraction:** Processamento de texto extraído do PDF
- **Hybrid Approach:** Combinação de ambos os métodos

### Campos Extraídos por Tipo

#### Invoice

- Número da fatura, ordem, datas, valores
- Informações do remetente e destinatário
- Detalhes dos serviços e cálculos
- Dados bancários para pagamento

#### Resume

- Informações pessoais e de contato
- Experiência profissional e educação
- Habilidades e certificações
- Perfis de redes sociais

#### Shipping Label

- ID do envio e número de rastreamento
- Informações do remetente e destinatário
- Detalhes do pacote e serviço
- Custos e datas de entrega

### Integrações

- **Google Drive:** Monitoramento e download automático
- **PDFRest:** Conversão de PDF para imagens
- **OpenAI:** Análise de IA para extração
- **Google Sheets:** Armazenamento estruturado de dados

### Funcionalidades de Processamento

- **Monitoramento Contínuo:** Verificação automática de novos arquivos
- **Processamento em Lote:** Suporte a múltiplas páginas
- **Validação de Dados:** Verificação de qualidade antes do armazenamento
- **Roteamento Inteligente:** Envio para planilha correta baseado no tipo

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
