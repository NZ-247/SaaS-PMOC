# PHASE-01-V0.2-CHANGE-REPORT.md

**Projeto:** PMOC Software — Product & Engineering Master Specification
**Organização:** Services.NET
**Fase:** 1 — Product Charter e Escopo
**Transição:** v0.1 DRAFT → **v0.2 DRAFT**
**Data:** 22/09/2026
**Origem de todas as alterações:** **Services.NET Phase 1 Audit — Approved**
**Status:** Aguardando segunda revisão formal da Services.NET
**Autor:** Opus — análise, arquitetura, documentação, modelagem, revisão e planejamento
**Finalização local:** Codex — revisão pós-Opus, higienização do repositório e atualização de rastreabilidade

---

## A. Resumo executivo

A v0.1 foi considerada estruturalmente adequada e **não foi refeita**. Esta revisão é **corretiva e controlada**: corrige, esclarece e harmoniza os pontos apontados pela auditoria, sem ampliar escopo, sem iniciar a Fase 2, sem produzir implementação e sem decidir ADRs.

Foram executadas **17 correções** agrupadas em três naturezas: regulatórias (4), de consistência (8) e de governança (5). Nenhuma capacidade foi criada, removida ou reclassificada. Nenhum identificador foi reaproveitado para conceito diferente.

Os quatro efeitos de maior peso:

1. **A cadeia normativa deixou de estar quebrada.** A ABNT NBR 17037 foi incorporada à matriz regulatória preliminar como **norma técnica** — não como instrumento de igual status jurídico a lei, portaria ou resolução. O risco RSK-001 caiu de score 20 para 12.
2. **O limite de 5 TR / 60.000 BTU/h deixou de ser tratado como divergência única.** Passaram a existir duas regras conceitualmente distintas: **Regra A — aplicabilidade do PMOC** e **Regra B — exigência de responsável técnico**.
3. **A tensão entre CAP-033 e o critério de MVP foi eliminada** pela separação entre capacidade estrutural (admitida no MVP) e conteúdo regulatório concreto (não carregado sem validação).
4. **Prescrições prematuras foram removidas**: `TenantId` como coluna física, assinatura simples como suficiente, checklist obrigatório para toda OS e API obrigatória para toda funcionalidade de interface.

A validação cruzada revelou ainda um **erro de consolidação não apontado pela auditoria**: a v0.1 declarava a consolidação **77/43**; a contagem real do catálogo é **79/50**. O catálogo estava correto; a tabela de consolidação estava errada. Corrigido.

---

## B. Matriz de alterações

