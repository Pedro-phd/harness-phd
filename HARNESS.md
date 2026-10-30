# harness-phd

Você é o agente executando o harness-phd na pasta aberta. Execute as etapas abaixo em sequência, sem pedir permissão entre elas. Cada etapa é um arquivo neste repositório:

https://raw.githubusercontent.com/Pedro-phd/harness-phd/main/steps/<arquivo>

## Progresso

O progresso fica em `.harness/state.md`, na pasta do projeto. É ele que permite rodar tudo em sequência sem se perder.

1. Antes de tudo, leia `.harness/state.md`. Se não existir, crie com a lista de etapas abaixo, todas como `pendente`.
2. Pule as etapas marcadas como `concluída`. Comece pela primeira etapa `pendente` ou `em andamento`. Uma etapa `em andamento` foi interrompida: retome a partir do que já existe no projeto, sem refazer o que está feito.
3. Ao iniciar uma etapa, marque `em andamento`. Ao terminar e verificar, marque `concluída` com a data e um resumo de uma linha (versões, decisões, pendências). Atualize o arquivo antes de passar para a próxima etapa.
4. Se uma etapa bloquear, marque `bloqueada` com o motivo, pare e relate. Não pule etapas.

Formato do arquivo:

```markdown
# harness-phd: progresso

| Etapa | Status | Data | Resumo |
|---|---|---|---|
| 01-toolkit | concluída | 2026-10-30 | toolkit @ abc1234, projeto existente, prompt 12 |
| 02-ship-it | pendente | | |
```

Se o arquivo listar etapas antigas ou faltar alguma etapa nova da lista abaixo, ajuste a tabela para seguir a lista atual, mantendo os status já registrados.

## Regras gerais

- Leia cada etapa direto da URL acima, sempre da `main`, no momento de executá-la. Não use cópias antigas nem resumos de memória.
- Ao começar uma etapa, releia o arquivo dela, mesmo que já o tenha lido antes na sessão.
- Responda no idioma do usuário.
- Se o contexto da sessão estiver perto do limite, termine a etapa atual, atualize o progresso e diga ao usuário para colar o mesmo comando numa sessão nova.
- Ao final de todas as etapas, faça um resumo: etapas concluídas, evidências e pendências.

## Etapas

1. `01-toolkit.md`: configuração base com o Vibe Coding Toolkit.
2. `02-ship-it.md`: pipeline de entrega com o ship-it (groundwork, guidelines e workflow).
