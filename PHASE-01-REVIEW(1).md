# PHASE-01-REVIEW.md

**Projeto:** PMOC Software — Plataforma de Gestão de Manutenção, Ativos e Conformidade para Sistemas de Climatização
**Organização:** Services.NET
**Fase:** 1 — Product Charter e Escopo
**Versão:** **0.2 DRAFT** · Versão anterior: 0.1 DRAFT (baseline histórica, preservada)
**Data:** 22/09/2026
**Origem das alterações:** **Services.NET Phase 1 Audit — Approved**
**Autor:** Opus — análise, arquitetura, documentação, modelagem, revisão e planejamento
**Status:** **Aguardando segunda revisão formal da Services.NET. A Fase 1 não está APPROVED. A Fase 2 não foi iniciada.**

> Este documento substitui integralmente a versão v0.1. Afirmações desatualizadas da v0.1 não foram reaproveitadas. O detalhamento das alterações está em `PHASE-01-V0.2-CHANGE-REPORT.md`.

---

## 1. Resumo

A Fase 1 entrega a visão formal do produto antes de qualquer levantamento detalhado de requisitos ou implementação: 8 documentos narrativos (DOC-001 a DOC-008), 5 planilhas de governança (XLS-001 a XLS-005), 1 diagrama de contexto conceitual (DIA-001), este documento de revisão e o relatório de mudanças da v0.2.

O produto é concebido, conforme o Master Specification §5, como **plataforma de gestão de manutenção, ativos, operações de campo, conformidade, evidências e inteligência operacional**, tendo o PMOC como **primeiro domínio regulatório atendido** — não como sistema de preenchimento de PMOC.

Números verificados nesta versão: **79 capacidades** catalogadas (50 MVP, 19 Pós-MVP, 5 Futuro, 5 A validar), **12 hipóteses**, **12 restrições**, **10 dependências**, **21 questões abertas**, **19 riscos**, **10 decisões propostas**, **8 ADRs indexados e nenhum decidido**, **11 critérios de aceite do MVP** e **13 linhas semente na RTM**.

Nenhum código foi produzido. Nenhuma tecnologia foi considerada definitiva. Nenhum ADR foi decidido. Nenhum parâmetro regulatório foi carregado. Nenhum requisito, norma, obrigação legal, periodicidade, perfil profissional obrigatório, norma técnica ou fluxo operacional do cliente foi inventado.

---

## 2. Artefatos entregues

| ID | Artefato | Formato | Versão | Recomendação |
| --- | --- | --- | --- | --- |
| DOC-001 | PMOC Software — Product Charter | Word | 0.2 DRAFT | Aprovar com ressalvas |
| DOC-002 | Product Vision and Product Principles | Word | 0.2 DRAFT | Aprovar |
| DOC-003 | Project Scope | Word | 0.2 DRAFT | Aprovar |
| DOC-004 | Stakeholder Map | Word | 0.2 DRAFT | Aprovar com ressalvas |
| DOC-005 | Personas — versão inicial | Word | 0.2 DRAFT | Revisar (hipótese não validada) |
| DOC-006 | Product Capabilities Map | Word | 0.2 DRAFT | Aprovar |
| DOC-007 | MVP Definition | Word | 0.2 DRAFT | Aprovar com ressalvas |
| DOC-008 | Product Roadmap — visão macro | Word | 0.2 DRAFT | Aprovar com ressalvas |
| XLS-001 | Assumptions, Constraints and Dependencies Register | Excel | 0.2 DRAFT | Aprovar |
| XLS-002 | Risk Register | Excel | 0.2 DRAFT | Aprovar |
| XLS-003 | Open Questions Register | Excel | 0.2 DRAFT | Aprovar |
| XLS-004 | Decision Log + ADR Register + Change Control | Excel | 0.2 DRAFT | Aprovar como propostas |
| XLS-005 | Requirements Traceability Matrix — estrutura inicial | Excel | 0.2 DRAFT | Aprovar a estrutura |
| DIA-001 | System/Product Context Diagram — nível conceitual | PNG | 0.2 DRAFT | Aprovar |
| — | PHASE-01-V0.2-CHANGE-REPORT.md | Markdown | 0.2 | Aprovar |
| — | Overview_Project.md — PATCH v0.2 | Markdown | 0.2 | **Aplicar ao arquivo-fonte e devolver para conferência** |

