# Módulos

Cada módulo agrupa skills para um tipo de trabalho. O [ROUTER.md](ROUTER.md) diz quando ativar cada módulo e é carregado em toda sessão do projeto.

```
modules/
  ROUTER.md                 roteador instalado em .harness/ROUTER.md
  <módulo>/skills/<skill>/  skill completa (SKILL.md + references/ + LICENSE, se de terceiros)
```

Para adicionar uma skill:

1. Copie a pasta da skill para `modules/<módulo>/skills/<nome>/`. Se for de terceiros, inclua a licença e a origem.
2. Coloque o nome dela na coluna "Skills" do módulo no `ROUTER.md`.
3. Faça commit e push. Os projetos recebem a skill ao rodar o harness de novo.
