# 🚀 Geração Automática de Landing Pages

## Descrição

Este fluxo automatiza a geração de conteúdo para landing pages focadas em automação de staffing. Ele coleta dados de entrada, gera conteúdo seção por seção usando IA, e consolida tudo em uma configuração de página pronta para uso.

## Funcionalidades

- **Trigger manual:** Inicia a automação ao clicar em "Test workflow"
- **Preparação de dados:** Carrega "Background Information" incluindo domínio, público-alvo, título do site, tipo de empresa, caso de uso e prompts de apresentação
- **Expansão de itens:** Divide a entrada em itens individuais para processamento
- **Processamento iterativo:** Itera através dos itens em lotes e aplica geração de conteúdo por item
- **Geração de conteúdo por IA:** Usa modelo de IA para criar conteúdo para várias seções incluindo hero, subtítulo, CTA, pain points e outras seções da landing page
- **Parser de saída estruturado:** Converte saídas de IA em estrutura previsível para uso
- **Criação de configuração RAW:** Monta a configuração da landing page com elementos como header, descrição, imagens, vídeo e depoimentos
- **Finalização da configuração:** Ajusta formatos (remove quebras) e produz a saída final
- **Agrupamento de conteúdo:** Agrupa conteúdo para formar o conteúdo final da página

## Parâmetros de Entrada

| Parâmetro                 | Tipo   | Descrição                                               |
| ------------------------- | ------ | ------------------------------------------------------- |
| `domain`                  | string | Domínio da landing page (ex: automationforstaffing.com) |
| `intended_audience`       | string | Público-alvo da empresa                                 |
| `site_title`              | string | Título do site                                          |
| `target_company_type`     | string | Tipo de empresa (ex: Staffing Agency)                   |
| `use_case_details`        | string | Detalhes do caso de uso específico                      |
| `company_overview_prompt` | string | Visão geral da empresa e princípios                     |

## Como Funciona

1. **Trigger Manual:** Inicia o workflow para geração de landing page
2. **Carregamento de Dados:** Define informações de background da empresa e público-alvo
3. **Divisão de Componentes:** Separa cada seção em itens individuais para processamento
4. **Geração de Conteúdo:** IA gera conteúdo específico para cada seção da landing page
5. **Estruturação:** Parser estruturado organiza o conteúdo gerado
6. **Montagem da Configuração:** Cria configuração completa com todas as seções
7. **Finalização:** Remove formatação desnecessária e produz resultado final

## Configuração

### Credenciais Necessárias

- **Anthropic API:** Para geração de conteúdo com IA
- **Configuração de domínio:** Para personalização da landing page

### Estrutura de Dados

```json
{
  "background_info": {
    "domain": "automationforstaffing.com",
    "intended_audience": "Staffing owners and C-suite decision makers",
    "site_title": "Automation For Staffing",
    "target_company_type": "Staffing Agency",
    "use_case_details": "Timesheet collection, invoice generation, payroll automation",
    "company_overview_prompt": "Workflowsy consulting service description"
  },
  "landing_page_sections": {
    "hero": "Título principal e subtítulo",
    "cta": "Call to action principal",
    "pain_points": "Pontos de dor da indústria",
    "automation_speaks": "Demonstração da automação",
    "how_it_works": "Processo de implementação",
    "faq": "Perguntas frequentes",
    "second_cta": "Call to action secundário"
  }
}
```

## Casos de Uso

- **Criação Rápida de Landing Pages:** Geração automática para diferentes domínios
- **Marketing de Nicho:** Páginas específicas para diferentes indústrias
- **Testes A/B:** Geração de múltiplas versões para otimização
- **Expansão de Negócio:** Criação de páginas para novos mercados
- **Consultoria de Automação:** Landing pages para serviços de automação

## Dependências

- Anthropic API configurada
- Informações de background da empresa
- Casos de uso específicos definidos
- Estrutura de seções da landing page

## Estrutura do Workflow

1. **When clicking 'Test workflow'** - Trigger manual para iniciar
2. **Background Information** - Define dados de entrada da empresa
3. **Split out into items** - Divide componentes em itens individuais
4. **Component** - Estrutura cada componente para processamento
5. **Loop Over Items** - Processa itens em lotes
6. **Text Content Generator** - IA gera conteúdo para cada seção
7. **Structured Output Parser** - Organiza saída da IA
8. **Configuration Creator RAW** - Monta configuração da landing page
9. **Config Output (Finalized)** - Finaliza e formata a saída

## Monitoramento

- Status de geração de conteúdo por IA
- Performance do processamento iterativo
- Qualidade do conteúdo gerado
- Tempo de execução do workflow
- Validação da estrutura de saída

## Tratamento de Erros

- Validação de dados de entrada
- Tratamento de falhas na geração de IA
- Verificação de estrutura de saída
- Fallback para conteúdo padrão
- Logs de debugging para troubleshooting

## Configurações Avançadas

### Seções da Landing Page

- **Hero Section:** Título principal, subtítulo e CTA
- **Pain Points:** Desafios específicos da indústria
- **Automation Benefits:** Demonstração de valor da automação
- **How It Works:** Processo de implementação
- **FAQ:** Perguntas frequentes e respostas
- **Social Proof:** Depoimentos e validação social
- **Second CTA:** Call to action final

### Modelo de IA

- **Anthropic Claude:** Para geração de conteúdo de alta qualidade
- **Prompts Estruturados:** Instruções específicas para cada seção
- **Parser Estruturado:** Validação e organização da saída

### Personalização

- **Domínio Específico:** Configuração para diferentes websites
- **Público-Alvo:** Conteúdo adaptado ao segmento
- **Caso de Uso:** Foco em automações específicas
- **Tipo de Empresa:** Linguagem e exemplos relevantes

### Formato de Saída

- **Configuração RAW:** Estrutura JSON completa
- **Formatação HTML:** Tags para formatação web
- **Imagens Placeholder:** URLs para elementos visuais
- **Estrutura Responsiva:** Layout adaptável

---

_Autor: Matheus Freitas_  
_Categoria: Marketing_  
_Versão: 1.0_