| ID | Artefato | Seção | Alteração | Motivo | Impacto |
| --- | --- | --- | --- | --- | --- |
| CHG-01 | DOC-001 | §5.1, §5.2 | Matriz regulatória preliminar passa a incluir a ABNT NBR 17037, com natureza, situação e data de consulta. Nova §5.2 sobre tratamento da natureza jurídica da norma técnica | Auditoria §3 | OQ-004, OQ-019, RSK-001, RSK-011, CON-004, DEC-009 |
| CHG-01a | PHASE-01-REVIEW | INC-001 | Reescrito: deixa de afirmar que a relação com a NBR 17037 consta apenas em "fontes secundárias" | Auditoria §3 | Redução de incerteza declarada |
| CHG-01b | XLS-002 | RSK-001 | Reformulado; probabilidade 4→3, impacto 5→4, score 20→12 | Auditoria §3 | Perfil de risco da Fase 1 |
| CHG-01c | XLS-003 | OQ-004 | Reformulada de "qual referencial existe" para "qual a extensão da aplicabilidade" | Auditoria §3 | Encaminhamento correto ao Jurídico e ao responsável técnico |
| CHG-02 | DOC-001 | §5.3 (nova) | Distinção formal entre Regra A e Regra B; veda o uso automático do limite de 5 TR / 60.000 BTU/h como condição única de existência de PMOC | Auditoria §4 | CAP-035, COMP-004, OQ-021, INC-003 |
| CHG-02a | DOC-006 | CAP-035 | Descrição passa a exigir regras distintas por objeto de regulação | Auditoria §4 | Modelagem de `ApplicabilityRule` na Fase 2/3 |
| CHG-03 | XLS-003 | OQ-012 | Reformulada: reconhece disponibilidade em fonte oficial, referência em documentação regulatória posterior e fortes evidências de aplicação atual; mantém pendente apenas a confirmação jurídica formal | Auditoria §5 | DOC-001 §5.1, Regra B |
| CHG-04 | DOC-006, DOC-007 | CAP-033, §3.1 | Separação entre capacidade estrutural (MVP) e conteúdo regulatório (não carregado sem validação) | Auditoria §6 | OOS-015, AC-MVP-11, COMP-002, RSK-MVP-03 |
| CHG-04a | DOC-003 | §4 | Nova exclusão OOS-015 — carga de valores regulatórios concretos | Auditoria §6 | Scope Boundary |
| CHG-04b | XLS-005 | COMP-002 | Nova linha semente na RTM | Auditoria §6 | Rastreabilidade |
| CHG-05 | DOC-001 | §25 | Removida a prescrição de coluna `TenantId`; mantida a regra semântica e de segurança; mecanismo físico remetido ao ADR-001 | Auditoria §7 | DATA-001, NFR-MVP-01, PE-02, DEC-004, RSK-006 |
| CHG-05a | DOC-002 | PE-02 | Reescrito como regra semântica | Auditoria §7 | Princípios de engenharia |
| CHG-05b | XLS-005 | DATA-001 | Reescrito sem prescrição física | Auditoria §7 | RTM |
| CHG-06 | Vários | ASM-012, CAP-054, OOS-010, DOC-007 §4 | Assinatura harmonizada como **A validar**, sem nível presumido, em todos os artefatos | Auditoria §8 | Elimina estado triplo da v0.1 |
| CHG-06a | DOC-005 | PER-004, PER-007 | Removidas menções a assinatura como requisito presumido | Auditoria §8 | Personas |
| CHG-07 | XLS-003 | OQ-006 | Reformulada para nível de identificação, manifestação de vontade, autoria, integridade e não repúdio por ato/documento | Auditoria §9 | CAP-054, RSK-MVP-06 |
| CHG-08 | DOC-007 | AC-MVP-03 | Passa a exigir os requisitos obrigatórios de execução definidos para o tipo de OS e template aplicável, incluindo checklist quando requerido | Auditoria §10 | CAP-045, CAP-050, FR-002 |
| CHG-09 | DOC-007, DOC-001 | AC-MVP-08, §26 | API First reformulado: contrato para operação de negócio ou server-side; sem endpoint artificial para comportamento local | Auditoria §11 | PE-01, NFR-002, ADR-007 |
| CHG-10 | DOC-004 | §2, §3, §4, §6 | STK-007 restrito a Jurídico/Regulatório; criado STK-021 — DPO/Encarregado; RACI desdobrado; GAP-005 e GAP-006 | Auditoria §12 | XLS-001, XLS-002, XLS-003, DOC-001 §30 |
| CHG-11 | DOC-008, XLS-004 | W1, §4, §5, ADR Register | ADR-008 posicionado como pré-requisito das partes dependentes do modelo de Compliance as Data | Auditoria §13 | DEP-009, sequência de W1 |
| CHG-12 | Overview_Project.md | Cabeçalho e lista de arquivos | Patch com aviso REFERENCE / NON-AUTHORITATIVE e correção da duplicidade de `AGENTS.md` | Auditoria §14 | CON-010, DOC-001 §30 |
| CHG-13 | XLS-001 | Summary | Fórmulas corrigidas (contavam a linha de cabeçalho); verificação estendida a XLS-002 a XLS-005 | Auditoria §15 | Dashboards e automações futuras |
| CHG-14 | DOC-001, DOC-002, DOC-006, DOC-007 | §9.2, PP-13, CAP-037, AC-MVP-02 | Princípio de preservação do estado de referência do PMOC emitido | Auditoria §16 | OQ-020, RSK-019, COMP-003 |
| CHG-15 | DIA-001 | — | Ajustes de legibilidade; atualização do rótulo do contexto regulatório; fronteiras conceituais preservadas | Auditoria §17 | Nenhum impacto conceitual |
| CHG-16 | Todos | Cabeçalhos | Versão 0.2 DRAFT; status "Aguardando segunda revisão formal"; origem das alterações declarada | Auditoria §18 | Controle de versão |
| CHG-17 | DOC-006, DOC-007, DOC-001 | DOC-006 §4, DOC-007 §3, DOC-001 §15 | Consolidação de capacidades corrigida de 77/43 para **79/50** | Validação cruzada (§22 da auditoria) | Coerência entre artefatos |

