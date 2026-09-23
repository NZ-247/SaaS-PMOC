# PHASE-01-REVIEW.md

**Projeto:** PMOC Software — Plataforma de Gestão de Manutenção, Ativos e Conformidade para Sistemas de Climatização
**Organização:** Services.NET
**Fase:** 1 — Product Charter e Escopo
**Versão:** **v0.2 — APPROVED** · Versão anterior: 0.1 DRAFT (baseline histórica, preservada)
**Data:** 22/09/2026
**Origem das alterações:** **Services.NET Phase 1 Audit — Approved**; finalização local por Codex; segunda revisão formal da Fase 1 v0.2 pela Services.NET
**Autor:** Opus — análise, arquitetura, documentação, modelagem, revisão e planejamento
**Status:** **Fase 1 APPROVED pela Services.NET em 22/09/2026. Status adicional: APPROVED WITH OPEN ACTIONS. A Fase 2 não foi iniciada.**

> Este documento substitui integralmente a versão v0.1. Afirmações desatualizadas da v0.1 não foram reaproveitadas. O detalhamento das alterações está em `PHASE-01-V0.2-CHANGE-REPORT.md`.

---

## 1. Resumo

A Fase 1 entrega a visão formal do produto antes de qualquer levantamento detalhado de requisitos ou implementação: 8 documentos narrativos (DOC-001 a DOC-008), 5 planilhas de governança (XLS-001 a XLS-005), 1 diagrama de contexto conceitual (DIA-001), este documento de revisão e o relatório de mudanças da v0.2.

O produto é concebido, conforme o Master Specification §5, como **plataforma de gestão de manutenção, ativos, operações de campo, conformidade, evidências e inteligência operacional**, tendo o PMOC como **primeiro domínio regulatório atendido** — não como sistema de preenchimento de PMOC.

Números verificados nesta versão: **79 capacidades** catalogadas (50 MVP, 19 Pós-MVP, 5 Futuro, 5 A validar), **12 hipóteses**, **12 restrições**, **10 dependências**, **22 questões registradas** (**18 abertas** e **4 respondidas/encerradas**), **19 riscos**, **11 decisões registradas** (**10 propostas** e **1 aprovada**), **8 ADRs indexados e nenhum decidido**, **11 critérios de aceite do MVP** e **13 linhas semente na RTM**.

Nenhum código foi produzido. Nenhuma tecnologia foi considerada definitiva. Nenhum ADR foi decidido. Nenhum parâmetro regulatório foi carregado. Nenhum requisito, norma, obrigação legal, periodicidade, perfil profissional obrigatório, norma técnica ou fluxo operacional do cliente foi inventado.

A aprovação formal da Fase 1 v0.2 aprova o pacote documental como base para avanço futuro. Ela **não** significa validação jurídica final, aprovação de ADRs, escolha definitiva da stack, encerramento de todas as OQs ou aprovação automática de todas as DEC.

---

## 2. Artefatos entregues

| ID | Artefato | Formato | Versão | Recomendação |
| --- | --- | --- | --- | --- |
| DOC-001 | PMOC Software — Product Charter | Word | v0.2 — APPROVED | Aprovado com ações abertas |
| DOC-002 | Product Vision and Product Principles | Word | v0.2 — APPROVED | Aprovado |
| DOC-003 | Project Scope | Word | v0.2 — APPROVED | Aprovado |
| DOC-004 | Stakeholder Map | Word | v0.2 — APPROVED | Aprovado com ações abertas |
| DOC-005 | Personas — versão inicial | Word | v0.2 — APPROVED | Aprovado como hipótese a validar |
| DOC-006 | Product Capabilities Map | Word | v0.2 — APPROVED | Aprovado |
| DOC-007 | MVP Definition | Word | v0.2 — APPROVED | Aprovado com ações abertas |
| DOC-008 | Product Roadmap — visão macro | Word | v0.2 — APPROVED | Aprovado com ações abertas |
| XLS-001 | Assumptions, Constraints and Dependencies Register | Excel | v0.2 — APPROVED | Aprovado |
| XLS-002 | Risk Register | Excel | v0.2 — APPROVED | Aprovado |
| XLS-003 | Open Questions Register | Excel | v0.2 — APPROVED | Aprovado |
| XLS-004 | Decision Log + ADR Register + Change Control | Excel | v0.2 — APPROVED | Aprovado com DEC-011 aprovada |
| XLS-005 | Requirements Traceability Matrix — estrutura inicial | Excel | v0.2 — APPROVED | Aprovado como estrutura |
| DIA-001 | System/Product Context Diagram — nível conceitual | PNG | v0.2 — APPROVED | Aprovado |
| — | PHASE-01-V0.2-CHANGE-REPORT.md | Markdown | v0.2 — APPROVED | Aprovado |
| — | Overview_Project.md | Markdown | 0.2 | Manter como referência não autoritativa |

