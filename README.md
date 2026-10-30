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
- Etapa 2: [ship-it](https://github.com/samsantosb/ship-it), criado por [Samuel Santos](https://github.com/samsantosb), licença MIT.

O harness-phd não copia esses projetos: ele lê os arquivos direto dos repositórios originais em cada execução. Todo o crédito pelo conteúdo é dos autores.