Registro operacional equivalente na aba **Change Control** de XLS-004 (16 itens, incluindo AUDIT-01 e CODEX-REVIEW-01).

---

## C. Correções regulatórias

| # | Correção | Estado anterior (v0.1) | Estado atual (v0.2) |
| --- | --- | --- | --- |
| R1 | **ABNT NBR 17037 incorporada** | "Fontes secundárias do setor indicam uma norma ABNT como novo referencial; não confirmado" | Norma identificada nominalmente, registrada na matriz preliminar como **norma técnica** vigente no catálogo da ABNT (primeira edição 04/2023; edição posterior 10/2024 incorporando errata), indicada como referência após a revogação da RE nº 9/2003 conforme orientação oficial da ANVISA de 2025 informada pela auditoria |
| R2 | **Natureza jurídica preservada** | Ausente | §5.2 do DOC-001 veda tratar a norma técnica como equivalente a lei, portaria ou resolução; exige aquisição legítima e validação jurídica quanto à extensão da aplicabilidade |
| R3 | **Regra A × Regra B** | INC-003 tratava o tema como divergência sobre limiar de 60.000 BTU/h | §5.3 do DOC-001 define duas regras distintas e veda o uso automático do limite como condição única de existência de PMOC |
| R4 | **Portaria GM/MS nº 3.523/1998** | "Situação de vigência a confirmar"; redação sugeria ausência de evidência de aplicação | Reconhecida a disponibilidade em fonte oficial, a referência em documentação regulatória posterior e as fortes evidências de aplicação atual. **Vigência jurídica formal continua não declarada** — OQ-012 reformulada |

**Finalização local por Codex.** A referência oficial foi confirmada e registrada: **Guia nº 73/2024, versão 2, de 03/04/2025 — Guia de boas práticas em células e tecidos humanos para uso terapêutico**, Agência Nacional de Vigilância Sanitária (ANVISA), Biblioteca Digital da Anvisa, item 17752; vigente a partir de 04/04/2025. O guia é instrumento regulatório **não normativo**, de caráter recomendatório e não vinculante. **OQ-019 foi respondida/encerrada.** Nenhum parâmetro, limite, faixa ou periodicidade da ABNT NBR 17037 foi reproduzido ou carregado.

---

## D. Correções de consistência