Governança documental aprovada em **DEC-011**: Microsoft 365 é o ambiente de autoria, colaboração, apresentação, visualização executiva, Word, Excel, Power BI e interação com agentes integrados ao ambiente corporativo. Git é a baseline técnica autoritativa e versionada dos artefatos de engenharia formalmente publicados/aprovados. Em caso de divergência entre uma cópia M365 e uma versão formalmente publicada/aprovada no Git, prevalece a baseline aprovada no Git. `Overview_Project.md` é **REFERENCE / NON-AUTHORITATIVE**.

---

## 3. O que foi solucionado nesta revisão

| # | Achado da auditoria | Situação |
| --- | --- | --- |
| 1 | Cadeia normativa quebrada após a revogação da RE nº 9/2003 | **Resolvido quanto à identificação e rastreabilidade da fonte.** Guia nº 73/2024, versão 2, da ANVISA registrado; OQ-019 encerrada. Extensão da aplicabilidade da ABNT NBR 17037 permanece pendente (OQ-004) |
| 2 | Tratamento do limite de 5 TR / 60.000 BTU/h como divergência única | **Resolvido no contexto federal documentado.** Regra A e Regra B separadas em DOC-001 §5.3; o limite fundamenta a Regra B pelo Art. 6º da Portaria. OQ-021 foi reformulada para exigências estaduais, municipais, setoriais, contratuais ou de uso restrito |
| 3 | Redação da OQ-012 sugeria ausência de evidência de aplicação da Portaria | **Resolvido quanto ao artigo e à redação.** Art. 6º e alínea a registrados; OQ-012 mantém apenas confirmação jurídica formal sobre eventual alteração, revogação, consolidação ou extensão atual |
| 4 | Tensão entre CAP-033 no MVP e o critério que veda dependência jurídica pendente | **Resolvido.** Capacidade estrutural no MVP; conteúdo regulatório excluído (OOS-015) e condicionado (AC-MVP-11) |
| 5 | `TenantId` prescrito como coluna física | **Resolvido.** Regra semântica e de segurança mantida; implementação física remetida ao ADR-001 |
| 6 | Assinatura em três estados contraditórios | **Resolvido.** Estado único "A validar", sem nível presumido |
| 7 | OQ-006 formulada de modo binário | **Resolvido.** Reformulada para nível de identificação, manifestação de vontade, autoria, integridade e não repúdio por ato/documento |
| 8 | AC-MVP-03 exigia checklist para toda OS | **Resolvido.** Requisitos obrigatórios por tipo de OS e template |
| 9 | AC-MVP-08 excessivamente literal | **Resolvido.** Contrato para operação de negócio ou server-side; sem endpoint artificial |
| 10 | Jurídico e DPO tratados como autoridade única | **Resolvido.** STK-007 e STK-021 separados; RACI desdobrado; responsáveis atualizados em registros |
| 11 | ADR-008 sem posição clara no roadmap | **Resolvido.** Pré-requisito das partes dependentes do modelo de Compliance as Data |
| 12 | `Overview_Project.md` competindo com artefatos aprovados | **Resolvido localmente.** Patch aplicado ao arquivo-fonte; duplicidade de `AGENTS.md` removida |
| 13 | Erro de consolidação na Summary de XLS-001 | **Resolvido.** Fórmulas corrigidas; verificação estendida às demais planilhas |
| 14 | Estado de referência do PMOC emitido não explicitado | **Resolvido como princípio.** PP-13, CAP-037, AC-MVP-02, OQ-020, RSK-019. Modelagem permanece para as Fases 3 e 6 |
| 15 | DIA-001 com sobreposições de rótulo | **Resolvido.** Ajustes de legibilidade; fronteiras conceituais preservadas |
| — | **Erro de consolidação de capacidades não apontado pela auditoria** | **Encontrado e corrigido na validação cruzada:** a v0.1 declarava 77/43; a contagem real do catálogo é **79/50** |

---

## 4. Decisões registradas (XLS-004)

