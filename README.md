# harness-phd

Meu harness de desenvolvimento com agentes de IA. Um comando prepara o projeto inteiro: base de engenharia, pipeline de entrega e módulos de skills. Funciona no Claude Code, no Codex ou em qualquer agente com acesso a arquivos e terminal.

## Como usar

Abra o agente na pasta do projeto e cole:

```text
Leia https://raw.githubusercontent.com/Pedro-phd/harness-phd/main/HARNESS.md e execute o harness nesta pasta.
```

- **Projeto novo:** abra numa pasta vazia. Se quiser, acrescente uma segunda linha com a descrição; se não acrescentar, o harness pergunta antes de começar.

  ```text
  Projeto: [nome, problema, público, fluxos principais e restrições].
  ```

- **Projeto existente:** abra na raiz do projeto. O harness detecta o que já existe e adapta a configuração, sem trocar a stack.

### Rodar de novo

Cole o mesmo comando. O progresso fica em `.harness/state.md`:

- se a sessão caiu ou o contexto acabou no meio, o harness continua de onde parou;
- etapas concluídas não se repetem, exceto a etapa 3, que roda sempre e traz as skills e o roteador atualizados;
- etapas novas adicionadas a este repositório são executadas.

## Requisitos

| Ferramenta | Para quê |
|---|---|
| Claude Code ou Codex | Executar o harness. Outros agentes funcionam se lerem arquivos e rodarem comandos. |
| `git` | Clonar o ship-it e os módulos; registrar versões. |
| Node.js com `npx` | Setup do toolkit e instalação de skills de terceiros. |
| `gh` autenticado (opcional) | Fluxo de PR e GitHub Issues do ship-it. Sem ele, o ship-it usa commits locais e tarefas em Markdown. |

Alguns recursos existem só no Claude Code: os slash commands do ship-it (`/ship-it:<skill>`) e o plugin `insecure-defaults`. No Codex, o harness avisa e segue sem eles.

## Etapas