| # | Correção | Antes | Depois |
| --- | --- | --- | --- |
| C1 | **CAP-033 × critério de MVP** | CAP-033 no MVP, mas o MVP não pode depender de decisão jurídica pendente | Capacidade estrutural no MVP; conteúdo regulatório excluído (OOS-015) e condicionado a validação (AC-MVP-11) |
| C2 | **TenantId** | Sugeria coluna física em toda entidade | Regra semântica e de segurança; implementação física é do ADR-001 |
| C3 | **Assinatura** | Simultaneamente hipótese do MVP (ASM-012), capacidade "A validar" (CAP-054) e item fora do MVP | Estado único: **A validar**, sem nível presumido, em todos os artefatos |
| C4 | **AC-MVP-03** | Exigia checklist para toda OS concluída | Requisitos obrigatórios de execução por tipo de OS e template, incluindo checklist quando requerido |
| C5 | **AC-MVP-08** | "Toda funcionalidade da UI existe como operação de API documentada" | Contrato para operação de negócio ou server-side; comportamento local não exige endpoint |
| C6 | **Consolidação de capacidades** | Consolidação histórica 77/43/21/7/6 | **79 capacidades, 50 MVP, 19 Pós-MVP, 5 Futuro, 5 A validar** — catálogo inalterado, tabela corrigida, com verificação por domínio |
| C7 | **Summary de XLS-001** | Restrições e dependências contavam a linha de cabeçalho | Fórmulas corrigidas; valores conferidos linha a linha |
| C8 | **Terminologia** | Uso alternado de "cliente", "sistema", "ativo", "checklist" | Tabela oficial em DOC-003 §11, aplicada a todos os artefatos |

---

## E. Correções de governança

| # | Correção | Efeito |
| --- | --- | --- |
| G1 | **Jurídico × DPO separados** | STK-007 restrito a interpretação legal, vigência, aplicabilidade, contratos e valor probatório; **STK-021** criado para LGPD, bases legais, categorias de dados, retenção, minimização e direitos dos titulares. RACI desdobrado; responsáveis atualizados em ASM-006, OQ-015, RSK-010, DEP-010 |
| G2 | **ADR-008 sequenciado** | Posicionado como decisão estrutural necessária antes da implementação das partes dependentes (CAP-030 a CAP-035, CAP-037, CAP-038); incorporado a DEP-009 e ao critério de entrada de W1. **Conteúdo não antecipado** |
| G3 | **Decision Log preservado** | DEC-001 a DEC-010 permanecem `Proposta`. A aceitação da auditoria foi registrada como **AUDIT-01** na nova aba Change Control, sem conversão automática de status. Regra incorporada a DOC-001 §31, item 6 |
| G4 | **Overview_Project.md** | Marcado como REFERENCE / NON-AUTHORITATIVE via patch; duplicidade de `AGENTS.md` corrigida; registrado em CON-010 e DOC-001 §30 |
| G5 | **Controle de versão** | Todos os artefatos alterados passam a v0.2 DRAFT com status "Aguardando segunda revisão formal da Services.NET". A Fase 1 **não** foi marcada como APPROVED |

---

## F. Questões novas da v0.2 — estado após finalização local

| ID | Questão (resumo) | Autoridade | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| **OQ-019** | Referência oficial exata da orientação da ANVISA que indica a ABNT NBR 17037 como referência de qualidade do ar interior | Respondida por Codex | Encerrada | Guia nº 73/2024, versão 2, de 03/04/2025; Biblioteca Digital da Anvisa, item 17752 |
| **OQ-020** | Mecanismo que preservará o estado de referência de um PMOC emitido | Architect (STK-003) | Alta | Auditoria §16 |
| **OQ-021** | Exigências estaduais, municipais, setoriais, contratuais ou situações de uso restrito que possam afetar Regra A / Regra B | Jurídico (STK-007) + Resp. técnico (STK-012) | Alta | Reformulada por Codex; no contexto federal, 5 TR / 60.000 BTU/h fundamenta a Regra B, não uma condição geral da Regra A |

Total histórico: 18 → **21 registradas**. Estado após Codex: **20 abertas**, **1 respondida/encerrada**.

---

## G. Questões reformuladas

### OQ-004
- **Antes:** "Qual referencial técnico de qualidade do ar é exigível hoje, dada a revogação da RE 9/2003 pela RDC 886/2024?"
- **Agora:** "Qual é a extensão da aplicabilidade da ABNT NBR 17037 ao produto e a cada requisito dele derivado, considerando a revogação da RE 9/2003 pela RDC 886/2024 e a orientação oficial da ANVISA indicando a norma como referência? Quais parâmetros são exigíveis e a partir de qual edição?"
- **Razão:** a existência do referencial deixou de ser incógnita. O que permanece aberto é a **extensão da aplicabilidade** e a edição aplicável — questão jurídica e técnica, não de identificação.

