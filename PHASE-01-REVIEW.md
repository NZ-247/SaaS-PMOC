# PHASE-01-REVIEW.md

**Projeto:** PMOC Software — Plataforma de Gestão de Manutenção, Ativos e Conformidade para Sistemas de Climatização
**Organização:** Services.NET
**Fase:** 1 — Product Charter e Escopo
**Versão:** 0.1 (DRAFT) · **Data:** 22/09/2026
**Autor:** Opus — análise, arquitetura, documentação, modelagem, revisão e planejamento
**Status:** Aguardando revisão formal da Services.NET. **A Fase 2 não foi iniciada.**

---

## 1. Resumo

A Fase 1 produziu a visão formal do produto antes de qualquer levantamento detalhado de requisitos ou implementação. Foram entregues 8 documentos narrativos (DOC-001 a DOC-008), 5 planilhas de governança (XLS-001 a XLS-005), 1 diagrama de contexto conceitual (DIA-001) e este documento de revisão.

O produto foi conceituado, conforme o Master Specification §5, como **plataforma de gestão de manutenção, ativos, operações de campo, conformidade, evidências e inteligência operacional**, tendo o PMOC como **primeiro domínio regulatório atendido** — e não como um sistema de preenchimento de PMOC.

Foram catalogadas **77 capacidades de negócio** (CAP-001 a CAP-106), classificadas segundo o Scope Boundary: 43 MVP, 21 Pós-MVP, 7 Futuro e 6 "A validar". O MVP foi definido pelo critério do *Golden Path*: o ciclo completo e raso de cliente → ativo → plano → cronograma → ordem de serviço → execução → evidência → PMOC/relatório, com auditoria nativa.

Nenhum código foi produzido. Nenhuma tecnologia foi considerada definitiva. Nenhum ADR foi decidido.

Nenhum requisito, norma, obrigação legal, periodicidade, perfil profissional obrigatório, norma técnica ou fluxo operacional do cliente foi inventado. Tudo que não pôde ser confirmado está registrado como **hipótese (ASM)** ou **questão aberta (OQ)**.

---

## 2. Artefatos entregues

| ID | Artefato | Formato | Status proposto |
| --- | --- | --- | --- |
| DOC-001 | PMOC Software — Product Charter | Word | Aprovar com ressalvas |
| DOC-002 | Product Vision and Product Principles | Word | Aprovar |
| DOC-003 | Project Scope | Word | Aprovar |
| DOC-004 | Stakeholder Map | Word | Aprovar com ressalvas |
| DOC-005 | Personas — versão inicial | Word | Revisar (hipótese não validada) |
| DOC-006 | Product Capabilities Map | Word | Aprovar |
| DOC-007 | MVP Definition | Word | Aprovar com ressalvas |
| DOC-008 | Product Roadmap — visão macro | Word | Aprovar com ressalvas |
| XLS-001 | Assumptions, Constraints and Dependencies Register | Excel | Aprovar |
| XLS-002 | Risk Register inicial | Excel | Aprovar |
| XLS-003 | Open Questions Register | Excel | Aprovar |
| XLS-004 | Decision Log (+ ADR Register) | Excel | Aprovar como propostas |
| XLS-005 | Requirements Traceability Matrix — estrutura inicial | Excel | Aprovar |
| DIA-001 | System/Product Context Diagram — nível conceitual | PNG | Aprovar |

Fonte autoritativa nesta fase: Microsoft 365. A representação em Markdown no repositório Git (`/docs`, `README.md`, `AGENTS.md`, `CLAUDE.md`) será criada na Fase 10, evitando duplicidade de fonte antes da aprovação.

---

## 3. Decisões propostas (aguardando aprovação — XLS-004)