A aprovação da Fase 1 **não** converteu automaticamente todas as decisões em aprovadas. **DEC-001 a DEC-010 permanecem no estado `Proposta`**. Somente **DEC-011** foi explicitamente aprovada pela Services.NET nesta formalização final.

| ID | Situação |
| --- | --- |
| DEC-001 | **Proposta:** plataforma de manutenção/ativos/campo/conformidade; PMOC como primeiro domínio regulatório |
| DEC-002 | **Proposta:** nome comercial não definido nesta fase |
| DEC-003 | **Proposta:** Modular Monolith + API First como hipótese, a confirmar por ADR |
| DEC-004 | **Proposta:** multi-tenancy como regra semântica e de segurança; modelo físico em ADR-001 |
| DEC-005 | **Proposta:** Compliance as Data, distinguindo capacidade estrutural de conteúdo regulatório |
| DEC-006 | **Proposta:** MVP Web First; mobile e offline Pós-MVP |
| DEC-007 | **Proposta:** auditoria de negócio na primeira versão, separada de log técnico |
| DEC-008 | **Proposta:** roadmap por ondas de valor, sem datas |
| DEC-009 | **Proposta:** normas técnicas referenciadas, nunca reproduzidas; norma técnica não recebe status de lei |
| DEC-010 | **Proposta:** nenhum código antes da aprovação documental e dos ADRs estruturantes |
| DEC-011 | **Aprovada:** Microsoft 365 como ambiente de autoria/colaboração/apresentação/visualização executiva; Git como baseline técnica autoritativa e versionada dos artefatos de engenharia formalmente publicados/aprovados |

---

## 5. Decisões ainda necessárias

**Ações abertas após aprovação da Fase 1:**
1. Identificação da autoridade jurídica (GAP-005), do DPO/Encarregado (GAP-006) e do responsável técnico operacional (GAP-004).
2. Definição de equipe, orçamento e prazo (OQ-007).
3. Confirmação do modelo de operação e SLA (OQ-011).
4. Formalização de interlocutores, disponibilidade, compromisso operacional e agenda com a Clima Zero Climatização (OQ-022 / DEP-004).
5. Solicitações formais de parecer jurídico, do DPO e de responsável técnico.

**Antes de iniciar a implementação (W1):**
1. ADR-001 — isolamento multi-tenant.
2. ADR-002 — estratégia de identificadores.
3. ADR-003 e ADR-004 — stacks de back-end e front-end.
4. ADR-005 — armazenamento de evidências.
5. ADR-006 — modelo de auditoria de negócio.
6. **ADR-008 — modelo de dados de Compliance as Data** (pré-requisito de CAP-030 a CAP-035, CAP-037 e CAP-038).
7. Mecanismo de preservação do estado de referência do PMOC (OQ-020), nas Fases 3 e 6.

**Dependentes de terceiros:**
1. Parecer jurídico sobre a extensão da aplicabilidade da ABNT NBR 17037, sobre a Portaria GM/MS nº 3.523/1998, sobre exigências locais/setoriais/contratuais da Regra A / Regra B e sobre o nível probatório exigido (DEP-001).
2. Parecer do DPO sobre bases legais, retenção e direitos dos titulares (DEP-010).
3. Parecer de responsável técnico sobre periodicidades e parâmetros (DEP-002).
4. Aquisição legítima da ABNT NBR 17037 e demais normas aplicáveis (DEP-003).

---

## 6. Hipóteses (12 — XLS-001)

Nenhuma hipótese é requisito confirmado. As de maior impacto:

| ID | Hipótese | Impacto se falsa |
| --- | --- | --- |
| ASM-001 | Clima Zero Climatização é o tenant-piloto; disponibilidade, interlocutores e agenda ainda serão formalizados | Fase 2 produziria requisitos presumidos se a disponibilidade operacional não for confirmada |
| ASM-004 | Há conectividade suficiente para uso Web no campo | PWA/offline precisaria ser antecipado para o MVP |
| ASM-008 | A prestadora possui responsável técnico habilitado | Modelo de responsabilidade do produto muda |
| ASM-010 | Equipamento é a menor unidade de inventário necessária ao MVP | Modelo de domínio e checklists mudam |
| ASM-011 | Periodicidades virão de responsável técnico habilitado | Engenharia ficaria sem fonte legítima de regra |
| **ASM-012** | **Reformulada na v0.2:** a plataforma precisará registrar alguma manifestação de vontade; **o nível exigido não é assumido** | Valor probatório, UX da OS e arquitetura mudam |

---

## 7. Questões registradas (22 — XLS-003)

