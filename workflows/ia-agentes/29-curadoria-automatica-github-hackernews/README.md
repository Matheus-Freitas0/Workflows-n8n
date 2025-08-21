# 🤖 Curadoria Automática de Projetos GitHub do Hacker News

## Descrição

Workflow automatizado que descobre links GitHub em posts do Hacker News, extrai informações dos repositórios e utiliza inteligência artificial para gerar posts otimizados para Twitter e LinkedIn. O sistema inclui verificação de duplicatas, armazenamento de registros e notificações antes da publicação.

## Funcionalidades

- **Rastreamento Agendado:** Verifica periodicamente a página inicial do Hacker News em busca de novos posts
- **Extração de Metadados:** Identifica e filtra links GitHub, coletando metadados como título, autor, pontuação e comentários
- **Verificação de Duplicatas:** Consulta banco de dados para evitar republicação do mesmo conteúdo
- **Visita ao Repositório:** Acessa a página GitHub para obter mais contexto e conteúdo sobre o projeto
- **Conversão de Conteúdo:** Transforma HTML da página GitHub em formato Markdown para análise mais fácil
- **Geração de Conteúdo com IA:** Utiliza modelo de linguagem para criar textos formatados para Twitter e LinkedIn, seguindo regras específicas sobre Call-to-Action (CTA), comprimento e tom
- **Validação de Conteúdo:** Verifica se os textos gerados atendem ao formato esperado antes de prosseguir
- **Registro no Banco:** Cria ou atualiza registros no banco de dados para rastrear o que foi preparado e publicado
- **Notificação e Aguardo:** Envia mensagem preparada para o responsável via Telegram e aguarda intervalo especificado antes da publicação final
- **Publicação nas Redes:** Publica o post no X (Twitter) e LinkedIn, atualizando o status do sistema após submissão bem-sucedida
- **Tratamento de Erros:** Filtra itens com erros para evitar publicações incorretas ou incompletas

## Parâmetros de Entrada

| Parâmetro           | Tipo   | Descrição                                    |
| ------------------- | ------ | -------------------------------------------- |
| `hackernews_url`   | string | URL da página inicial do Hacker News         |
| `ai_model`         | string | Modelo de IA para geração de conteúdo        |
| `telegram_chat_id` | string | ID do chat Telegram para notificações        |
| `wait_interval`    | number | Intervalo de espera antes da publicação (minutos) |

## Como Funciona

### 1. **Rastreamento e Descoberta**
- Acessa periodicamente a página inicial do Hacker News
- Identifica posts que contêm links para repositórios GitHub
- Extrai metadados relevantes (título, autor, pontuação, comentários)

### 2. **Processamento e Análise**
- Verifica banco de dados para evitar duplicatas
- Acessa páginas GitHub para obter contexto adicional
- Converte conteúdo HTML em Markdown para processamento

### 3. **Geração de Conteúdo com IA**
- Utiliza modelo de linguagem para criar posts otimizados
- Gera versões específicas para Twitter e LinkedIn
- Aplica regras de CTA, comprimento e tom apropriados

### 4. **Validação e Aprovação**
- Valida formato e qualidade do conteúdo gerado
- Envia notificação para aprovação via Telegram
- Aguarda intervalo configurado antes da publicação

### 5. **Publicação e Monitoramento**
- Publica conteúdo nas redes sociais configuradas
- Atualiza status no banco de dados
- Registra sucessos e falhas para análise

## Configuração

### Credenciais Necessárias

- **Hacker News:** Acesso à API pública do Hacker News
- **GitHub:** Acesso a repositórios públicos (sem credenciais especiais)
- **IA:** Chave de API para modelo de linguagem (OpenAI, Claude, etc.)
- **Telegram:** Bot token e chat ID para notificações
- **Twitter (X):** API keys e tokens de acesso
- **LinkedIn:** Credenciais de API do LinkedIn
- **Banco de Dados:** Conexão para armazenamento de registros

### Estrutura do Banco de Dados