Fonte autoritativa nesta fase: Microsoft 365. A representação em Markdown no repositório Git (`/docs`, `README.md`, `AGENTS.md`, `CLAUDE.md`) será criada na Fase 10. `Overview_Project.md` é **REFERENCE / NON-AUTHORITATIVE**.

---

## 3. O que foi solucionado nesta revisão

| # | Achado da auditoria | Situação |
| --- | --- | --- |
| 1 | Cadeia normativa quebrada após a revogação da RE nº 9/2003 | **Resolvido quanto à identificação.** ABNT NBR 17037 incorporada como norma técnica, com natureza jurídica preservada. Extensão da aplicabilidade permanece pendente (OQ-004) |
| 2 | Tratamento do limite de 5 TR / 60.000 BTU/h como divergência única | **Resolvido conceitualmente.** Regra A (aplicabilidade do PMOC) e Regra B (exigência de responsável técnico) separadas em DOC-001 §5.3. Critérios pendentes (OQ-021) |
| 3 | Redação da OQ-012 sugeria ausência de evidência de aplicação da Portaria | **Resolvido.** Reformulada; reconhece disponibilidade oficial, referência posterior e fortes evidências de aplicação; mantém pendente apenas a confirmação jurídica formal |
| 4 | Tensão entre CAP-033 no MVP e o critério que veda dependência jurídica pendente | **Resolvido.** Capacidade estrutural no MVP; conteúdo regulatório excluído (OOS-015) e condicionado (AC-MVP-11) |
| 5 | `TenantId` prescrito como coluna física | **Resolvido.** Regra semântica e de segurança mantida; implementação física remetida ao ADR-001 |
| 6 | Assinatura em três estados contraditórios | **Resolvido.** Estado único "A validar", sem nível presumido |
| 7 | OQ-006 formulada de modo binário | **Resolvido.** Reformulada para nível de identificação, manifestação de vontade, autoria, integridade e não repúdio por ato/documento |
| 8 | AC-MVP-03 exigia checklist para toda OS | **Resolvido.** Requisitos obrigatórios por tipo de OS e template |
| 9 | AC-MVP-08 excessivamente literal | **Resolvido.** Contrato para operação de negócio ou server-side; sem endpoint artificial |
| 10 | Jurídico e DPO tratados como autoridade única | **Resolvido.** STK-007 e STK-021 separados; RACI desdobrado; responsáveis atualizados em registros |
| 11 | ADR-008 sem posição clara no roadmap | **Resolvido.** Pré-requisito das partes dependentes do modelo de Compliance as Data |
| 12 | `Overview_Project.md` competindo com artefatos aprovados | **Resolvido via patch.** Arquivo-fonte não disponível neste ambiente |
| 13 | Erro de consolidação na Summary de XLS-001 | **Resolvido.** Fórmulas corrigidas; verificação estendida às demais planilhas |
| 14 | Estado de referência do PMOC emitido não explicitado | **Resolvido como princípio.** PP-13, CAP-037, AC-MVP-02, OQ-020, RSK-019. Modelagem permanece para as Fases 3 e 6 |
| 15 | DIA-001 com sobreposições de rótulo | **Resolvido.** Ajustes de legibilidade; fronteiras conceituais preservadas |
| — | **Erro de consolidação de capacidades não apontado pela auditoria** | **Encontrado e corrigido na validação cruzada:** a v0.1 declarava 77/43; a contagem real do catálogo é **79/50** |