**18 abertas, 4 respondidas/encerradas (OQ-002, OQ-003, OQ-010 e OQ-019) e 11 abertas de prioridade alta.** Ações abertas principais:

- **OQ-004** — extensão da aplicabilidade da ABNT NBR 17037 (reformulada).
- **OQ-005** — metas quantitativas.
- **OQ-006** — nível probatório/assinaturas e manifestação de vontade.
- **OQ-007** — equipe, orçamento e prazo.
- **OQ-009** — validação das personas com o tenant-piloto.
- **OQ-011** — modelo operacional/SLA.
- **OQ-012** — confirmação formal quanto à Portaria GM/MS nº 3.523/1998 (reformulada).
- **OQ-021** — exigências estaduais, municipais, setoriais, contratuais ou situações de uso restrito que possam afetar Regra A / Regra B.
- **OQ-020** — mecanismo de preservação do estado de referência do PMOC (**nova**).
- **OQ-015** — bases legais da LGPD, agora sob o DPO (responsável corrigido).
- **OQ-018** — granularidade mínima de ativo exigida pelo piloto.
- **OQ-022** — interlocutores específicos, disponibilidade, compromisso operacional e agenda da Clima Zero Climatização.

---

## 8. Riscos (19 — XLS-002)

| ID | Risco | Score |
| --- | --- | --- |
| RSK-003 | Scope creep no MVP | 16 |
| RSK-004 | Interlocutores, disponibilidade e agenda do tenant-piloto ainda não formalizados | 15 |
| RSK-006 | Definição tardia do modelo de multi-tenancy | 15 |
| RSK-017 | Backup existente com restore nunca testado | 15 |
| **RSK-019** | **PMOC emitido perder fidelidade ao estado que o originou (novo)** | **16** |
| RSK-001 | Extensão da aplicabilidade da referência técnica de qualidade do ar (**reduzido de 20 para 12**) | 12 |
| RSK-002 | Vazamento de dados entre tenants | 10 (impacto máximo) |

Score médio: 11,7. Riscos com score ≥ 15: 5.

---

## 9. Pontos de atenção regulatórios — estado atual

**INC-001 — Referência técnica de qualidade do ar (atualizado).** A Lei nº 13.589/2018 remete os parâmetros de qualidade do ar à RE/ANVISA nº 9/2003 "e posteriores alterações". O **Guia nº 73/2024, versão 2, de 03/04/2025**, da ANVISA (Biblioteca Digital da Anvisa, item 17752; vigente a partir de 04/04/2025), registra que a RE nº 9/2003 foi revogada pela RDC nº 886/2024 e que, após essa revogação, a **ABNT NBR 17037**, em sua versão mais atual, passou a ser referência para qualidade do ar interior.

Tratamento adotado: a ABNT NBR 17037 é registrada como **norma técnica**, **não** como instrumento de status jurídico equivalente a lei, portaria ou resolução. O próprio Guia da ANVISA é instrumento regulatório **não normativo**, recomendatório e não vinculante. A norma exige aquisição legítima (DEP-003), não é reproduzida, e a extensão de sua aplicabilidade ao produto depende de validação jurídica e de responsável técnico (OQ-004). **Nenhum parâmetro, faixa, limite ou periodicidade foi carregado.**

**OQ-019 foi respondida e encerrada** nesta revisão local.

**INC-002 — Portaria GM/MS nº 3.523/1998 (atualizado).** A Portaria permanece disponível em fonte oficial do Ministério da Saúde. O Art. 6º estabelece a exigência de responsável técnico habilitado para sistemas de climatização com capacidade acima de 5 TR (15.000 kcal/h = 60.000 BTU/h), e a alínea a atribui a implantação e manutenção disponível no imóvel do PMOC. Esta revisão **não declara** sua vigência jurídica formal. OQ-012 foi reformulada para pedir somente a confirmação jurídica de eventual alteração, revogação, consolidação ou extensão atual.

**INC-003 — Regra A × Regra B (reescrito).** O tema deixou de ser tratado como divergência sobre limiar de capacidade. São regras distintas: **Regra A** determina a aplicabilidade do PMOC (Lei nº 13.589/2018); **Regra B** determina a exigência de responsável técnico (Portaria GM/MS nº 3.523/1998, Art. 6º). No contexto federal documentado, o limite de 5 TR / 60.000 BTU/h fundamenta a Regra B e **não** é usado automaticamente como condição geral da Regra A. OQ-021 fica restrita a normas estaduais, municipais, regulamentações setoriais específicas, exigências contratuais e situações de uso restrito.