### OQ-006
- **Antes:** "A assinatura coletada em campo precisa de validade ICP-Brasil?"
- **Agora:** "Qual nível de identificação, manifestação de vontade, autoria, integridade e não repúdio é necessário para cada ato ou documento produzido pela plataforma, considerando legislação, exigências contratuais, fiscalização e finalidade probatória?" — com distinção possível entre aceite/acknowledgement, assinatura eletrônica simples, avançada, qualificada, baseada em ICP-Brasil e provedor externo.
- **Razão:** a pergunta anterior pressupunha uma solução binária e induzia à escolha tecnológica antes da definição da necessidade probatória.

### OQ-012
- **Antes:** "A Portaria GM/MS 3.523/1998 permanece vigente e em que extensão?" — com observação que sugeria ausência de evidência de aplicação.
- **Agora:** "Confirmar formalmente eventual alteração, revogação, consolidação ou extensão atual da Portaria GM/MS nº 3.523/1998 para fins da matriz regulatória oficial do produto. O Art. 6º e sua redação sobre o limite acima de 5 TR (15.000 kcal/h = 60.000 BTU/h) e responsável técnico já estão identificados em fonte oficial."
- **Razão:** a fonte oficial responde artigo e redação. O que falta é confirmação jurídica formal — não evidência de uso nem identificação do Art. 6º.

### OQ-015
- **Antes:** responsável "Jurídico/DPO".
- **Agora:** responsável **DPO (STK-021)**; redação ampliada para prazos de retenção e direitos de titular.
- **Razão:** separação de autoridades (auditoria §12).

### OQ-010
- **Antes:** cliente-piloto descrito genericamente como não confirmado.
- **Agora:** a existência de cliente candidato/piloto é tratada como confirmada pelo contexto de origem; permanecem pendentes a identidade formal do tenant-piloto, interlocutores, disponibilidade para levantamento, compromisso de operar o MVP e agenda da Fase 2.
- **Razão:** evitar transformar em desconhecido o que o contexto do projeto já confirma, sem inventar nome, CNPJ ou pessoas.

### OQ-021
- **Antes:** perguntava se o limite de 5 TR / 60.000 BTU/h integrava ou não a Regra A.
- **Agora:** trata somente de normas estaduais, municipais, regulamentações setoriais específicas, exigências contratuais e situações de uso restrito.
- **Razão:** no contexto federal documentado, o limite está associado à Regra B pelo Art. 6º da Portaria GM/MS nº 3.523/1998, não a um limiar geral de existência de PMOC.

---

## H. Requisitos e capacidades afetados

**Capacidades (descrição alterada; nenhuma reclassificação):** CAP-030, CAP-031, CAP-032, **CAP-033**, CAP-034, **CAP-035**, **CAP-037**, CAP-045, CAP-050, **CAP-054**, CAP-058, CAP-061, CAP-095.

**Requisitos na RTM:**

| ID | Situação |
| --- | --- |
| NFR-001 | Reescrito — regra semântica de tenant |
| DATA-001 | Reescrito — sem prescrição física |
| COMP-001 | Ampliado — distinção de natureza normativa |
| **COMP-002** | **Novo** — capacidade estrutural de parâmetros |
| **COMP-003** | **Novo** — estado de referência do PMOC emitido |
| **COMP-004** | **Novo** — Regra A × Regra B |
| **FR-002** | **Novo** — requisitos de execução por tipo de OS |
| **NFR-002** | **Novo** — contrato de API para operação de negócio |
| SEC-001, OPS-001, UX-001, FR-001, BR-001 | Inalterados |

**Critérios de aceite:** AC-MVP-02 ampliado; AC-MVP-03 reescrito; AC-MVP-05 precisado; AC-MVP-08 reescrito; **AC-MVP-11 novo**; AC-SCOPE-05 novo. Total do MVP: 10 → **11**.