| ID | Decisão proposta |
| --- | --- |
| DEC-001 | Produto concebido como plataforma de manutenção/ativos/campo/conformidade; PMOC como primeiro domínio regulatório |
| DEC-002 | Nome comercial **não** definido nesta fase |
| DEC-003 | Modular Monolith + API First como **hipótese** inicial, a confirmar por ADR |
| DEC-004 | Multi-tenancy obrigatória desde a concepção; modelo de isolamento em ADR-001 |
| DEC-005 | Compliance as Data: regra, periodicidade e parâmetro como dado versionado |
| DEC-006 | MVP Web First; mobile e offline Pós-MVP, com contratos preparados |
| DEC-007 | Auditoria de negócio na primeira versão, separada de log técnico |
| DEC-008 | Roadmap por ondas de valor, sem datas |
| DEC-009 | Normas técnicas protegidas referenciadas, nunca reproduzidas |
| DEC-010 | Nenhum código antes da aprovação documental e dos ADRs estruturantes |

---

## 4. Decisões ainda necessárias

**Antes do encerramento da Fase 1:**
1. Nomeação do patrocinador (OQ-002) e do Product Owner (OQ-003).
2. Confirmação formal do cliente-piloto (OQ-010).
3. Definição de equipe, orçamento e prazo (OQ-007).
4. Confirmação do modelo de operação e SLA (OQ-011).

**Antes do início da implementação (W1):**
5. ADR-001 — modelo de isolamento multi-tenant.
6. ADR-002 — estratégia de identificadores (UUIDv7 ou equivalente).
7. ADR-003/004 — stacks de back-end e front-end.
8. ADR-005 — armazenamento de evidências.
9. ADR-006 — modelo de auditoria de negócio.
10. ADR-008 — modelo de dados de Compliance as Data.

**Dependentes de terceiros:**
11. Parecer jurídico sobre referencial regulatório vigente e bases legais da LGPD.
12. Parecer de responsável técnico sobre periodicidades e parâmetros.

---

## 5. Hipóteses (não são requisitos confirmados — XLS-001)

Doze hipóteses registradas. As de maior impacto:

| ID | Hipótese | Impacto se falsa |
| --- | --- | --- |
| ASM-001 | Existe cliente-piloto disponível para validar requisitos | Fase 2 produziria requisitos presumidos |
| ASM-004 | Há conectividade suficiente para uso Web no campo | PWA/offline precisaria ser antecipado para o MVP |
| ASM-008 | A prestadora possui responsável técnico habilitado | Modelo de responsabilidade do produto muda |
| ASM-010 | Equipamento é a menor unidade de inventário necessária ao MVP | Modelo de domínio e checklists mudam |
| ASM-011 | Periodicidades virão de responsável técnico habilitado | A engenharia ficaria sem fonte legítima de regra |
| ASM-012 | Assinatura simples em tela basta para o MVP | Arquitetura de assinatura e valor probatório mudam |

---

## 6. Questões abertas (XLS-003)

Dezoito questões registradas, sendo **onze de prioridade alta**. Bloqueantes para o avanço:

- **OQ-002 / OQ-003** — patrocinador e Product Owner não designados: não há autoridade formal para aprovar a Fase 1.
- **OQ-010** — cliente-piloto não confirmado: sem fonte primária, a Fase 2 não pode iniciar.
- **OQ-004 / OQ-012** — referencial regulatório vigente indefinido (ver §8).
- **OQ-015** — bases legais da LGPD por categoria de dado: **não será concluído pela engenharia**.
- **OQ-006** — exigência ou não de assinatura com validade ICP-Brasil.
- **OQ-018** — granularidade mínima de ativo exigida pelo piloto.

---

## 7. Riscos (XLS-002)

Dezoito riscos registrados com escala 1–5 e score = probabilidade × impacto. Os de maior exposição:

| ID | Risco | Score |
| --- | --- | --- |
| RSK-001 | Indefinição do referencial técnico vigente para qualidade do ar | 20 |
| RSK-003 | Scope creep no MVP | 16 |
| RSK-004 | Ausência de cliente-piloto engajado | 15 |
| RSK-006 | Definição tardia do modelo de multi-tenancy | 15 |
| RSK-017 | Backup existente com restore nunca testado | 15 |
| RSK-002 | Vazamento de dados entre tenants | 10 (impacto máximo) |

