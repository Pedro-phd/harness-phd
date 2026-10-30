# Etapa 1: configuração base com o Vibe Coding Toolkit

Toolkit: https://github.com/soumatheusgomes/vibe-coding-toolkit

## 1. Registrar a versão do toolkit

Execute `git ls-remote https://github.com/soumatheusgomes/vibe-coding-toolkit HEAD` e guarde o commit. Ele é a versão usada nesta execução e deve aparecer no resumo final.

## 2. Detectar o tipo de projeto

Inspecione a pasta aberta, incluindo arquivos ocultos.

- Se a pasta for o próprio vibe-coding-toolkit ou o harness-phd, pare e pergunte ao usuário qual é a pasta de destino.
- **Projeto existente**: há código, manifesto ou histórico. Exemplos: `package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `composer.json`, `Gemfile`, `src/`, `app/`, ou um `.git` com pelo menos um commit.
- **Projeto novo**: a pasta está vazia, ou só tem arquivos sem código (por exemplo `.git` sem commits, `.DS_Store`, `.gitignore`, `README.md`, `LICENSE`, `.claude/`, `.codex/`, `.vscode/`, `.idea/`).
- Se ficar ambíguo, mostre ao usuário o que encontrou e pergunte. Não escolha no escuro.

Informe ao usuário o tipo detectado e o motivo em uma linha antes de continuar.

## 3. Executar o setup correspondente

- **Projeto existente**: leia https://raw.githubusercontent.com/soumatheusgomes/vibe-coding-toolkit/main/docs/prompts/12-existing-project-setup.md e execute todo o bloco da seção "Prompt" nesta pasta, começando pelo brainstorming.
- **Projeto novo**: leia https://raw.githubusercontent.com/soumatheusgomes/vibe-coding-toolkit/main/docs/prompts/11-next-project-bootstrap.md e execute todo o bloco da seção "Prompt" nesta pasta. Se o usuário não descreveu o projeto (nome, problema, público, fluxos principais e restrições), peça essa descrição antes de começar.

Siga as regras do prompt do toolkit. Elas prevalecem sobre este arquivo em caso de conflito sobre o setup.

## 4. Concluir

A etapa termina quando o prompt do toolkit chega ao fim com as verificações dele. Registre no resumo: commit do toolkit, tipo de projeto, prompt usado e pendências. Depois volte ao HARNESS.md e siga para a próxima etapa, se houver.