**Registros:** ASM-006 e ASM-012 reformulados (total 12); CON-004, CON-005, CON-010 e CON-011 reformulados (total 12); DEP-001, DEP-003, DEP-008 e DEP-009 reformulados e **DEP-010 criado** (total 9 → **10**); RSK-001, RSK-002, RSK-006, RSK-010, RSK-011, RSK-016 e RSK-018 reformulados e **RSK-019 criado** (total 18 → **19**).

---

## I. Itens deliberadamente não alterados

Para demonstrar ausência de scope creep:

1. **O catálogo de capacidades.** Nenhuma capacidade criada, removida ou reclassificada. Apenas a tabela de consolidação foi corrigida.
2. **O escopo do MVP.** As mesmas 50 capacidades da v0.1 permanecem; o que mudou foi a explicitação da separação entre capacidade estrutural e conteúdo.
3. **As decisões DEC-001 a DEC-010.** Permanecem `Proposta`. Nenhuma foi aprovada, rejeitada ou substituída.
4. **Os ADRs.** Nenhum foi decidido. Do ADR-008 alterou-se apenas a posição na sequência de dependências, não o conteúdo.
5. **A arquitetura do DIA-001.** As fronteiras conceituais são idênticas; "Contexto Regulatório" permanece como fonte de requisitos e não como sistema externo.
6. **A visão, a missão e a proposta de valor.**
7. **O roadmap por ondas.** Continua sem datas (OQ-007 aberta).
8. **As exclusões de escopo da v0.1.** Nenhuma foi revertida; duas foram acrescentadas (OOS-015) ou precisadas (OOS-010).
9. **As personas.** Continuam como hipótese não validada; apenas terminologia e menções a assinatura foram ajustadas.
10. **Nenhum parâmetro regulatório foi preenchido.** Nenhum valor, faixa, limite ou periodicidade foi carregado.
11. **Nada da Fase 2 em diante foi produzido:** sem entrevistas, requisitos completos, BPMN, modelo de domínio definitivo, ERD, escolha de banco ou stack, arquitetura de infraestrutura, OpenAPI, código, `AGENTS.md`/`CLAUDE.md` definitivos, backlog ou estimativas.

---

## J. Resultado da auto-revisão

### J.1 Validação cruzada executada

Verificação entre DOC-001 a DOC-008, XLS-001 a XLS-005, DIA-001, Overview_Project.md e PHASE-01-REVIEW.md.

**Contagens — conferidas e coerentes entre documento e planilha:**

| Item | Valor v0.2 | Conferido em |
| --- | --- | --- |
| Capacidades | 79 (50 MVP, 19 Pós-MVP, 5 Futuro, 5 A validar) | DOC-006 §4 e contagem por domínio; DOC-007 §3 |
| Hipóteses | 12 | XLS-001 Assumptions + Summary |
| Restrições | 12 | XLS-001 Constraints + Summary; DOC-001 §19 |
| Dependências | 10 | XLS-001 Dependencies + Summary |
| Questões registradas | 21 (20 abertas; 1 encerrada) | XLS-003 + Summary |
| Riscos | 19 | XLS-002 + Summary |
| Decisões | 11, todas `Proposta` | XLS-004 + Summary |
| ADRs indexados | 8, nenhum decidido | XLS-004 ADR Register; DOC-008 §5 |
| Critérios de aceite do MVP | 11 | DOC-007 §6 |
| Linhas semente da RTM | 13 | XLS-005 + Summary |
| Itens de controle de mudança | 16 (AUDIT-01 + CHG-01 a CHG-14 + CODEX-REVIEW-01) | XLS-004 Change Control |

**Estados:** nenhuma capacidade aparece com mais de uma classificação. A única situação de dupla natureza — CAP-033 — foi resolvida por regra formal (DOC-003 §2, parágrafo final): a classificação recai sobre a capacidade, e a restrição sobre o conteúdo é declarada no próprio item.