| # | Etapa | O que faz | Arquivo |
|---|---|---|---|
| 1 | Base com o [Vibe Coding Toolkit](https://github.com/soumatheusgomes/vibe-coding-toolkit) | Detecta se o projeto é novo ou existente. Projeto novo: cria a base Next.js com TypeScript, Drizzle/PostgreSQL, Vitest, ESLint e documentação. Projeto existente: diagnostica e adota o toolkit preservando a stack. Nos dois casos instala skills, integrações e verificações. | [steps/01-toolkit.md](steps/01-toolkit.md) |
| 2 | Pipeline com o [ship-it](https://github.com/samsantosb/ship-it) | Instala o ship-it na máquina, roda o `/groundwork` (tracker, repo, reviewer, idioma) e o `/make-guidelines` (gera o `GUIDELINES.md`). | [steps/02-ship-it.md](steps/02-ship-it.md) |
| 3 | Módulos de skills | Instala as skills dos módulos, os plugins do Claude Code e o roteador que diz quando usar cada skill. Mede o contexto carregado em toda sessão. Roda sempre. | [steps/03-modules.md](steps/03-modules.md) |

### Quando o harness pergunta

Ele segue sozinho, exceto nestes pontos:

- **Etapa 1:** a descrição do projeto novo, se você não a passou no comando. Em projeto existente, o toolkit começa com um brainstorming e apresenta o plano.
- **Etapa 2:** uma rodada de perguntas do `/groundwork` (tracker, tamanho máximo de PR, idioma) e a entrevista do `/make-guidelines`.
- **Etapa 3:** só se já existir no projeto uma skill com o mesmo nome de uma skill do harness, vinda de outro lugar.
- Qualquer etapa pode parar e perguntar se algo for ambíguo ou arriscado.

A etapa 1 é a mais longa. Se o contexto da sessão estiver perto do limite, o harness termina a etapa atual, salva o progresso e pede para você colar o comando numa sessão nova.

## Módulos

O roteador (`.harness/ROUTER.md`) é carregado em toda sessão e decide quais módulos a tarefa ativa. Cada módulo tem um arquivo com as condições de uso de cada skill, lido só quando o módulo é ativado.

| Módulo | Ativa quando | Skills |
|---|---|---|
| `quality` | A tarefa cria, altera ou revisa código | `property-based-testing`, `tdd` (só quando pedido) |
| `sec` | A tarefa mexe em código executável, configuração, dependências, auth ou dados | `secure-by-default`, `backend-security`, `security-audit` (só quando pedido), `insecure-defaults` (plugin, só quando pedido), `differential-review` (do toolkit) |
| `front` | Interface: páginas, componentes, layout, animação | 14 skills de design e motion de Emil Kowalski, mais a base do toolkit (`vercel-react-best-practices`, `web-design-guidelines` e outras) |
| `back` | Endpoints, serviços, regras, persistência, jobs | `backend-core`, `backend-jobs-webhooks`, `database-migrations`, `nestjs`, `prisma-client-api`, `postgres`, `mysql`, `redis` |
| `debug` | Bug, erro, regressão ou lentidão | `diagnosing-bugs` |

O roteador também manda ler o `GUIDELINES.md` antes de escrever ou revisar código, dentro ou fora do fluxo do ship-it.

Detalhes e como adicionar skills: [modules/README.md](modules/README.md).

## O que fica no projeto

| Caminho | Origem |
|---|---|
| `.harness/state.md` | Progresso das etapas |
| `.harness/ROUTER.md`, `.harness/modules/*.md` | Roteador e condições de cada módulo |
| `.harness/skills.lock` | Skills instaladas pelo harness, para atualizar e remover com segurança |
| `.claude/skills/`, `.agents/skills/` | Skills dos módulos e do toolkit (Claude Code e outros agentes) |
| `docs/agents/*.md`, `GUIDELINES.md` | Configuração e regras do ship-it |
| `README.md`, `PRODUCT.md`, `AGENTS.md`, `CLAUDE.md`, `docs/*.md` | Documentação e instruções geradas pelo toolkit |

Versione tudo isso junto com o código.

## Uso no dia a dia

Depois do setup, peça normalmente: o roteador escolhe as skills. Para entregar features com o pipeline do ship-it:

```
/create-product <ideia>  →  /create-tasks <doc>  →  /do-task <card>  →  /watch-pr  →  /chaos-engineering
```

No Claude Code, os comandos ficam como `/ship-it:<skill>`. Em outros agentes, peça: "Siga ~/.ship-it/AGENTS.md e rode skills/<skill>/SKILL.md com <argumento>".

## Créditos

- Etapa 1: [Vibe Coding Toolkit](https://github.com/soumatheusgomes/vibe-coding-toolkit), criado por [Matheus Gomes](https://github.com/soumatheusgomes), licença MIT.
- Etapa 2: [ship-it](https://github.com/samsantosb/ship-it), criado por [Samuel Santos](https://github.com/samsantosb), licença MIT.
- Módulo front: skills de design e motion de [Emil Kowalski](https://github.com/emilkowalski/skills), licença MIT.
- Módulo back: adaptadores derivados de [Prisma](https://github.com/prisma/skills), [PlanetScale](https://github.com/planetscale/database-skills), [Supabase](https://github.com/supabase/agent-skills), [Neon](https://github.com/neondatabase/postgres-skills) (Apache-2.0) e [Redis](https://github.com/redis/agent-skills), licença MIT salvo indicação.
- Módulo sec: [security-audit](https://github.com/cloudflare/security-audit-skill) da Cloudflare (MIT) e o plugin `insecure-defaults` da [Trail of Bits](https://github.com/trailofbits/skills) (CC-BY-SA-4.0, instalado pelo marketplace, não copiado).
- Módulos quality e debug: `tdd` e `diagnosing-bugs` de [Matt Pocock](https://github.com/mattpocock/skills) (MIT) e `property-based-testing` da [Trail of Bits](https://github.com/trailofbits/skills) (CC-BY-SA-4.0).

O toolkit e o ship-it não são copiados: o harness lê os arquivos direto dos repositórios originais em cada execução. As skills dos módulos são copiadas com a licença original; a origem e o commit de cada uma ficam em `modules/<módulo>/SOURCES.md`. Todo o crédito pelo conteúdo é dos autores.
