# Roteador de skills (harness-phd)

Este arquivo é carregado em toda sessão. Ele define quais skills usar em cada tipo de tarefa, dentro ou fora de qualquer fluxo (ship-it ou conversa solta).

As skills ficam em `.claude/skills/<nome>/SKILL.md` (Claude Code) e `.agents/skills/<nome>/SKILL.md` (Codex e outros agentes). O conteúdo é o mesmo nos dois lugares.

## Como usar

1. Antes de começar uma tarefa, identifique quais módulos ela toca. Uma tarefa pode tocar vários. Exemplo: uma feature full stack ativa `quality`, `sec`, `front` e `back`.
2. Para cada módulo ativado, leia `.harness/modules/<módulo>.md` quando existir. Ele diz quais skills do módulo usar e em que condição. Módulos sem esse arquivo usam as skills listadas na tabela abaixo.
3. Siga a ordem `sec`, `quality`, `front`, `back`, `debug`. Carregue só os módulos e as skills que a tarefa pede.
4. Se uma skill listada não existir no projeto, avise o usuário em uma linha e siga sem ela. Não invente um substituto.
5. O pedido explícito do usuário e as regras do projeto (`GUIDELINES.md`, `AGENTS.md`) prevalecem sobre as skills.

## Módulos

| Módulo | Quando ativar | Skills |
|---|---|---|
| `quality` | Sempre que a tarefa criar, alterar ou revisar código. | _a definir_ |
| `sec` | Sempre que a tarefa mexer em código executável, configuração, dependências, autenticação, permissões ou fluxo de dados. Não ativa para edição só de documentação. | _a definir_ |
| `front` | Interface renderizada: páginas, componentes, layout, responsividade, estados visuais, animação. | Ver `.harness/modules/front.md` |
| `back` | Endpoints, serviços, regras de negócio, persistência, integrações, jobs, webhooks. | Ver `.harness/modules/back.md` |
| `debug` | Investigar bug, erro, falha, comportamento inesperado, regressão ou lentidão. | `diagnosing-bugs` (pendente) |
