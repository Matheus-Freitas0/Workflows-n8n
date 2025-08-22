# 🤖 Revisor Automático de MR GitLab

## Descrição

Sistema inteligente que reage a comentários específicos em merge requests do GitLab, analisa as alterações de código com um modelo de linguagem e publica uma revisão técnica como discussão posicionada no merge request.

## Funcionalidades

- **Trigger:** Comentário específico em merge request (palavra-chave configurável)
- **Integração:** GitLab API, modelos de linguagem para análise técnica
- **Processamento:** Análise automática de diffs e geração de parecer técnico
- **Saída:** Discussão posicionada no MR com revisão técnica completa

## Parâmetros de Entrada

| Parâmetro   | Tipo   | Descrição                                        |
| ----------- | ------ | ------------------------------------------------ |
| `comment`   | object | Comentário que ativa o workflow                  |
| `mr_data`   | object | Dados do merge request do GitLab                 |
| `diff_data` | object | Diferencial de código para análise               |
| `config`    | object | Configurações do revisor (prompt, palavra-chave) |

## Como Funciona

1. **Detecção de Evento:** Monitora comentários em merge requests para palavra-chave específica
2. **Recuperação de Dados:** Consulta API do GitLab para obter diffs e metadados do MR
3. **Processamento por Arquivo:** Separa e analisa cada arquivo modificado individualmente
4. **Filtragem Inteligente:** Ignora arquivos renomeados, deletados ou diffs irrelevantes
5. **Extração de Posição:** Calcula posição precisa para discussão no diff
6. **Análise IA:** Envia contexto para modelo de linguagem gerar parecer técnico
7. **Publicação:** Cria discussão posicionada no MR com revisão completa
8. **Formatação:** Estrutura resposta em formato Markdown rigoroso

## Configuração

### Credenciais Necessárias

- **GitLab:** API token com permissões de leitura e escrita
- **IA:** Modelo de linguagem configurado para análise de código
- **Webhook:** Configuração para receber eventos de comentários

### Estrutura de Dados

```json
{
  "merge_request": {
    "id": 123,
    "project_id": 456,
    "source_branch": "feature/nova-funcionalidade",
    "target_branch": "main",
    "title": "Implementação de nova funcionalidade"
  },
  "comment": {
    "id": 789,
    "body": "!review",
    "author": "desenvolvedor@empresa.com",
    "position": {
      "file_path": "src/components/Button.js",
      "line_range": [10, 25]
    }
  },
  "diff_analysis": {
    "file_path": "src/components/Button.js",
    "changes": [
      {
        "type": "addition",
        "content": "// Nova funcionalidade adicionada",
        "line_number": 15
      }
    ],
    "technical_review": {
      "decision": "approve",
      "score": 8.5,
      "suggestions": ["Considerar adicionar validação de entrada"]
    }
  }
}
```

## Casos de Uso

- **Code Review Automatizado:** Análise técnica de alterações de código
- **Padronização:** Garantir consistência na qualidade do código
- **Treinamento:** Educar desenvolvedores sobre boas práticas
- **Auditoria:** Rastreamento de revisões técnicas automatizadas
- **Integração CI/CD:** Revisão automática em pipelines de desenvolvimento

## Dependências

- Conta GitLab com API habilitada
- Token de API com permissões adequadas
- Modelo de IA para análise de código
- Webhook configurado para eventos de comentários
- Acesso de escrita aos merge requests

## Estrutura do Workflow

1. **Webhook Trigger** - Recebe eventos de comentários do GitLab
2. **Comment Filter** - Filtra comentários com palavra-chave específica
3. **GitLab API** - Recupera dados do merge request e diffs
4. **Diff Parser** - Processa e organiza alterações por arquivo
5. **File Filter** - Remove arquivos irrelevantes da análise
6. **Position Calculator** - Calcula posição precisa para discussão
7. **AI Analysis** - Gera parecer técnico usando modelo de linguagem
8. **Response Formatter** - Formata resposta em Markdown
9. **Discussion Creator** - Cria discussão posicionada no MR

## Monitoramento

- **Revisões Realizadas:** Contagem de MRs revisados automaticamente
- **Taxa de Aprovação:** Percentual de MRs aprovados pela IA
- **Tempo de Resposta:** Velocidade da revisão automática
- **Qualidade das Sugestões:** Feedback sobre sugestões técnicas
- **Erros de API:** Status das chamadas para GitLab
- **Performance IA:** Tempo de geração de pareceres técnicos

## Tratamento de Erros

- **API GitLab Indisponível:** Retry com backoff exponencial
- **Diff Inválido:** Fallback para análise simplificada
- **Falha IA:** Notificação de erro para revisão manual
- **Permissões Insuficientes:** Log de erro e notificação
- **Timeout:** Cancelamento de operações longas
- **Validação:** Verificação de dados antes da análise

## Características Técnicas

### Sistema de Ativação

- **Palavra-chave:** Configurável (ex: "!review", "!analyze")
- **Filtros:** Apenas comentários em merge requests
- **Autorização:** Verificação de permissões do usuário
- **Rate Limiting:** Controle de frequência de revisões

### Análise de Código

- **Modelo IA:** Configurável (GPT, Claude, etc.)
- **Contexto:** Diffs completos + metadados do MR
- **Formato:** Parecer técnico estruturado
- **Decisão:** Aprovar/rejeitar com pontuação
- **Sugestões:** Recomendações específicas de melhoria

### Posicionamento de Discussão

- **Precisão:** Cálculo exato de linha/arquivo
- **Contexto:** Vinculação ao bloco de código específico
- **Histórico:** Rastreamento de revisões anteriores
- **Navegação:** Links diretos para alterações revisadas

### Integração GitLab

- **API v4:** Uso da versão mais recente da API
- **Webhooks:** Recebimento de eventos em tempo real
- **Discussões:** Criação de threads posicionados
- **Permissões:** Respeito às configurações de projeto

### Segurança e Controle

- **Validação:** Verificação de dados antes da análise
- **Logs:** Auditoria completa de todas as ações
- **Fallbacks:** Mecanismos de recuperação para falhas
- **Rate Limiting:** Respeito aos limites da API do GitLab

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
