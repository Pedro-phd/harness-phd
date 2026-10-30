# Origem das skills do módulo back

Todas vieram do `meu_herness` v0.3.1, onde foram avaliadas na pesquisa de 2026-09-14.

| Skill | Origem | Commit | Licença |
|---|---|---|---|
| `backend-core`, `backend-jobs-webhooks`, `database-migrations`, `nestjs` | Autorais (Pedro-phd) | | Mesma do harness-phd |
| `prisma-client-api` | [prisma/skills](https://github.com/prisma/skills) | `1123817` | MIT (`LICENSE` na pasta) |
| `mysql` | Adaptada de [planetscale/database-skills](https://github.com/planetscale/database-skills) `mysql`, sem promoção de fornecedor e com defaults condicionados | `73b20b7` | MIT (`LICENSE` na pasta) |
| `postgres` | Adaptada de [supabase/agent-skills](https://github.com/supabase/agent-skills) (núcleo de performance) e [neondatabase/postgres-skills](https://github.com/neondatabase/postgres-skills) (backup/PITR, replicação, upgrades). Arquivos da Neon foram modificados. | `f421451` / `27fe45e` | MIT (`LICENSE.supabase`) e Apache-2.0 (`LICENSE.neon`) |
| `redis` | Adaptada de [redis/agent-skills](https://github.com/redis/agent-skills) `redis-core`, com operação, concorrência e falhas acrescentadas | `a84871d` | MIT (`LICENSE` na pasta) |

Mudança feita na cópia: `backend-jobs-webhooks` apontava para `backend-security`; agora aponta para o módulo `sec`.
