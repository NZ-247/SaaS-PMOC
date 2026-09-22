# Overview_Project.md — PATCH v0.2

**Projeto:** PMOC Software — Product & Engineering Master Specification
**Origem:** **Services.NET Phase 1 Audit — Approved** (item §14 da auditoria)
**Data:** 22/09/2026
**Referência de controle de mudança:** CHG-12 / CHG-13 (XLS-004 — aba Change Control)

---

## Aviso obrigatório sobre esta entrega

O arquivo-fonte `Overview_Project.md` **não estava disponível no ambiente desta execução**. Ele não consta dos artefatos produzidos na Fase 1 nem foi localizado nos dados corporativos consultados.

Por isso, **não foi possível editar o arquivo original**. Em vez de reconstruí-lo por inferência — o que violaria a proibição de invenções do Master Specification §25 — esta entrega é um **patch**: contém o texto exato a ser aplicado e a instrução precisa da correção pendente.

**Ação requerida da Services.NET:** aplicar as duas alterações abaixo ao arquivo-fonte e devolver o resultado para conferência. Registrado como inconsistência residual **RES-03** no `PHASE-01-V0.2-CHANGE-REPORT.md`.

---

## Alteração 1 — Bloco de status a inserir no início do arquivo

Inserir o bloco abaixo como **primeiro conteúdo** do arquivo, antes de qualquer título, sumário ou texto existente.

```markdown
> **STATUS: REFERENCE / NON-AUTHORITATIVE**
>
> Este documento registra a concepção inicial do projeto.
> Em caso de divergência, prevalecem os artefatos aprovados do
> **PMOC Software — Product & Engineering Master Specification**
> e suas fontes autoritativas declaradas.
>
> Fontes autoritativas vigentes:
> - **Microsoft 365** — documentos executivos, planilhas de governança e visualizações (Fase 1: DOC-001 a DOC-008, XLS-001 a XLS-005, DIA-001).
> - **Repositório Git** — decisões próximas ao código (`/docs`, `README.md`, `AGENTS.md`, `CLAUDE.md`), a partir da Fase 10.
>
> Este documento **não** é fonte autoritativa para nenhuma informação.
> Ele não deve ser usado por engenheiros humanos nem por agentes de
> desenvolvimento (Opus, Claude Code, GPT Codex) como base para decisão
> de requisito, arquitetura, escopo, regra de negócio ou conformidade.
>
> Registrado em: CON-010 (XLS-001) e DOC-001 §30.
> Versão de referência desta marcação: v0.2 DRAFT — 22/09/2026.
> Origem: Services.NET Phase 1 Audit — Approved.
```

---

## Alteração 2 — Correção da duplicidade de `AGENTS.md`

**Problema identificado pela auditoria:** o arquivo `AGENTS.md` aparece **duas vezes** na lista de arquivos de governança sugeridos para o repositório.

**Correção:** remover a ocorrência duplicada, preservando **uma única** menção. A lista de arquivos de governança para agentes deve conter exatamente três entradas, sem repetição:

```markdown
- README.md
- AGENTS.md
- CLAUDE.md
```

**Verificação após aplicar:** uma busca por `AGENTS.md` no arquivo deve retornar apenas uma ocorrência dentro da lista de arquivos de governança. Menções em prosa explicativa fora da lista são aceitáveis, desde que não constituam item de lista duplicado.

---

## O que este patch deliberadamente NÃO faz

1. **Não transforma `Overview_Project.md` em fonte autoritativa.** O aviso tem efeito contrário: subordina o documento aos artefatos aprovados.
2. **Não reescreve, resume ou reorganiza o conteúdo existente.** Apenas prefixa o bloco de status e corrige a duplicidade apontada.
3. **Não reconstrói o arquivo por inferência.** Nenhum conteúdo foi presumido.
4. **Não harmoniza o conteúdo do documento com a v0.2.** Eventuais divergências entre `Overview_Project.md` e os artefatos aprovados permanecem — e é exatamente isso que o aviso de precedência resolve, sem exigir reescrita.
5. **Não cria `AGENTS.md` nem `CLAUDE.md`.** Esses arquivos serão produzidos na Fase 10, conforme o Master Specification §21 e §23 da instrução de revisão.

---

## Conferência sugerida após aplicação

| # | Verificação | Resultado esperado |
| --- | --- | --- |
| 1 | O bloco de status é o primeiro conteúdo do arquivo | Sim |
| 2 | O texto "STATUS: REFERENCE / NON-AUTHORITATIVE" está presente e visível | Sim |
| 3 | `AGENTS.md` aparece uma única vez na lista de arquivos de governança | Sim |
| 4 | `README.md` e `CLAUDE.md` aparecem uma vez cada | Sim |
| 5 | Nenhum outro conteúdo do arquivo foi alterado | Sim |
| 6 | O arquivo continua legível como registro histórico de concepção | Sim |