**INC-004 — Normas técnicas ABNT.** Protegidas por direito autoral: referenciadas, nunca reproduzidas. Aquisição legítima pendente (DEP-003). A relevância aumentou com a incorporação da NBR 17037 — RSK-011 reforçado.

**INC-005 — Exigências estaduais e municipais.** Não levantadas. Podem impor requisitos adicionais ao piloto (OQ-013).

**INC-006 — Governança documental.** **DEC-011 aprovada.** Microsoft 365 será o ambiente de autoria, colaboração, apresentação, visualização executiva, Word, Excel, Power BI e interação com agentes integrados ao ambiente corporativo. Git será a baseline técnica autoritativa e versionada dos artefatos de engenharia formalmente publicados/aprovados. Fluxos operacionais: M365 → autoria/alteração → revisão → publicação → Git; ou Git → alteração técnica → revisão/aprovação → baseline → sincronização da representação M365 quando aplicável. Em caso de divergência entre cópia M365 e baseline aprovada no Git, prevalece a baseline aprovada no Git. `Overview_Project.md` permanece não autoritativo (CON-010).

**INC-007 — Personas não validadas.** DOC-005 permanece integralmente hipótese (ASM-009, OQ-009).

**INC-008 — Separação de autoridades (novo).** Patrocinador e Product Owner institucional foram definidos. Jurídico e DPO continuam autoridades distintas e ainda não nominalmente identificadas (GAP-005, GAP-006).

---

## 10. Informações que precisam ser obtidas com o tenant-piloto

Tenant-piloto definido: **Clima Zero Climatização**.

1. Interlocutores específicos, disponibilidade, compromisso operacional e agenda da Fase 2.
2. Processo operacional real: do fechamento do contrato à entrega do relatório ao cliente da prestadora.
3. Volumetria: clientes da prestadora, unidades, ambientes, sistemas HVAC, equipamentos, OS/mês, técnicos.
4. Estrutura atual de dados e qualidade do inventário.
5. Papéis reais, permissões praticadas e regras de segregação interna.
6. Modelo de planos de manutenção em uso, periodicidades praticadas e **origem** dessas periodicidades.
7. Checklists e formulários utilizados em campo, e **quais são obrigatórios por tipo de OS**.
8. Medições coletadas, instrumentos, unidades e critérios de aceitação praticados.
9. Tratamento atual de não conformidades e ações corretivas.
10. Formato, conteúdo e destinatários dos relatórios e do PMOC entregues hoje.
11. Condições reais de campo: conectividade, dispositivos, restrições de acesso e de segurança do trabalho.
12. Exigências contratuais e de fiscalização já enfrentadas, **incluindo o nível probatório exigido de cada documento**.
13. Expectativas explícitas quanto ao MVP e critérios do cliente para considerá-lo bem-sucedido.

---

## 11. Itens que não puderam ser determinados nesta fase

- Nome comercial do produto.
- Datas, esforço, custo e composição de equipe.
- Metas numéricas das métricas de sucesso.
- Extensão da aplicabilidade da ABNT NBR 17037, parâmetros exigíveis e edição aplicável.
- Confirmação jurídica formal de eventual alteração, revogação, consolidação ou extensão atual da Portaria GM/MS nº 3.523/1998.
- Exigências estaduais, municipais, setoriais, contratuais ou de uso restrito que possam afetar Regra A / Regra B.
- Bases legais da LGPD por categoria de dado.
- Nível exigido de identificação e manifestação de vontade.
- Mecanismo de preservação do estado de referência do PMOC emitido.
- Modelo de isolamento multi-tenant e demais escolhas tecnológicas.
- Nível exigido de acessibilidade.
- Modelo comercial e de contrato do piloto.
- Interlocutores específicos, disponibilidade, compromisso operacional e agenda da Clima Zero Climatização.

---

## 12. Recomendação por artefato

