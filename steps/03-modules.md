# Etapa 3: módulos de skills

Instala todos os módulos do harness-phd no projeto e conecta o roteador ao `CLAUDE.md` e ao `AGENTS.md`. O roteador fica sempre carregado; as skills só são lidas quando a tarefa ativa o módulo delas.

## 1. Baixar os módulos

1. Clone o harness numa pasta temporária fora do projeto: `git clone --depth 1 https://github.com/Pedro-phd/harness-phd <tmp>/harness-phd`.
2. Registre o commit com `git -C <tmp>/harness-phd rev-parse --short HEAD`.

## 2. Instalar as skills

As skills dos módulos ficam em `.harness/skills/`, fora das pastas que os agentes varrem (`.claude/skills/`, `.agents/skills/`). Assim, os nomes e as descrições delas não entram em toda sessão: o agente só lê uma skill quando o roteador mandar.

1. Substitua `.harness/skills/` inteira pelo conteúdo de todas as pastas `modules/<módulo>/skills/<nome>/` do harness, ignorando `.gitkeep`. A pasta é só do harness; nada de fora deve ficar nela.
2. Skills citadas nos `MODULE.md` que vêm de outras etapas (toolkit, ship-it) não são instaladas aqui.
3. Migração de versões antigas: se existir `.harness/skills.lock`, apague de `.claude/skills/` e de `.agents/skills/` cada skill listada nele e depois apague o lock. Não toque em skills que não estejam no lock.

## 3. Instalar plugins externos (só Claude Code)

Alguns módulos usam plugins do Claude Code que não são skills portáteis. Eles ficam instalados na máquina, como o ship-it.

| Plugin | Módulo | Marketplace |
|---|---|---|
| `insecure-defaults@trailofbits` | sec | `trailofbits/skills` |

1. Verifique com `claude plugin list`. Para cada plugin ausente: `claude plugin marketplace add <marketplace>` (se o marketplace ainda não estiver registrado) e `claude plugin install <plugin>`. Para os presentes: `claude plugin update <plugin>`.
2. Fora do Claude Code, pule este passo e registre nas pendências que esses plugins não estão disponíveis neste agente.

## 4. Instalar o roteador

1. Copie `modules/ROUTER.md` do harness para `.harness/ROUTER.md`, substituindo a versão anterior.
2. Para cada `modules/<módulo>/MODULE.md` do harness, copie para `.harness/modules/<módulo>.md`. Apague de `.harness/modules/` os arquivos de módulos que não existem mais no harness.
3. No `CLAUDE.md` da raiz, garanta a linha `@.harness/ROUTER.md`. Ela importa o roteador em toda sessão do Claude Code. Crie o arquivo se não existir. Não duplique a linha e não altere o resto do arquivo.
4. No `AGENTS.md` da raiz, garanta a linha `Antes de qualquer tarefa, leia e siga .harness/ROUTER.md.` o mais perto possível do topo, logo após o título. Mesmas regras: sem duplicar, sem alterar o resto.

## 5. Concluir

1. Apague a pasta temporária.
2. Verifique se `.harness/ROUTER.md`, `.harness/modules/` e `.harness/skills/` existem, se as duas linhas estão no `CLAUDE.md` e no `AGENTS.md`, e se cada skill citada nos `MODULE.md` como deste módulo tem `.harness/skills/<nome>/SKILL.md`.
3. Meça o contexto que entra em toda sessão:
   - Claude Code: `CLAUDE.md` mais todos os arquivos que ele importa com `@`, recursivamente (por exemplo `@AGENTS.md` e `@.harness/ROUTER.md`). Conte cada arquivo uma vez.
   - Outros agentes: `AGENTS.md`.
   - Estime os tokens como caracteres ÷ 4 e informe o total de cada um, com os três maiores trechos.
   - Se `CLAUDE.md` importa `AGENTS.md` e os dois têm a mesma seção (por exemplo `## Agent skills` ou `## Guidelines`, escritas pelo ship-it), aponte a duplicação. Não remova: o ship-it mantém as duas cópias em sincronia.
   - Acima de 6.000 tokens, sugira ao usuário o que enxugar. Não corte nada sem aprovação.
4. Registre no progresso: commit do harness, skills instaladas por módulo, conflitos, tokens medidos e pendências.
