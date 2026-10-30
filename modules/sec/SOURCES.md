# Origem das skills do módulo sec

| Skill | Origem | Commit | Licença |
|---|---|---|---|
| `secure-by-default` | Autoral (Pedro-phd), do `meu_herness` v0.3.1. `references/evidence-and-findings.md` adapta princípios do `security-audit-skill` da Cloudflare, reduzidos ao escopo do dia a dia. | `c1c8a8c` (referência adaptada) | Mesma do harness-phd; trecho adaptado sob MIT (`LICENSE.cloudflare`) |
| `security-audit` | [cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill), sem alterações | `c1c8a8c` (2026-09-14) | MIT © Cloudflare (`LICENSE` na pasta) |
| `backend-security` | Autoral (Pedro-phd), do `meu_herness` v0.3.1, com ideias extraídas de [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) `security-and-hardening` (threat model, fronteiras de confiança, SSRF, supply chain) | `be4e44a` | Mesma do harness-phd; trecho derivado sob MIT (`LICENSE.addy`) |

## Plugins externos (não copiados)

| Plugin | Origem | Licença | Por que não é copiado |
|---|---|---|---|
| `insecure-defaults` | [trailofbits/skills](https://github.com/trailofbits/skills), marketplace `trailofbits` | CC-BY-SA-4.0 | É um plugin do Claude Code (comando + workflow), não uma skill portátil. A etapa 3 instala pelo marketplace. |