---

## 8. Inconsistências e pontos de atenção identificados

**INC-001 — Cadeia normativa quebrada (crítico).** A Lei nº 13.589/2018 (Planalto) remete os parâmetros de qualidade do ar à **RE/ANVISA nº 9/2003** "e posteriores alterações". Em consulta ao repositório normativo da ANVISA em **22/09/2026**, a RE nº 9/2003 consta **revogada pela RDC nº 886, de 10/07/2024** — resolução de revogação expressa do ciclo 2023–2024 de consolidação normativa. Fontes secundárias do setor indicam que a referência técnica passou a ser uma norma ABNT da família de qualidade do ar interior; **essa afirmação não foi confirmada em fonte primária e não é adotada aqui**. Consequência: os parâmetros de medição exigíveis **não podem ser fixados pela engenharia**. Encaminhamento: OQ-004, com parecer jurídico e de responsável técnico. Mitigação arquitetural: Compliance as Data isola o impacto ao dado, não ao código.

**INC-002 — Vigência da Portaria GM/MS nº 3.523/1998 não confirmada.** O documento é amplamente referenciado como base dos procedimentos de manutenção, mas sua situação atual precisa ser verificada no sistema Saúde Legis do Ministério da Saúde, inclusive quanto a eventual revogação por consolidação. Encaminhamento: OQ-012.

**INC-003 — Divergência de critério de aplicabilidade no mercado.** Fontes secundárias divergem sobre a existência de limiar de capacidade (por exemplo, 60.000 BTU/h) para obrigatoriedade do PMOC, uma vez que a Lei nº 13.589/2018 não reproduz esse limiar em seu texto. **Nenhum critério foi adotado no produto.** O critério de aplicabilidade será modelado como dado (`ApplicabilityRule`) e preenchido somente após validação jurídica.

**INC-004 — Normas técnicas ABNT.** São protegidas por direito autoral e, portanto, **referenciadas e não reproduzidas**. A Services.NET precisa adquiri-las legitimamente para consulta interna (DEP-003) antes da Fase 2.

**INC-005 — Exigências estaduais e municipais.** Não levantadas nesta fase. Podem impor requisitos adicionais ao piloto (OQ-013).

**INC-006 — Governança documental.** O Master Specification prevê duas representações (Microsoft 365 e Git). Enquanto a Fase 10 não define a divisão, a fonte autoritativa é o Microsoft 365. Sem essa regra, haveria risco imediato de fontes conflitantes.

**INC-007 — Personas não validadas.** DOC-005 é integralmente hipótese; foi marcado como tal e não deve ser usado como base de decisão de UX antes da Fase 2.

---

## 9. Informações que precisam ser obtidas com o cliente

1. Processo operacional real: do fechamento do contrato à entrega do relatório ao cliente final.
2. Volumetria: clientes, unidades, ambientes, sistemas, equipamentos, OS/mês, técnicos.
3. Estrutura atual de dados (planilhas, sistemas legados) e qualidade do inventário.
4. Papéis reais, permissões praticadas e regras de segregação interna.
5. Modelo de planos de manutenção em uso, periodicidades praticadas e origem dessas periodicidades.
6. Checklists e formulários atualmente utilizados em campo.
7. Medições coletadas, instrumentos, unidades e critérios de aceitação praticados.
8. Tratamento atual de não conformidades e ações corretivas.
9. Formato, conteúdo e destinatários dos relatórios e do PMOC entregues hoje.
10. Condições reais de campo: conectividade, dispositivos, restrições de acesso e de segurança do trabalho.
11. Exigências contratuais e de fiscalização já enfrentadas.
12. Expectativas explícitas quanto ao MVP e critérios do cliente para considerá-lo bem-sucedido.

---

## 10. Itens que não puderam ser determinados nesta fase