---

## 4. Decisões propostas (permanecem `Proposta` — XLS-004)

A aceitação da auditoria **não** converteu decisões em aprovadas. As dez decisões seguem com status `Proposta`; a aceitação está registrada como **AUDIT-01** na aba Change Control.

| ID | Decisão proposta |
| --- | --- |
| DEC-001 | Plataforma de manutenção/ativos/campo/conformidade; PMOC como primeiro domínio regulatório |
| DEC-002 | Nome comercial não definido nesta fase |
| DEC-003 | Modular Monolith + API First como hipótese, a confirmar por ADR |
| DEC-004 | Multi-tenancy como regra semântica e de segurança; modelo físico em ADR-001 |
| DEC-005 | Compliance as Data, distinguindo capacidade estrutural de conteúdo regulatório |
| DEC-006 | MVP Web First; mobile e offline Pós-MVP |
| DEC-007 | Auditoria de negócio na primeira versão, separada de log técnico |
| DEC-008 | Roadmap por ondas de valor, sem datas |
| DEC-009 | Normas técnicas referenciadas, nunca reproduzidas; norma técnica não recebe status de lei |
| DEC-010 | Nenhum código antes da aprovação documental e dos ADRs estruturantes |

---

## 5. Decisões ainda necessárias

**Antes de aprovar a Fase 1:**
1. Nomeação de patrocinador (OQ-002) e Product Owner (OQ-003).
2. Identificação da autoridade jurídica (GAP-005) e do DPO/Encarregado (GAP-006).
3. Confirmação formal do cliente-piloto (OQ-010).
4. Definição de equipe, orçamento e prazo (OQ-007).
5. Confirmação do modelo de operação e SLA (OQ-011).

**Antes de iniciar a implementação (W1):**
6. ADR-001 — isolamento multi-tenant.
7. ADR-002 — estratégia de identificadores.
8. ADR-003 e ADR-004 — stacks de back-end e front-end.
9. ADR-005 — armazenamento de evidências.
10. ADR-006 — modelo de auditoria de negócio.
11. **ADR-008 — modelo de dados de Compliance as Data** (pré-requisito de CAP-030 a CAP-035, CAP-037 e CAP-038).
12. Mecanismo de preservação do estado de referência do PMOC (OQ-020), nas Fases 3 e 6.

**Dependentes de terceiros:**
13. Parecer jurídico sobre a extensão da aplicabilidade da ABNT NBR 17037, sobre a Portaria GM/MS nº 3.523/1998, sobre a distinção Regra A / Regra B e sobre o nível probatório exigido (DEP-001).
14. Parecer do DPO sobre bases legais, retenção e direitos dos titulares (DEP-010).
15. Parecer de responsável técnico sobre periodicidades e parâmetros (DEP-002).
16. Aquisição legítima da ABNT NBR 17037 e demais normas aplicáveis (DEP-003).

---

## 6. Hipóteses (12 — XLS-001)

Nenhuma hipótese é requisito confirmado. As de maior impacto:

| ID | Hipótese | Impacto se falsa |
| --- | --- | --- |
| ASM-001 | Existe cliente-piloto disponível para validar requisitos | Fase 2 produziria requisitos presumidos |
| ASM-004 | Há conectividade suficiente para uso Web no campo | PWA/offline precisaria ser antecipado para o MVP |
| ASM-008 | A prestadora possui responsável técnico habilitado | Modelo de responsabilidade do produto muda |
| ASM-010 | Equipamento é a menor unidade de inventário necessária ao MVP | Modelo de domínio e checklists mudam |
| ASM-011 | Periodicidades virão de responsável técnico habilitado | Engenharia ficaria sem fonte legítima de regra |
| **ASM-012** | **Reformulada na v0.2:** a plataforma precisará registrar alguma manifestação de vontade; **o nível exigido não é assumido** | Valor probatório, UX da OS e arquitetura mudam |

