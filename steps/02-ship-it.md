# Etapa 2: pipeline de entrega com o ship-it

ship-it: https://github.com/samsantosb/ship-it

Esta etapa roda depois do toolkit de propósito. O `/groundwork` detecta os comandos de validação e as convenções que o toolkit configurou, e o `/make-guidelines` propõe regras a partir do código e do lint que já existem. As duas skills só acrescentam seções próprias ao `AGENTS.md` e ao `CLAUDE.md`, sem reescrever o que o toolkit gerou.

## 1. Instalar ou atualizar o ship-it

O ship-it fica instalado uma vez por máquina, nunca dentro do projeto.

1. Garanta uma cópia local em `~/.ship-it`:
   - Se a pasta não existir: `git clone https://github.com/samsantosb/ship-it ~/.ship-it`
   - Se existir: `git -C ~/.ship-it pull --ff-only`
   - Registre o commit com `git -C ~/.ship-it rev-parse --short HEAD`.
2. No Claude Code, registre também o plugin para ter os slash commands nas próximas sessões. Verifique com `claude plugin list`. Se o `ship-it` não aparecer, rode `claude plugin marketplace add samsantosb/ship-it` e `claude plugin install ship-it@ship-it`. Se já aparecer, rode `claude plugin marketplace update ship-it` e `claude plugin update ship-it@ship-it`. Se algum comando não existir na versão instalada, informe o usuário e siga com a cópia local.
3. Nesta sessão, execute as skills pela cópia local, sem reiniciar: siga `~/.ship-it/AGENTS.md`, com `${CLAUDE_PLUGIN_ROOT}` apontando para `~/.ship-it`, e abra `~/.ship-it/skills/<nome>/SKILL.md`. Os arquivos gerados vão para a pasta do projeto, nunca para `~/.ship-it`.

## 2. Rodar o groundwork

Execute `~/.ship-it/skills/groundwork/SKILL.md` no projeto. Ele resolve tracker, repo, reviewer, notifier, validação e idioma, e faz uma única rodada de perguntas. Responda o que for possível a partir do que o toolkit registrou em `docs/setup.md` e `docs/quality.md`. Pergunte ao usuário só o que não der para decidir com segurança.

## 3. Rodar o make-guidelines

Execute `~/.ship-it/skills/make-guidelines/SKILL.md` sem argumento, para gerar o `GUIDELINES.md` da raiz. Use as regras de lint, os scripts e a documentação do toolkit como respostas propostas, não como perguntas do zero.

Em projeto novo ainda há pouco código. Gere as guidelines mesmo assim e registre nas pendências: "rodar `/make-guidelines` de novo depois das primeiras tasks".

## 4. Documento de produto

O toolkit mantém o `PRODUCT.md` na raiz como visão geral do produto. Cada feature nova entra pelo `/create-product`, em `docs/product/<slug>.md`. Não mova nem apague o `PRODUCT.md`. Se o `AGENTS.md` não deixar essa divisão clara, acrescente uma linha explicando.

## 5. Concluir

Verifique se existem `docs/agents/*.md`, `GUIDELINES.md` e as seções `## Agent skills` e `## Guidelines` no `AGENTS.md` e no `CLAUDE.md`. Registre no progresso: commit do ship-it, papéis resolvidos e pendências.

Mostre ao usuário o fluxo do dia a dia:

```
/create-product <ideia>  →  /create-tasks <doc>  →  /do-task <card>  →  /watch-pr  →  /chaos-engineering
```

No Claude Code, os comandos ficam como `/ship-it:<skill>` a partir da próxima sessão. Em outros agentes, peça: "Siga ~/.ship-it/AGENTS.md e rode skills/<skill>/SKILL.md com <argumento>".