- Nome comercial do produto.
- Datas, esforço, custo e composição de equipe.
- Metas numéricas das métricas de sucesso.
- Referencial técnico regulatório exigível e periodicidades legítimas.
- Bases legais da LGPD por categoria de dado.
- Modelo de isolamento multi-tenant e demais escolhas tecnológicas.
- Nível exigido de acessibilidade.
- Necessidade real de assinatura qualificada e de geolocalização.
- Modelo comercial e de contrato do piloto.

---

## 11. Recomendação por artefato

| Artefato | Recomendação | Condição |
| --- | --- | --- |
| DOC-001 Product Charter | **Aprovar com ressalvas** | Preencher patrocinador (OQ-002) e Product Owner (OQ-003); manter §5 sob revisão até parecer jurídico |
| DOC-002 Vision and Principles | **Aprovar** | Sem dependências externas |
| DOC-003 Project Scope | **Aprovar** | Reavaliar itens "A validar" após a Fase 2 |
| DOC-004 Stakeholder Map | **Aprovar com ressalvas** | Fechar GAP-001 a GAP-005 |
| DOC-005 Personas | **Revisar** | Validar com o piloto antes de usar em decisões de UX |
| DOC-006 Capabilities Map | **Aprovar** | Reclassificação permitida via gestão de mudança |
| DOC-007 MVP Definition | **Aprovar com ressalvas** | Reconfirmar após levantamento da Fase 2 |
| DOC-008 Roadmap | **Aprovar com ressalvas** | Incluir datas somente após OQ-007 |
| XLS-001 Assumptions/Constraints/Dependencies | **Aprovar** | Manutenção contínua |
| XLS-002 Risk Register | **Aprovar** | Reavaliar a cada fase |
| XLS-003 Open Questions | **Aprovar** | Atribuir prazos aos responsáveis |
| XLS-004 Decision Log | **Aprovar as decisões como propostas** | Converter para "Aprovada" na revisão formal |
| XLS-005 RTM | **Aprovar a estrutura** | Preenchimento a partir da Fase 2 |
| DIA-001 Context Diagram | **Aprovar** | Atualizar quando o escopo do MVP for reconfirmado |

---

## 12. Critérios de aceite da Fase 1

| ID | Critério | Situação |
| --- | --- | --- |
| AC-F1-01 | Todos os artefatos exigidos pelo Master Specification §26 foram produzidos | Atendido |
| AC-F1-02 | O Product Charter contém os 32 itens obrigatórios do §27 | Atendido |
| AC-F1-03 | Toda capacidade possui exatamente uma classificação de Scope Boundary | Atendido |
| AC-F1-04 | Nenhum requisito, norma ou regra foi inventado | Atendido |
| AC-F1-05 | Toda incerteza está registrada como hipótese ou questão aberta | Atendido |
| AC-F1-06 | Fontes regulatórias registradas com órgão, data de consulta e situação | Atendido, com INC-001 e INC-002 em aberto |
| AC-F1-07 | Decisões, riscos, dependências e pendências registrados antes do avanço | Atendido |
| AC-F1-08 | Aprovação formal da Services.NET | **Pendente** |

---

## 13. Pré-condições para iniciar a Fase 2

1. Aprovação formal deste pacote pela Services.NET.
2. Patrocinador e Product Owner designados.
3. Cliente-piloto confirmado e agenda de levantamento definida.
4. Solicitações de parecer jurídico e de responsável técnico formalmente abertas.
5. Normas técnicas aplicáveis adquiridas legitimamente.
6. Questões abertas bloqueantes (OQ-002, OQ-003, OQ-010) respondidas.

**A Fase 2 — Levantamento completo de requisitos e regras do PMOC — não será iniciada automaticamente.** Aguarda-se a revisão formal da Services.NET.

---

## 14. Nota de responsabilidade

Este pacote é material de engenharia de software. Ele **não** constitui parecer jurídico, **não** determina vigência normativa, **não** substitui responsável técnico habilitado e **não** certifica conformidade regulatória. Os pontos que exigem validação jurídica ou de responsável técnico estão sinalizados individualmente nos artefatos e consolidados nas seções 6 e 8 deste documento.