**IDs:** nenhum duplicado; nenhum reaproveitado para conceito diferente. STK-021, DEP-010, RSK-019, OQ-019 a OQ-021, DEC-011, COMP-002 a COMP-004, FR-002, NFR-002, AC-MVP-11, AC-SCOPE-05, OOS-015, GAP-006 e PP-13 são identificadores novos.

**Referências:** todas as referências a §, CAP, OQ, ASM, RSK, DEC, ADR, STK, DEP e CON foram verificadas contra os registros existentes. Nenhuma referência pendente foi localizada.

**Terminologia:** padronizada conforme DOC-003 §11.

### J.2 Inconsistências restantes

| ID | Inconsistência | Natureza | Encaminhamento |
| --- | --- | --- | --- |
| RES-01 | **Encerrado por Codex.** Referência oficial da ANVISA registrada em fonte primária | Rastreabilidade de fonte | OQ-019 respondida/encerrada |
| RES-02 | **Encerrado quanto ao artigo e à redação.** Art. 6º da Portaria GM/MS nº 3.523/1998 e limite acima de 5 TR (15.000 kcal/h = 60.000 BTU/h) registrados | Precisão normativa | OQ-012 permanece somente para confirmação jurídica formal |
| RES-03 | **Encerrado por Codex.** `Overview_Project.md` recebeu o bloco REFERENCE / NON-AUTHORITATIVE e a duplicidade de `AGENTS.md` foi removida | Artefato externo | Patch aplicado |
| RES-04 | Metas numéricas das métricas de sucesso continuam vazias | Produto | OQ-005 |
| RES-05 | Autoridades (patrocinador, PO, Jurídico, DPO, responsável técnico) continuam nominalmente vazias | Governança | OQ-002, OQ-003, GAP-004 a GAP-006 |
| RES-06 | O roadmap continua sem datas | Planejamento | OQ-007 |

### J.3 Riscos introduzidos por esta revisão

| Risco introduzido | Avaliação | Tratamento |
| --- | --- | --- |
| A separação entre capacidade estrutural e conteúdo pode ser lida como licença para entregar o MVP sem qualquer conformidade útil | Real, porém baixo | AC-MVP-11 e DOC-007 §3.1 deixam explícito que a ausência é de **valores não validados**, não de conformidade |
| A remoção da prescrição de `TenantId` pode ser lida como enfraquecimento do isolamento | Real, porém baixo | NFR-MVP-01, PE-02 e AC-MVP-05 reforçam a regra semântica e a verificação server-side |
| A flexibilização de AC-MVP-08 pode ser usada para justificar lógica de negócio na interface | Real, moderado | PP-05 e PE-01 mantêm a vedação; NFR-002 exige inventário das operações de negócio na conferência |
| A flexibilização de AC-MVP-03 pode ser usada para concluir OS sem registro | Real, moderado | A exigência passou a ser "requisitos obrigatórios definidos para o tipo", o que **requer** que cada tipo de OS declare seus requisitos — CAP-045 e FR-002 |

Nenhum risco introduzido foi avaliado como alto. RSK-019 foi registrado como risco de produto, não como risco desta revisão.

### J.4 Referências cruzadas quebradas

Nenhuma identificada após a revisão. As referências da v0.1 a "XLS-002 (18 riscos)" e à consolidação histórica 77/43 foram corrigidas em DOC-001 §15, §21, DOC-006 §4 e DOC-007 §3.

### J.5 Divergências de contagem

Duas encontradas e corrigidas: as fórmulas de Summary de XLS-001 (restrições e dependências) e a consolidação de capacidades do DOC-006. As demais planilhas foram verificadas e não apresentavam a mesma falha, mas todas tiveram as fórmulas normalizadas para a primeira linha de dados e receberam valores esperados para conferência cruzada.

### J.6 Artefatos ainda dependentes de validação externa