---

## 7. Questões abertas (21 — XLS-003)

**14 de prioridade alta.** Bloqueantes para o avanço:

- **OQ-002 / OQ-003** — patrocinador e Product Owner não designados.
- **OQ-010** — cliente-piloto não confirmado.
- **OQ-004** — extensão da aplicabilidade da ABNT NBR 17037 (reformulada).
- **OQ-012** — confirmação formal quanto à Portaria GM/MS nº 3.523/1998 (reformulada).
- **OQ-021** — critérios da Regra A e da Regra B (**nova**).
- **OQ-019** — referência oficial exata da orientação da ANVISA (**nova**).
- **OQ-020** — mecanismo de preservação do estado de referência do PMOC (**nova**).
- **OQ-006** — nível de identificação e manifestação de vontade (reformulada).
- **OQ-015** — bases legais da LGPD, agora sob o DPO (responsável corrigido).
- **OQ-018** — granularidade mínima de ativo exigida pelo piloto.

---

## 8. Riscos (19 — XLS-002)

| ID | Risco | Score |
| --- | --- | --- |
| RSK-003 | Scope creep no MVP | 16 |
| RSK-004 | Ausência de cliente-piloto engajado | 15 |
| RSK-006 | Definição tardia do modelo de multi-tenancy | 15 |
| RSK-017 | Backup existente com restore nunca testado | 15 |
| **RSK-019** | **PMOC emitido perder fidelidade ao estado que o originou (novo)** | **16** |
| RSK-001 | Extensão da aplicabilidade da referência técnica de qualidade do ar (**reduzido de 20 para 12**) | 12 |
| RSK-002 | Vazamento de dados entre tenants | 10 (impacto máximo) |

Score médio: 11,7. Riscos com score ≥ 15: 5.

---

## 9. Pontos de atenção regulatórios — estado atual

**INC-001 — Referência técnica de qualidade do ar (atualizado).** A Lei nº 13.589/2018 remete os parâmetros de qualidade do ar à RE/ANVISA nº 9/2003 "e posteriores alterações". A RE nº 9/2003 consta **revogada pela RDC/ANVISA nº 886, de 10/07/2024**. A **ABNT NBR 17037 — Qualidade do ar interior em ambientes não residenciais climatizados artificialmente — Padrões referenciais** consta vigente no catálogo da ABNT (primeira edição 04/2023; edição posterior 10/2024 incorporando errata) e é indicada como referência para o tema após a revogação, conforme orientação oficial da ANVISA de 2025 informada pela auditoria da Services.NET.

Tratamento adotado: a ABNT NBR 17037 é registrada como **norma técnica**, **não** como instrumento de status jurídico equivalente a lei, portaria ou resolução. Exige aquisição legítima (DEP-003), não é reproduzida, e a extensão de sua aplicabilidade ao produto depende de validação jurídica e de responsável técnico (OQ-004). **Nenhum parâmetro, faixa, limite ou periodicidade foi carregado.**

*Limite declarado:* a referência bibliográfica exata da orientação da ANVISA de 2025 não foi confirmada em fonte primária nesta execução — **OQ-019**.

**INC-002 — Portaria GM/MS nº 3.523/1998 (atualizado).** A Portaria permanece disponível em fontes oficiais e é referenciada em documentação regulatória posterior; há fortes evidências de aplicação atual. Esta revisão **não declara** sua vigência jurídica formal. OQ-012 foi reformulada para pedir a confirmação de eventual alteração, revogação, consolidação ou extensão atual, incluindo o limite de capacidade nela previsto.