| Artefato | Recomendação | Condição |
| --- | --- | --- |
| DOC-001 | **Aprovado com ações abertas** | §5.1, §5.2 e §5.3 permanecem sob revisão até parecer jurídico |
| DOC-002 | **Aprovado** | PP-13 depende de detalhamento nas Fases 3 e 6 |
| DOC-003 | **Aprovado** | Reavaliar itens "A validar" após a Fase 2 |
| DOC-004 | **Aprovado com ações abertas** | GAP-001 a GAP-003 encerrados; GAP-004 a GAP-006 permanecem |
| DOC-005 | **Aprovado como hipótese a validar** | Validar com o tenant-piloto antes de usar em decisões de UX |
| DOC-006 | **Aprovado** | Consolidação corrigida; reclassificação apenas por gestão de mudança |
| DOC-007 | **Aprovado com ações abertas** | Reconfirmar após o levantamento da Fase 2; AC-MVP-11 depende de registro formal de validação |
| DOC-008 | **Aprovado com ações abertas** | Incluir datas somente após OQ-007 |
| XLS-001 | **Aprovado** | Manutenção contínua |
| XLS-002 | **Aprovado** | Reavaliar a cada fase |
| XLS-003 | **Aprovado** | Atribuir prazos aos responsáveis |
| XLS-004 | **Aprovado com DEC-011 aprovada** | DEC-001 a DEC-010 permanecem Proposta; conversões futuras exigem instrução explícita |
| XLS-005 | **Aprovado como estrutura** | Preenchimento a partir da Fase 2 |
| DIA-001 | **Aprovado** | Atualizar quando o escopo do MVP for reconfirmado |
| CHANGE-REPORT | **Aprovado** | Formalização final registrada |
| Overview_Project.md | **Manter como referência não autoritativa** | Patch aplicado; não usar como fonte de requisito, arquitetura, escopo ou conformidade |

---

## 13. Critérios de aceite da Fase 1

| ID | Critério | Situação |
| --- | --- | --- |
| AC-F1-01 | Todos os artefatos exigidos pelo Master Specification §26 foram produzidos | Atendido |
| AC-F1-02 | O Product Charter contém os 32 itens obrigatórios do §27 | Atendido |
| AC-F1-03 | Toda capacidade possui exatamente uma classificação de Scope Boundary | Atendido |
| AC-F1-04 | Nenhum requisito, norma ou regra foi inventado | Atendido |
| AC-F1-05 | Toda incerteza está registrada como hipótese ou questão aberta | Atendido |
| AC-F1-06 | Fontes regulatórias registradas com órgão, natureza, data de consulta e situação | Atendido; OQ-004 permanece para extensão da aplicabilidade da NBR 17037 |
| AC-F1-07 | Decisões, riscos, dependências e pendências registrados antes do avanço | Atendido |
| AC-F1-08 | Contagens coerentes entre documentos e planilhas | Atendido nesta versão (corrigido) |
| AC-F1-09 | Nenhum ID duplicado ou reaproveitado para conceito diferente | Atendido |
| AC-F1-10 | Terminologia padronizada aplicada | Atendido (DOC-003 §11) |
| AC-F1-11 | Aprovação formal da Services.NET | **Atendido** — Sponsor definido; Product Owner institucional definido; tenant-piloto definido; DEC-011 aprovada; segunda revisão formal concluída |

---

## 14. Open Actions carried into Phase 2

A Fase 1 está aprovada, mas as ações abaixo permanecem abertas e devem ser carregadas para a etapa seguinte quando a Services.NET autorizar seu início:

1. OQ-004 — extensão da aplicabilidade da NBR 17037.
2. OQ-005 — metas quantitativas.
3. OQ-006 — nível probatório/assinaturas.
4. OQ-007 — equipe, orçamento e prazo.
5. OQ-009 — validação das personas.
6. OQ-011 — modelo operacional/SLA.
7. OQ-012 — confirmação jurídica formal da Portaria GM/MS nº 3.523/1998.
8. OQ-015 — bases legais da LGPD, retenção e direitos dos titulares.
9. OQ-020 — mecanismo de preservação do estado de referência do PMOC emitido.
10. OQ-021 — normas locais, setoriais, contratuais ou situações de uso restrito que afetem Regra A / Regra B.
11. OQ-022 — interlocutores específicos, disponibilidade, compromisso operacional e agenda da Clima Zero Climatização.

---

## 15. Nota de responsabilidade

Este pacote é material de engenharia de software. Ele **não** constitui parecer jurídico, **não** determina vigência normativa, **não** atribui status jurídico a norma técnica, **não** substitui responsável técnico habilitado e **não** certifica conformidade regulatória. Os pontos que exigem validação jurídica, do DPO/Encarregado ou de responsável técnico estão sinalizados individualmente nos artefatos e consolidados nas seções 5, 7 e 9 deste documento.

---

**A Fase 1 v0.2 está APPROVED WITH OPEN ACTIONS. A Fase 2 não foi iniciada nesta execução.**
