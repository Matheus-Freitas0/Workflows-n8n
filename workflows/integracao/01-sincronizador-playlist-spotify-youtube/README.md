# 🔄 Sincronizador Playlist Spotify → YouTube

## Descrição

Workflow automatizado que mantém uma playlist do YouTube sincronizada com uma playlist do Spotify, usando armazenamento persistente para rastrear faixas e correspondências de vídeos. O sistema detecta alterações na playlist do Spotify e propaga automaticamente adições e remoções para o YouTube.

## Funcionalidades

- **Detecção de alterações na playlist do Spotify:** Verifica se houve mudanças usando snapshot_id antes de processar
- **Sincronização unidirecional:** Propaga adições e remoções da playlist Spotify para a playlist do YouTube
- **Importação para banco persistente:** Adiciona faixas novas ao banco de dados com título, artista e duração
- **Marcação para exclusão:** Marca entradas do banco com to_delete quando removidas da playlist Spotify
- **Busca inteligente no YouTube:** Pesquisa vídeos usando título e artista e avalia os top resultados com base na duração (tolerância configurada)
- **Adição automática ao YouTube:** Adiciona o vídeo correspondente à playlist do YouTube e grava o ID do vídeo no banco
- **Marcação NOTFOUND:** Sinaliza faixas sem correspondência encontrada para tentativas futuras
- **Verificação e recuperação:** Detecta vídeos removidos do YouTube e limpa o ID no banco para re-pesquisar e permite re-tentativas periódicas
- **Exclusão condicional do banco:** Remove registros marcados para exclusão quando apropriado
- **Agendamentos múltiplos:** Executa verificações periódicas (hora a hora, diariamente e mensalmente) e inclui um processo de espera para checagens repetidas
- **Notificações opcionais:** Envia notificações sobre correspondências falhadas ou adições bem-sucedidas via webhook

## Parâmetros de Entrada

| Parâmetro             | Tipo   | Descrição                                     |
| --------------------- | ------ | --------------------------------------------- |
| `spotify_playlist_id` | string | ID da playlist do Spotify                     |
| `youtube_playlist_id` | string | ID da playlist do YouTube                     |
| `supabase_table_name` | string | Nome da tabela no Supabase para armazenamento |

## Como Funciona

### Workflow 1: Processo Principal de Sincronização

1. **Detecção de Mudanças:** Monitora playlist do Spotify usando snapshot_id
2. **Comparação de Dados:** Compara estado atual com banco de dados
3. **Processamento de Novas Faixas:** Adiciona novas faixas ao banco e busca correspondentes no YouTube
4. **Matching Inteligente:** Avalia vídeos do YouTube baseado em título, artista e duração
5. **Sincronização:** Adiciona vídeos correspondentes à playlist do YouTube

### Workflow 2: Manutenção do YouTube

1. **Verificação de Vídeos Removidos:** Detecta vídeos removidos da playlist do YouTube
2. **Limpeza de IDs:** Reseta IDs de vídeos removidos para re-pesquisa
3. **Remoção de Entradas:** Remove registros marcados para exclusão

### Workflow 3: Processo de Recuperação

1. **Reset de Flags NOTFOUND:** Limpa marcações de faixas não encontradas
2. **Re-tentativas:** Permite nova tentativa de matching para faixas previamente não encontradas

## Configuração

### Credenciais Necessárias

- **Spotify API:** Credenciais configuradas no n8n
- **YouTube Data API v3:** API key configurada
- **Supabase:** Credenciais de conexão com banco de dados
- **Discord (opcional):** Webhook para notificações

### Estrutura de Dados do Banco

```sql
CREATE TABLE IF NOT EXISTS musics (
    id TEXT PRIMARY KEY,
    title TEXT NOT NULL,
    artist TEXT NOT NULL,
    duration INT8 NOT NULL,
    youtube_video_id TEXT,
    to_delete BOOLEAN DEFAULT FALSE
);
```

### Variáveis de Configuração

```json
{
  "spotify_playlist_id": "4fjIxvQt8aQrQZs4XqvsmR",
  "youtube_playlist_id": "PLjmwnzu1gWRsnW6icKeUyvbaK9-Cs8oom",
  "supabase_table_name": "musics"
}
```

## Casos de Uso

- Sincronização automática de playlists musicais entre plataformas
- Manutenção de biblioteca musical consistente
- Backup e sincronização de preferências musicais
- Gestão automatizada de playlists para diferentes serviços

## Dependências

- Projeto Supabase configurado com tabela `musics`
- Playlist do YouTube vazia (recomendado para evitar duplicatas)
- Credenciais válidas para Spotify, YouTube e Supabase APIs
- Workflow ativado no n8n

## Estrutura do Workflow

### Triggers de Agendamento

1. **Every hour** - Verificação principal de mudanças
2. **Every day at noon** - Verificação forçada diária
3. **Every day at midnight** - Manutenção do YouTube
4. **Every month** - Processo de recuperação

### Nós Principais

1. **Spotify API** - Obtenção de dados da playlist
2. **Supabase** - Operações de banco de dados
3. **YouTube API** - Busca e gestão de vídeos
4. **Compare Datasets** - Análise de diferenças
5. **Discord** - Notificações (opcional)

## Monitoramento

- **Logs de Execução:** Acompanhar execuções via n8n
- **Métricas de Sincronização:** Contagem de faixas processadas
- **Notificações:** Alertas sobre falhas de matching
- **Status do Banco:** Verificar integridade dos dados

## Tratamento de Erros

- **Tolerância de Duração:** ±10 segundos para matching de vídeos
- **Marcação NOTFOUND:** Para faixas sem correspondência
- **Re-tentativas Automáticas:** Reset mensal de flags NOTFOUND
- **Continuidade:** Workflow continua mesmo com erros individuais

## Implementação Técnica

- **Tolerância de Duração:** Configurável via código (atualmente ±20 segundos)
- **Limite de Resultados:** Top 5 vídeos do YouTube analisados
- **Processamento em Lotes:** Uso de SplitInBatches para eficiência
- **Armazenamento Persistente:** Banco Supabase para rastreamento

---

_Autor: Matheus Freitas_  
_Categoria: Integração_  
_Versão: 1.0_