```sql
CREATE TABLE IF NOT EXISTS github_projects (
    id SERIAL PRIMARY KEY,
    hackernews_id VARCHAR(50) UNIQUE,
    github_url TEXT,
    title TEXT,
    author VARCHAR(100),
    score INTEGER,
    comments_count INTEGER,
    content_markdown TEXT,
    twitter_post TEXT,
    linkedin_post TEXT,
    status VARCHAR(20) DEFAULT 'pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    published_at TIMESTAMP,
    error_message TEXT
);
```

### Configurações de IA

```json
{
  "model": "gpt-4",
  "max_tokens": 500,
  "temperature": 0.7,
  "prompt_template": "Crie um post para {platform} sobre o projeto GitHub: {title}. Inclua CTA apropriado e mantenha o tom profissional."
}
```

## Casos de Uso

- **Descoberta de Projetos:** Identificação automática de projetos interessantes no GitHub
- **Marketing de Conteúdo:** Geração automática de posts para redes sociais
- **Curadoria Técnica:** Seleção e compartilhamento de projetos relevantes
- **Engajamento Social:** Manutenção ativa de presença nas redes sociais
- **Análise de Tendências:** Rastreamento de projetos populares no Hacker News

## Dependências

- Acesso à API pública do Hacker News
- Modelo de IA configurado e funcional
- Bot do Telegram configurado
- Contas ativas no Twitter (X) e LinkedIn
- Banco de dados para armazenamento de registros
- Workflow ativado no n8n

## Estrutura do Workflow

### Nós Principais
1. **Schedule Trigger** - Execução periódica
2. **HTTP Request** - Acesso ao Hacker News
3. **HTML Extract** - Extração de links GitHub
4. **GitHub API** - Obtenção de dados dos repositórios
5. **AI Model** - Geração de conteúdo
6. **Telegram** - Notificações de aprovação
7. **Wait** - Intervalo antes da publicação
8. **Social Media APIs** - Publicação nas redes
9. **Database** - Armazenamento de registros

### Fluxo de Execução
```
Schedule → Hacker News → GitHub Links → AI Generation → Approval → Wait → Publish → Database Update
```

## Monitoramento

- **Logs de Execução:** Acompanhar descobertas via n8n
- **Métricas de Descoberta:** Contagem de projetos encontrados
- **Taxa de Aprovação:** Percentual de posts aprovados
- **Status de Publicação:** Sucesso/falha nas redes sociais
- **Histórico de Projetos:** Rastrear projetos processados

## Tratamento de Erros

- **Falhas de API:** Retry automático com backoff exponencial
- **Conteúdo Inválido:** Filtragem de posts com erros
- **Rate Limiting:** Respeito aos limites das APIs
- **Falhas de Publicação:** Registro de erros para análise
- **Timeout de Resposta:** Tratamento de respostas lentas

## Implementação Técnica

- **Processamento Assíncrono:** Execução paralela de tarefas
- **Cache de Dados:** Evita reprocessamento desnecessário
- **Validação de Conteúdo:** Verificação de qualidade antes da publicação
- **Logs Estruturados:** Rastreamento detalhado de execuções
- **Tratamento de HTML:** Conversão robusta para Markdown

## Personalização

- **Filtros de Conteúdo:** Regras para seleção de projetos
- **Templates de IA:** Prompts personalizáveis por plataforma
- **Intervalos de Execução:** Frequência configurável de rastreamento
- **Critérios de Pontuação:** Filtros baseados em popularidade
- **Palavras-chave:** Foco em tecnologias ou domínios específicos

## Segurança e Compliance

- **Rate Limiting:** Respeito aos limites das APIs
- **Validação de Conteúdo:** Prevenção de conteúdo inadequado
- **Logs de Auditoria:** Rastreamento de todas as ações
- **Aprovação Humana:** Controle antes da publicação
- **Conformidade GDPR:** Tratamento adequado de dados

---

_Autor: Matheus Freitas_  
_Categoria: IA e Agentes_  
_Versão: 1.0_
