# PHASE-02-DISCOVERY-READINESS.md

**Projeto:** PMOC Software — Product & Engineering Master Specification
**Organização:** Services.NET
**Fase:** 2 — Requirements Discovery Preparation
**Versão:** v0.1-DRAFT
**Data:** 23/09/2026
**Autor:** Codex — documentação, estruturação e preparação de descoberta
**Status:** DRAFT — pronto para revisão da Services.NET; nenhuma entrevista presumida ou executada

---

## 1. Resumo

Esta execução iniciou a preparação da Fase 2 sem avançar para elicitação real com a Clima Zero.

Foram produzidos os artefatos de preparação, roteiros, registros estruturados e matriz regulatória preliminar solicitados. Os arquivos v0.2 aprovados da Fase 1 foram preservados; os registros existentes receberam cópias v0.3-DRAFT para a preparação da Fase 2.

Nenhum requisito foi marcado como Approved. Nenhuma resposta foi atribuída à Clima Zero. Nenhum parâmetro regulatório, faixa, limite ou periodicidade foi carregado.

---

## 2. Artefatos Produzidos

| ID | Artefato | Arquivo | Status |
| --- | --- | --- | --- |
| DOC-009 | Requirements Discovery Plan | `DOC-009 - Requirements Discovery Plan - v0.1-DRAFT.docx` | Produzido |
| DOC-010 | Clima Zero — Tenant Pilot Discovery Guide | `DOC-010 - Clima Zero - Tenant Pilot Discovery Guide - v0.1-DRAFT.docx` | Produzido |
| XLS-006 | Pain Points & Opportunities Register | `XLS-006 - Pain Points & Opportunities Register - v0.1-DRAFT.xlsx` | Template |
| XLS-007 | Functional Requirements Catalog | `XLS-007 - Functional Requirements Catalog - v0.1-DRAFT.xlsx` | Estrutura |
| XLS-008 | Business Rules Catalog | `XLS-008 - Business Rules Catalog - v0.1-DRAFT.xlsx` | Estrutura |
| XLS-009 | Security Requirements Register | `XLS-009 - Security Requirements Register - v0.1-DRAFT.xlsx` | Estrutura |
| XLS-010 | Data & Privacy Requirements Register | `XLS-010 - Data & Privacy Requirements Register - v0.1-DRAFT.xlsx` | Estrutura |
| XLS-011 | Operational Requirements Register | `XLS-011 - Operational Requirements Register - v0.1-DRAFT.xlsx` | Estrutura |
| XLS-012 | UX Requirements Register | `XLS-012 - UX Requirements Register - v0.1-DRAFT.xlsx` | Estrutura |
| XLS-013 | Regulatory & Compliance Matrix | `XLS-013 - Regulatory & Compliance Matrix - v0.1-DRAFT.xlsx` | Preliminar, fontes verificadas |
| XLS-014 | Roles & Permissions Matrix | `XLS-014 - Roles & Permissions Matrix - v0.1-DRAFT.xlsx` | Estrutura inicial |
| XLS-015 | Lifecycle & Status Discovery Register | `XLS-015 - Lifecycle & Status Discovery Register - v0.1-DRAFT.xlsx` | Estrutura inicial |
| XLS-005 | Requirements Traceability Matrix | `XLS-005 - Requirements Traceability Matrix - v0.3-DRAFT.xlsx` | Preparada para expansão |
| XLS-001 | Assumptions, Constraints and Dependencies Register | `XLS-001 - Assumptions, Constraints and Dependencies Register - v0.3-DRAFT.xlsx` | Atualização draft |
| XLS-002 | Risk Register | `XLS-002 - Risk Register - v0.3-DRAFT.xlsx` | Atualização draft |
| XLS-003 | Open Questions Register | `XLS-003 - Open Questions Register - v0.3-DRAFT.xlsx` | Atualização draft |
| XLS-004 | Decision Log | `XLS-004 - Decision Log - v0.3-DRAFT.xlsx` | Atualização draft |

