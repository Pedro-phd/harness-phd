# Módulos

Cada módulo agrupa skills para um tipo de trabalho. O [ROUTER.md](ROUTER.md) diz quando ativar cada módulo e é carregado em toda sessão do projeto.

```
modules/
  ROUTER.md                 roteador instalado em .harness/ROUTER.md
  <módulo>/MODULE.md        quando usar cada skill do módulo, instalado em .harness/modules/<módulo>.md
  <módulo>/SOURCES.md       origem, commit e licença das skills de terceiros
  <módulo>/skills/<skill>/  skill completa, instalada em .claude/skills/ e .agents/skills/ (SKILL.md + arquivos de apoio + LICENSE, se de terceiros)
```

Para adicionar uma skill:

1. Copie a pasta da skill para `modules/<módulo>/skills/<nome>/`. Se for de terceiros, inclua a licença e a origem.
2. Coloque a skill e a condição de uso no `MODULE.md` do módulo, e a origem no `SOURCES.md`.

Skills instaladas por outras etapas (toolkit, ship-it) podem ser citadas no `MODULE.md` pelo nome, sem cópia.
3. Faça commit e push. Os projetos recebem a skill ao rodar o harness de novo.

Skills usadas só quando o usuário pede devem ter `disable-model-invocation: true` no frontmatter: continuam com slash command, mas a descrição não ocupa contexto em toda sessão.
