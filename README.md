# harness-phd

Meu harness de desenvolvimento com agentes de IA. Um comando inicia toda a configuração, no Claude Code, no Codex ou em qualquer agente com acesso a arquivos e terminal.

## Como usar

Abra o agente na pasta do projeto (vazia para um projeto novo, ou a raiz de um projeto existente) e cole:

```text
Leia https://raw.githubusercontent.com/Pedro-phd/harness-phd/main/HARNESS.md e execute o harness nesta pasta.
```

Para um projeto novo, você pode adicionar uma segunda linha com a descrição:

```text
Projeto: [nome, problema, público, fluxos principais e restrições].
```

## Etapas

| # | Etapa | Arquivo |
|---|---|---|
| 1 | Configuração base com o [Vibe Coding Toolkit](https://github.com/soumatheusgomes/vibe-coding-toolkit) | [steps/01-toolkit.md](steps/01-toolkit.md) |
| 2 | Pipeline de entrega com o [ship-it](https://github.com/samsantosb/ship-it): groundwork, guidelines e workflow | [steps/02-ship-it.md](steps/02-ship-it.md) |
| 3 | Módulos de skills e o roteador que diz quando usar cada um | [steps/03-modules.md](steps/03-modules.md) |

As etapas rodam em sequência. O progresso fica em `.harness/state.md` no projeto: se a sessão cair, cole o mesmo comando e o harness continua de onde parou.

Novas etapas entram em `steps/` e na lista do [HARNESS.md](HARNESS.md).

## Créditos

- Etapa 1: [Vibe Coding Toolkit](https://github.com/soumatheusgomes/vibe-coding-toolkit), criado por [Matheus Gomes](https://github.com/soumatheusgomes), licença MIT.
- Módulo front: skills de design e motion de [Emil Kowalski](https://github.com/emilkowalski/skills), licença MIT. A origem de cada skill fica em `modules/<módulo>/SOURCES.md`.
- Módulo back: adaptadores derivados de [Prisma](https://github.com/prisma/skills), [PlanetScale](https://github.com/planetscale/database-skills), [Supabase](https://github.com/supabase/agent-skills), [Neon](https://github.com/neondatabase/postgres-skills) (Apache-2.0) e [Redis](https://github.com/redis/agent-skills), licença MIT salvo indicação.
- Módulo sec: [security-audit](https://github.com/cloudflare/security-audit-skill) da Cloudflare, licença MIT.
- Módulo sec: plugin `insecure-defaults` da [Trail of Bits](https://github.com/trailofbits/skills), licença CC-BY-SA-4.0, instalado pelo marketplace (não copiado).
- Etapa 2: [ship-it](https://github.com/samsantosb/ship-it), criado por [Samuel Santos](https://github.com/samsantosb), licença MIT.

O toolkit e o ship-it não são copiados: o harness lê os arquivos direto dos repositórios originais em cada execução. As skills dos módulos são copiadas com a licença original. Todo o crédito pelo conteúdo é dos autores.