---

## 3. Fontes Consultadas

| Fonte | URL | Uso |
| --- | --- | --- |
| Planalto — Lei nº 13.589/2018 | https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13589.htm | Regra A — aplicabilidade do PMOC |
| Ministério da Saúde / BVSMS — Portaria GM/MS nº 3.523/1998 | https://bvsms.saude.gov.br/bvs/saudelegis/gm/1998/prt3523_28_08_1998.html | Regra B — responsável técnico; vigência jurídica formal pendente |
| AnvisaLegis — RE nº 9/2003 | https://anvisalegis.datalegis.net/action/ActionDatalegis.php?acao=abrirTextoAto&cod_menu=9434&cod_modulo=310&numeroAto=00000009&orgao=RE/DC/ANVISA/MS&seqAto=001&tipo=RES&valorAno=2003 | Registro de revogação pela RDC nº 886/2024 |
| AnvisaLegis — RDC nº 886/2024 | https://anvisalegis.datalegis.net/action/ActionDatalegis.php?acao=abrirTextoAto&cod_menu=9432&cod_modulo=310&link=S&numeroAto=00000886&orgao=ANVISA/MS&seqAto=222&tipo=RDC&valorAno=2024 | Revogação da RE nº 9/2003 |
| Biblioteca Digital da ANVISA — Guia nº 73/2024, versão 2 | https://bibliotecadigital.anvisa.gov.br/jspui/handle/anvisa/17752 | Guia não normativo que referencia a ABNT NBR 17037 após revogação da RE nº 9/2003 |
| ABNT Catálogo | https://www.abntcatalogo.com.br/ | Referência para aquisição/consulta legítima da ABNT NBR 17037 |
| Planalto — LGPD | https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709compilado.htm | Privacidade, bases legais pendentes de DPO |
| Confea — orientação PMOC/ART | https://www.confea.org.br/conselho-orienta-sobre-registro-de-art-de-plano-de-manutencao-operacao-e-controle | Fonte profissional oficial a investigar, sem transformar em requisito sem validação |

---

## 4. Regulamentos Encontrados / Registrados

| ID | Instrumento | Tratamento nesta execução |
| --- | --- | --- |
| REG-001 | Lei nº 13.589/2018 | Fonte federal principal da Regra A. |
| REG-002 | Portaria GM/MS nº 3.523/1998 | Fonte conhecida da Regra B; confirmação jurídica formal ainda necessária. |
| REG-003 | RE/ANVISA nº 9/2003 | Revogada; manter rastreabilidade histórica. |
| REG-004 | RDC/ANVISA nº 886/2024 | Revoga a RE nº 9/2003; registrar retificação e efeitos jurídicos pendentes. |
| REG-005 | Guia ANVISA nº 73/2024, versão 2 | Não normativo, recomendatório e não vinculante; registra referência à ABNT NBR 17037. |
| REG-006 | ABNT NBR 17037 | Norma técnica; conteúdo não reproduzido; aquisição legítima e validação jurídica/técnica pendentes. |
| REG-007 | Lei nº 13.709/2018 — LGPD | Relevante para dados e privacidade; bases legais pendentes de DPO. |

---

## 5. Documentos Ainda Necessários Da Clima Zero

- Modelo atual de PMOC.
- Ordens de serviço reais ou exemplos anonimizados.
- Checklists utilizados em campo.
- Relatórios e documentos entregues aos clientes.
- Planilhas de clientes, unidades, ambientes, sistemas HVAC e equipamentos.
- Contratos ou cláusulas operacionais relevantes, quando autorizado.
- Modelos de ART/TRT e documentos de responsável técnico, quando autorizado.
- Registros de manutenção, medições, fotos e evidências.
- Modelos de não conformidade e ações corretivas.
- Cronogramas e documentos utilizados em fiscalização.

---