**INC-003 — Regra A × Regra B (reescrito).** O tema deixou de ser tratado como divergência sobre limiar de capacidade. São regras distintas: **Regra A** determina a aplicabilidade do PMOC (Lei nº 13.589/2018); **Regra B** determina a exigência de responsável técnico (Portaria GM/MS nº 3.523/1998 e o limite de capacidade nela previsto — 5 TR / 60.000 BTU/h). **O limite não pode ser usado automaticamente como condição única para decidir a existência de PMOC.** Serão modeladas como `ApplicabilityRule` distintas (CAP-035, COMP-004), sem valores nesta fase. Critérios pendentes em OQ-021.

**INC-004 — Normas técnicas ABNT.** Protegidas por direito autoral: referenciadas, nunca reproduzidas. Aquisição legítima pendente (DEP-003). A relevância aumentou com a incorporação da NBR 17037 — RSK-011 reforçado.

**INC-005 — Exigências estaduais e municipais.** Não levantadas. Podem impor requisitos adicionais ao piloto (OQ-013).

**INC-006 — Governança documental.** Fonte autoritativa nesta fase: Microsoft 365. `Overview_Project.md` marcado como não autoritativo (CON-010).

**INC-007 — Personas não validadas.** DOC-005 permanece integralmente hipótese (ASM-009, OQ-009).

**INC-008 — Separação de autoridades (novo).** Jurídico e DPO são autoridades distintas. Nenhuma das duas está nominalmente identificada (GAP-005, GAP-006).

---

## 10. Informações que precisam ser obtidas com o cliente

1. Processo operacional real: do fechamento do contrato à entrega do relatório ao cliente da prestadora.
2. Volumetria: clientes da prestadora, unidades, ambientes, sistemas HVAC, equipamentos, OS/mês, técnicos.
3. Estrutura atual de dados e qualidade do inventário.
4. Papéis reais, permissões praticadas e regras de segregação interna.
5. Modelo de planos de manutenção em uso, periodicidades praticadas e **origem** dessas periodicidades.
6. Checklists e formulários utilizados em campo, e **quais são obrigatórios por tipo de OS**.
7. Medições coletadas, instrumentos, unidades e critérios de aceitação praticados.
8. Tratamento atual de não conformidades e ações corretivas.
9. Formato, conteúdo e destinatários dos relatórios e do PMOC entregues hoje.
10. Condições reais de campo: conectividade, dispositivos, restrições de acesso e de segurança do trabalho.
11. Exigências contratuais e de fiscalização já enfrentadas, **incluindo o nível probatório exigido de cada documento**.
12. Expectativas explícitas quanto ao MVP e critérios do cliente para considerá-lo bem-sucedido.

---

## 11. Itens que não puderam ser determinados nesta fase

- Nome comercial do produto.
- Datas, esforço, custo e composição de equipe.
- Metas numéricas das métricas de sucesso.
- Extensão da aplicabilidade da ABNT NBR 17037 e edição aplicável.
- Status jurídico formal da Portaria GM/MS nº 3.523/1998 e a redação exata do limite de capacidade.
- Critérios definitivos da Regra A e da Regra B.
- Referência bibliográfica oficial exata da orientação da ANVISA de 2025.
- Bases legais da LGPD por categoria de dado.
- Nível exigido de identificação e manifestação de vontade.
- Mecanismo de preservação do estado de referência do PMOC emitido.
- Modelo de isolamento multi-tenant e demais escolhas tecnológicas.
- Nível exigido de acessibilidade.
- Modelo comercial e de contrato do piloto.

---

## 12. Recomendação por artefato