| Artefato | Dependência | Autoridade |
| --- | --- | --- |
| DOC-001 §5.1, §5.2, §5.3 | Extensão da aplicabilidade da ABNT NBR 17037; confirmação jurídica formal da Portaria; normas locais, setoriais ou contratuais relacionadas à Regra A × Regra B | Jurídico (STK-007) |
| DOC-005 (integral) | Confirmação das personas | Cliente-piloto (STK-010) |
| CAP-033, CAP-035, CAP-038 (conteúdo) | Parâmetros, faixas e periodicidades | Resp. técnico (STK-012) |
| CAP-054, CAP-058, CAP-095 | Nível probatório e bases legais | Jurídico (STK-007) e DPO (STK-021) |
| DOC-008 (datas) | Equipe, orçamento e prazo | Patrocinador (STK-001) |

---

## K. Finalização local por Codex — revisão pós-Opus

Esta seção registra a execução local posterior ao trabalho do Opus, sem apagar o histórico das alterações anteriores.

**Problemas encontrados e corrigidos:**

- `PHASE-01-REVIEW.md` v0.1 e `PHASE-01-REVIEW(1).md` v0.2 concorriam no diretório principal.
- `DIA-002_System_Product_Context_Diagram.png` era revisão visual do DIA-001, não novo artefato conceitual.
- Planilhas continham sufixo artificial ` 1.xlsx`.
- `Overview_Project.md` ainda não tinha recebido o patch v0.2.
- OQ-019 permanecia aberta apesar da fonte oficial ter sido identificada.
- OQ-012/OQ-021 ainda mantinham perguntas que a fonte oficial já respondia.
- A edição local/versionamento Git criou uma questão de governança documental M365 × Git.

**Arquivos renomeados ou higienizados:**

- `PHASE-01-REVIEW(1).md` passa a ser o canônico `PHASE-01-REVIEW.md`.
- `DIA-002_System_Product_Context_Diagram.png` substitui o conteúdo canônico de `DIA-001_System_Product_Context_Diagram.png`.
- `XLS-001` a `XLS-005` passam a usar nomes canônicos com `- v0.2.xlsx`.
- `Overview_Project_20-_20PATCH_20v0.2.md` foi removido após aplicação.

**Atualizações regulatórias e de governança:**

- Fonte ANVISA registrada: Guia nº 73/2024, versão 2, de 03/04/2025; Biblioteca Digital da Anvisa, item 17752; vigente a partir de 04/04/2025; instrumento regulatório não normativo, recomendatório e não vinculante.
- OQ-019 encerrada.
- OQ-012 reformulada para tratar apenas de confirmação jurídica formal de eventual alteração, revogação, consolidação ou extensão atual da Portaria.
- OQ-021 reformulada para tratar apenas de normas locais, setoriais, contratuais ou situações de uso restrito.
- OQ-010 refinada: existência de cliente candidato/piloto confirmada pelo contexto; identidade formal e compromisso operacional seguem pendentes.
- DEC-011 criada como **Proposta**, sem aprovação automática.
- `CODEX-REVIEW-01` registrado na aba Change Control.

**Contagens finais após Codex:**

- Capacidades: 79 total; 50 MVP; 19 Pós-MVP; 5 Futuro; 5 A validar.
- Hipóteses: 12.
- Restrições: 12.
- Dependências: 10.
- Questões registradas: 21; abertas: 20; encerradas: 1.
- Riscos: 19.
- Decisões: 11, todas `Proposta`.
- ADRs indexados: 8, nenhum decidido.
- Critérios AC-MVP: 11.
- RTM: 13 linhas semente.

**Itens ainda pendentes:**

- RES-04: metas numéricas das métricas de sucesso (OQ-005).
- RES-05: autoridades nominalmente não designadas.
- RES-06: roadmap sem datas (OQ-007).
- DEC-011 aguarda deliberação formal da Services.NET.

---

**A Fase 2 não foi iniciada e permanece aguardando nova revisão formal da Services.NET.**