## 6. Stakeholders A Entrevistar

- Direção / proprietário da Clima Zero.
- Gestor operacional.
- Responsável técnico.
- Supervisor.
- Técnico de campo.
- Administrativo / back-office.
- Financeiro, quando aplicável.
- Product Owner institucional da Services.NET.
- Jurídico / Regulatório.
- DPO / Encarregado de Dados.

---

## 7. Novas Open Questions

| ID | Questão |
| --- | --- |
| OQ-023 | Quais estados, municípios, tipos de clientes e ambientes do piloto delimitam a pesquisa regulatória local/setorial? |
| OQ-024 | Quais documentos reais a Clima Zero autoriza compartilhar, em qual formato e com quais restrições? |
| OQ-025 | Quem será o responsável técnico operacional designado para validação técnica? |
| OQ-026 | Quem serão as autoridades nominais de Jurídico/Regulatório e DPO? |
| OQ-027 | Qual recorte de volumetria será usado como baseline inicial? |
| OQ-028 | Quais exigências de fiscalização, auditoria, contrato ou cliente final já foram enfrentadas pela Clima Zero? |

---

## 8. Novos Riscos

| ID | Risco |
| --- | --- |
| RSK-020 | Entrevistas iniciarem sem gate de preparação aprovado. |
| RSK-021 | Exigências estaduais, municipais, setoriais ou contratuais relevantes não serem identificadas. |
| RSK-022 | Evidências do tenant-piloto chegarem incompletas, desatualizadas ou sem autorização de uso. |
| RSK-023 | Prática operacional do tenant ser interpretada como obrigação legal sem validação de fonte. |

---

## 9. Novas Dependências

| ID | Dependência |
| --- | --- |
| DEP-011 | Pacote documental inicial da Clima Zero, com autorização de uso e restrições de confidencialidade. |
| DEP-012 | Nomeação de participantes por perfil e agenda de entrevistas. |
| DEP-013 | Agenda de revisão com Jurídico, DPO e responsável técnico. |

---

## 10. Gaps E Dependências De Decisão

- Autoridades nominais de Jurídico, DPO e responsável técnico ainda não designadas.
- Recorte regulatório local/setorial do piloto ainda não definido.
- Evidências reais da Clima Zero ainda não recebidas.
- Volumetria operacional real ainda não levantada.
- Bases legais LGPD pendentes de DPO.
- Extensão da aplicabilidade da ABNT NBR 17037 pendente de Jurídico e responsável técnico.
- Nenhuma autorização formal de início de entrevistas foi registrada nesta execução.

---

## 11. Decisões Propostas

| ID | Decisão proposta | Status |
| --- | --- | --- |
| DEC-012 | Conduzir a Fase 2 inicialmente como Discovery Preparation, com gate formal antes das entrevistas. | Proposta |
| DEC-013 | Preservar os artefatos v0.2 APPROVED da Fase 1 e publicar registros de preparação da Fase 2 como versões DRAFT separadas. | Proposta |

---

## 12. Conflitos Encontrados Com A Fase 1

Nenhum conflito material foi identificado.

A preparação reforça decisões já aprovadas ou abertas na Fase 1:

- Preserva a governança documental da DEC-011.
- Mantém DEC-001 a DEC-010 como Proposta.
- Mantém Regra A e Regra B separadas.
- Mantém CAP-054 como A validar.
- Mantém LGPD sob validação do DPO.
- Mantém conteúdo regulatório concreto bloqueado até validação jurídica e técnica.

---

## 13. Readiness

**Readiness status:** READY para revisão da Services.NET.

O pacote está pronto para ser apresentado à Services.NET como preparação da Fase 2. Ele ainda não autoriza, por si só, a execução das entrevistas. A passagem para elicitação depende do gate formal previsto no Master Specification.

**Fase 2 — Discovery Preparation READY para revisão da Services.NET. Nenhuma entrevista foi presumida ou executada.**