| Artefato | Recomendação | Condição |
| --- | --- | --- |
| DOC-001 | **Aprovar com ressalvas** | §5.1, §5.2 e §5.3 permanecem sob revisão até parecer jurídico; preencher patrocinador e Product Owner |
| DOC-002 | **Aprovar** | PP-13 depende de detalhamento nas Fases 3 e 6 |
| DOC-003 | **Aprovar** | Reavaliar itens "A validar" após a Fase 2 |
| DOC-004 | **Aprovar com ressalvas** | Fechar GAP-001 a GAP-006 |
| DOC-005 | **Revisar** | Validar com o piloto antes de usar em decisões de UX |
| DOC-006 | **Aprovar** | Consolidação corrigida; reclassificação apenas por gestão de mudança |
| DOC-007 | **Aprovar com ressalvas** | Reconfirmar após o levantamento da Fase 2; AC-MVP-11 depende de registro formal de validação |
| DOC-008 | **Aprovar com ressalvas** | Incluir datas somente após OQ-007 |
| XLS-001 | **Aprovar** | Manutenção contínua |
| XLS-002 | **Aprovar** | Reavaliar a cada fase |
| XLS-003 | **Aprovar** | Atribuir prazos aos responsáveis |
| XLS-004 | **Aprovar as decisões como propostas** | Conversão de status exige instrução explícita |
| XLS-005 | **Aprovar a estrutura** | Preenchimento a partir da Fase 2 |
| DIA-001 | **Aprovar** | Atualizar quando o escopo do MVP for reconfirmado |
| CHANGE-REPORT | **Aprovar** | — |
| Overview_Project.md — PATCH | **Aplicar e devolver** | Arquivo-fonte não disponível neste ambiente (RES-03) |

---

## 13. Critérios de aceite da Fase 1

| ID | Critério | Situação |
| --- | --- | --- |
| AC-F1-01 | Todos os artefatos exigidos pelo Master Specification §26 foram produzidos | Atendido |
| AC-F1-02 | O Product Charter contém os 32 itens obrigatórios do §27 | Atendido |
| AC-F1-03 | Toda capacidade possui exatamente uma classificação de Scope Boundary | Atendido |
| AC-F1-04 | Nenhum requisito, norma ou regra foi inventado | Atendido |
| AC-F1-05 | Toda incerteza está registrada como hipótese ou questão aberta | Atendido |
| AC-F1-06 | Fontes regulatórias registradas com órgão, natureza, data de consulta e situação | Atendido, com OQ-019 pendente quanto à referência bibliográfica exata |
| AC-F1-07 | Decisões, riscos, dependências e pendências registrados antes do avanço | Atendido |
| AC-F1-08 | Contagens coerentes entre documentos e planilhas | Atendido nesta versão (corrigido) |
| AC-F1-09 | Nenhum ID duplicado ou reaproveitado para conceito diferente | Atendido |
| AC-F1-10 | Terminologia padronizada aplicada | Atendido (DOC-003 §11) |
| AC-F1-11 | Aprovação formal da Services.NET | **Pendente — segunda revisão** |

---

## 14. Condições para aprovação final da Fase 1

1. Segunda revisão formal deste pacote v0.2 pela Services.NET.
2. Patrocinador, Product Owner, autoridade jurídica e DPO designados.
3. Cliente-piloto confirmado e agenda de levantamento definida.
4. Solicitações de parecer jurídico, do DPO e de responsável técnico formalmente abertas.
5. ABNT NBR 17037 adquirida legitimamente.
6. Referência oficial exata da orientação da ANVISA registrada (OQ-019).
7. Questões abertas bloqueantes (OQ-002, OQ-003, OQ-010) respondidas.
8. Patch de `Overview_Project.md` aplicado e devolvido para conferência.
9. Decisão explícita da Services.NET sobre converter ou não DEC-001 a DEC-010 para `Aprovada`.

---

## 15. Nota de responsabilidade

Este pacote é material de engenharia de software. Ele **não** constitui parecer jurídico, **não** determina vigência normativa, **não** atribui status jurídico a norma técnica, **não** substitui responsável técnico habilitado e **não** certifica conformidade regulatória. Os pontos que exigem validação jurídica, do DPO/Encarregado ou de responsável técnico estão sinalizados individualmente nos artefatos e consolidados nas seções 5, 7 e 9 deste documento.

---

**A Fase 2 não foi iniciada e permanece aguardando nova revisão formal da Services.NET.**
