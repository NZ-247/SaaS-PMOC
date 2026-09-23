# STATUS: REFERENCE / NON-AUTHORITATIVE

Este documento registra somente a concepção inicial do projeto.

Em caso de divergência, prevalecem os artefatos formais da Fase 1 do **PMOC Software — Product & Engineering Master Specification** e suas fontes autoritativas declaradas.

Fontes autoritativas vigentes:
- **Microsoft 365** — ambiente de autoria, colaboração, apresentação, visualização executiva, Word, Excel, Power BI e interação com agentes integrados ao ambiente corporativo.
- **Repositório Git** — baseline técnica autoritativa e versionada dos artefatos de engenharia formalmente publicados/aprovados.

Regra de precedência: em caso de divergência entre uma cópia M365 e uma versão formalmente publicada/aprovada no Git, prevalece a baseline aprovada no Git.

Este documento **não** é fonte autoritativa para requisito, arquitetura, escopo, regra de negócio ou conformidade.

Registrado em: CON-010 (XLS-001), DOC-001 §30 e DEC-011 — Aprovada (XLS-004).

---

# PMOC Software — Overview do Projeto

Para esse projeto, eu trataria o software como uma plataforma SaaS vertical para gestão de PMOC, e não apenas como um formulário eletrônico ou gerador de relatórios. Isso muda a arquitetura desde o início e evita que o produto fique limitado quando entrarem app mobile, novos clientes, integrações, automações e alterações regulatórias.

A legislação também reforça essa abordagem. A Lei nº 13.589/2018 determina PMOC para edifícios de uso público e coletivo com ambientes climatizados artificialmente. A Portaria GM/MS nº 3.523/1998 já estrutura informações como identificação do estabelecimento, proprietário/locatário/preposto, responsável técnico, ART, ambientes climatizados, atividades, periodicidades e registros de execução.

Um detalhe especialmente importante para o projeto: a RE Anvisa nº 9/2003, ainda mencionada no texto da Lei, foi revogada pela RDC nº 886/2024. Portanto, referências normativas, parâmetros e periodicidades não devem ser hard-coded. Devem existir como regras configuráveis e versionadas no banco.

---

## 1. Visão que eu adotaria para o produto

A plataforma deveria permitir que uma empresa de climatização gerencie toda a cadeia:

Empresa prestadora → clientes → unidades → ambientes → sistemas de climatização → equipamentos → componentes → PMOC → manutenções → evidências → não conformidades → relatórios → histórico.

### Modelo conceitual inicial

```text
PLATAFORMA SERVICES.NET PMOC
│
├── Empresa Prestadora / Tenant
│   ├── Usuários
│   ├── Técnicos
│   ├── Responsáveis Técnicos
│   ├── Equipes
│   └── Clientes
│
├── Cliente
│   ├── Matriz
│   └── Unidades / Estabelecimentos
│       ├── Ambientes
│       │   ├── Ocupação
│       │   ├── Área
│       │   └── características
│       │
│       └── Sistemas HVAC
│           └── Equipamentos
│               ├── Fabricante
│               ├── Modelo
│               ├── Número de série
│               ├── Capacidade
│               ├── Localização
│               ├── QR Code
│               ├── Componentes
│               └── Histórico
│
├── PMOC
│   ├── Versão
│   ├── Responsável técnico
│   ├── ART/TRT
│   ├── Regras
│   ├── Plano de manutenção
│   ├── Periodicidades
│   └── Cronograma
│
├── Ordens de Serviço
│   ├── Preventiva
│   ├── Corretiva
│   ├── Preditiva
│   └── Inspeção
│
├── Execução
│   ├── Checklist
│   ├── Medições
│   ├── Fotografias
│   ├── Peças utilizadas
│   ├── Observações
│   ├── Assinatura
│   └── Evidências
│
├── Não conformidades
│   └── Ações corretivas
│
└── Relatórios / Compliance
    ├── PMOC
    ├── Histórico
    ├── Manutenção executada
    ├── Pendências
    ├── Indicadores
    └── Documentos
```

Essa estrutura também acompanha situações reais de contratação pública recentes, nas quais PMOC aparece associado não só à manutenção preventiva, mas também a corretiva, fornecimento de peças, monitoramento da qualidade do ar, instalação/desinstalação e higienização de dutos.

---

## 2. O princípio mais importante: Multi-Tenant

Mesmo que o primeiro cliente seja apenas uma empresa, eu desenvolveria desde o início como:

```text
Services.NET PMOC
        │
        ├── Empresa A
        │     ├── Cliente A1
        │     ├── Cliente A2
        │     └── Cliente A3
        │
        ├── Empresa B
        │     ├── Cliente B1
        │     └── Cliente B2
        │
        └── Empresa C
```

Ou seja:

- Services.NET é dona da plataforma.
- Uma empresa de climatização é um tenant.
- Essa empresa possui seus próprios clientes.

Isso permitirá futuramente comercializar o produto para várias empresas sem criar uma instalação diferente para cada uma.

E devemos garantir isolamento lógico em praticamente todas as entidades pertencentes a uma organização:

```text
tenant_id
```

---

## 3. Perfis de usuário

O RBAC deve nascer cedo no projeto.

### Perfil inicial sugerido

| Perfil | Função |
|---|---|
| Platform Admin | Administração da Services.NET |
| Tenant Admin | Administrador da empresa de climatização |
| Gestor | Gestão operacional |
| Responsável Técnico | Validação técnica e PMOC |
| Supervisor | Coordenação das equipes |
| Técnico | Execução em campo |
| Financeiro | Futuramente contratos/custos |
| Cliente | Visualização pelo contratante |
| Auditor | Acesso somente leitura |

Depois podemos evoluir de RBAC puro para RBAC + permissões granulares.

### Exemplos de permissões

```text
pmoc.create
pmoc.approve
pmoc.sign
asset.create
asset.edit
workorder.execute
workorder.approve
report.generate
customer.view
```

---

## 4. Fluxo principal do produto

Eu vejo o fluxo operacional central assim:

```text
CADASTRO DO CLIENTE
        ↓
CADASTRO DA UNIDADE
        ↓
LEVANTAMENTO DOS AMBIENTES
        ↓
INVENTÁRIO DOS EQUIPAMENTOS
        ↓
CLASSIFICAÇÃO DOS EQUIPAMENTOS
        ↓
DEFINIÇÃO DAS REGRAS DE MANUTENÇÃO
        ↓
CRIAÇÃO DO PMOC
        ↓
VALIDAÇÃO DO RESPONSÁVEL TÉCNICO
        ↓
PUBLICAÇÃO DO PMOC
        ↓
GERAÇÃO AUTOMÁTICA DO CRONOGRAMA
        ↓
GERAÇÃO DAS ORDENS DE SERVIÇO
        ↓
TÉCNICO EXECUTA MANUTENÇÃO
        ↓
CHECKLIST + MEDIÇÕES + FOTOS
        ↓
NORMAL?
   ↙          ↘
 SIM          NÃO
  ↓            ↓
FECHA OS    NÃO CONFORMIDADE
             ↓
        AÇÃO CORRETIVA
             ↓
        NOVA VALIDAÇÃO
             ↓
         HISTÓRICO
             ↓
        RELATÓRIOS / DASHBOARD
```

Isso deve ser o coração do domínio.

---

## 5. Um equipamento não pode ser apenas um cadastro

Esse será um erro fácil de cometer.

Um ativo deve possuir um Digital Asset Record dentro do sistema.

### Exemplo de registro de equipamento

```text
EQ-00001824

Split Hi-Wall
Fabricante: Daikin
Modelo: XXXXX
Serial: XXXXX
Capacidade: 24.000 BTU/h

Cliente: Empresa XYZ
Unidade: Matriz Cuiabá
Local: Sala de reuniões 02
Instalação: 03/04/2024
Status: OPERACIONAL
Próxima preventiva: 15/10/2026
```

Mas junto disso:

```text
Histórico
├─ Instalação
├─ Manutenção 01
├─ Manutenção 02
├─ Troca de filtro
├─ Falha compressor
├─ Manutenção corretiva
└─ Inspeção
```

Essa modelagem posteriormente permite indicadores de:

- MTBF
- MTTR
- reincidência
- custo por ativo
- custo por cliente
- vida útil
- falhas por fabricante
- frequência de corretivas
- equipamentos críticos

Isso transforma o sistema PMOC em algo muito mais valioso.

---

## 6. QR Code deve fazer parte do projeto

Todo equipamento poderá receber algo como:

```text
┌──────────────────┐
│      QR CODE     │
│                  │
│ EQ-000001282     │
│ Services.NET     │
└──────────────────┘
```

O técnico aponta o celular.

O futuro app abre diretamente:

```text
/asset/EQ-000001282
```

E apresenta:

- Equipamento
- Histórico
- Última manutenção
- Próxima manutenção
- Ordens abertas
- Checklist
- Documentos

No app:

Escanear → identificar equipamento → executar OS → coletar evidências → sincronizar.

---

## 7. Arquitetura que recomendo inicialmente

Eu evitaria microsserviços agora.

Para esse estágio, recomendo um Modular Monolith API First.

```text
                    INTERNET
                       │
                 WAF / Reverse Proxy
                       │
               ┌───────▼────────┐
               │   FRONT-END    │
               │ React/Next.js  │
               └───────┬────────┘
                       │ HTTPS
                    REST API
                       │
              ┌────────▼─────────┐
              │   BACK-END       │
              │ Modular Monolith │
              │                  │
              │ Auth             │
              │ Customers        │
              │ Assets           │
              │ PMOC             │
              │ Work Orders      │
              │ Maintenance      │
              │ Compliance       │
              │ Documents        │
              │ Notifications    │
              └───────┬─────────┘
                      │
        ┌─────────────┼─────────────┐
        │             │             │
        ▼             ▼             ▼
   PostgreSQL       Redis       Object Storage
                                  │
                                 Fotos
                                 PDFs
                                 ART
                                 anexos
```

O conceito importante é: monólito no deploy, modular no código.

### Estrutura modular sugerida

```text
src/
├── identity/
├── tenants/
├── customers/
├── sites/
├── environments/
├── assets/
├── technicians/
├── pmoc/
├── maintenance/
├── work-orders/
├── inspections/
├── compliance/
├── documents/
├── reports/
└── notifications/
```

Posteriormente qualquer módulo importante pode virar um serviço separado.

---

## 8. Stack tecnológica preliminar

Uma baseline forte:

### Front-end

- Next.js
- React
- TypeScript
- Tailwind
- component library
- PWA

### Back-end

Uma decisão a documentar em ADR entre:

- ASP.NET Core
- NestJS / TypeScript

Tenho uma leve preferência arquitetural para ASP.NET Core + PostgreSQL nesse produto empresarial, principalmente por robustez, integração corporativa, autenticação, jobs, OpenTelemetry e vida útil da plataforma.

### Dados

- PostgreSQL

### Cache/filas

- Redis

### Arquivos

Object storage compatível com:

- S3
- Azure Blob Storage

Nunca armazenaria fotografias e PDFs diretamente no PostgreSQL.

---

## 9. API First

Mesmo o MVP tendo apenas navegador, o backend deve nascer independente do frontend.

```text
Web
   │
   ├──────────┐
   │          │
REST API     Auth
   │
Backend
```

Quando o aplicativo chegar:

```text
             ┌─ Web
             │
REST API ────┼─ Android
             │
             ├─ iOS
             │
             └─ Integrações
```

Isso evita reconstruir o backend futuramente.

### Documentação automática

- OpenAPI 3.x
- Swagger
- versionamento por API

```text
/api/v1/
```

---

## 10. Mobile deve ser considerado agora, mesmo sendo futuro

Principalmente por causa de offline-first.

Técnicos podem trabalhar em:

- galpões
- hospitais
- indústrias
- telhados
- casas de máquinas
- áreas sem Wi-Fi
- locais com sinal celular ruim

Portanto o aplicativo futuro deveria conseguir:

```text
baixar OS
  ↓
trabalhar offline
  ↓
preencher checklist
  ↓
registrar medições
  ↓
fotografar
  ↓
assinar
  ↓
guardar timestamp
  ↓
sincronizar posteriormente
```

Por isso as APIs devem utilizar identificadores adequados e suportar sincronização.

Eu provavelmente adotaria:

```text
UUIDv7
```

como identificadores de entidades.

---

## 11. Motor de regras de manutenção

Esse pode virar um dos diferenciais comerciais da plataforma.

### Estrutura de regra

```text
REGRA PMOC #102

Tipo: Filtro
Aplicabilidade: UTA
Atividade: Inspecionar / limpar
Periodicidade: 30 dias
Origem: Normativa
Referência: <documento>
Vigência inicial: xx/xx/xxxx
Vigência final: null
Versão: 3
```

Um equipamento poderia herdar:

```text
Tipo de equipamento
      ↓
Template PMOC
      ↓
Regras
      ↓
Plano específico
      ↓
Cronograma
```

E o responsável técnico poderia complementar ou alterar a regra justificadamente.

---

## 12. Compliance Engine

Aqui eu colocaria algo próprio:

- Regulation
- RegulationVersion
- Requirement
- MaintenanceRule
- MeasurementParameter
- ChecklistTemplate

### Exemplo de modelagem

```text
Regulation
   id
   name
   authority
   document_number

RegulationVersion
   regulation_id
   version
   valid_from
   valid_until
   source_url

Requirement
   regulation_version_id
   code
   requirement
```

Assim uma mudança regulatória não exige reescrever regras de negócio.

Isso é particularmente importante diante da revogação da RE nº 9/2003 em 2024.

---

## 13. Ordem de Serviço

Uma OS deveria ser uma entidade própria:

```text
WO-2026-00001428
```

### Campos principais

- Cliente
- Unidade
- Equipamento
- Tipo
  - Preventiva
  - Corretiva
  - Inspeção
  - Emergencial
- Prioridade
- SLA
- Técnico
- Data planejada
- Data executada
- Checklist
- Medições
- Materiais
- Fotos antes
- Fotos depois
- Observações
- Não conformidades
- Assinatura técnico
- Assinatura cliente
- Status

### Workflow sugerido

```text
DRAFT
   ↓
SCHEDULED
   ↓
ASSIGNED
   ↓
IN_PROGRESS
   ↓
AWAITING_REVIEW
   ↓
COMPLETED
```

### Estados excepcionais

```text
CANCELLED
BLOCKED
RESCHEDULED
REJECTED
```

---

## 14. Auditoria deve existir desde a primeira versão

Não apenas:

```text
usuário X alterou o equipamento.
```

Mas sim:

```text
AuditLog

actor
tenant
timestamp
ip
entity
entity_id
operation
before
after
request_id
```

### Exemplo de evento

```text
10:37:52

Alan Silva

ALTEROU:
Periodicidade

DE:
90 dias

PARA:
60 dias

PMOC:
PMOC-1292
```

Isso será fundamental para rastreabilidade.

---

## 15. Documentação do projeto

Aqui eu acho que devemos ser bastante rigorosos.

Eu criaria esta estrutura no repositório:

```text
/docs
├── 00-project/
│   ├── project-charter.md
│   ├── vision.md
│   ├── glossary.md
│   └── scope.md
├── 01-business/
│   ├── business-context.md
│   ├── personas.md
│   ├── business-processes.md
│   ├── requirements.md
│   └── business-rules.md
├── 02-domain/
│   ├── domain-model.md
│   ├── entities.md
│   ├── aggregates.md
│   └── lifecycle.md
├── 03-compliance/
│   ├── regulatory-matrix.md
│   ├── pmoc-rules.md
│   └── regulation-versioning.md
├── 04-product/
│   ├── modules.md
│   ├── user-stories.md
│   ├── use-cases.md
│   ├── workflows.md
│   └── permissions.md
├── 05-architecture/
│   ├── system-context.md
│   ├── container-architecture.md
│   ├── application-architecture.md
│   ├── infrastructure.md
│   ├── integrations.md
│   └── adr/
│       ├── ADR-001-backend.md
│       ├── ADR-002-database.md
│       ├── ADR-003-authentication.md
│       └── ADR-004-multitenancy.md
├── 06-database/
│   ├── conceptual-model.md
│   ├── logical-model.md
│   ├── data-dictionary.md
│   └── migrations.md
├── 07-api/
│   ├── api-guidelines.md
│   ├── authentication.md
│   ├── endpoints.md
│   ├── errors.md
│   └── openapi.yaml
├── 08-security/
│   ├── threat-model.md
│   ├── security-requirements.md
│   ├── lgpd.md
│   ├── audit.md
│   └── backup-recovery.md
├── 09-ui/
│   ├── design-system.md
│   ├── navigation.md
│   ├── screens.md
│   └── components.md
├── 10-devops/
│   ├── environments.md
│   ├── docker.md
│   ├── cicd.md
│   ├── observability.md
│   ├── backup.md
│   └── deployment.md
├── 11-testing/
│   ├── test-strategy.md
│   ├── acceptance-tests.md
│   └── integration-tests.md
├── 12-mobile/
│   ├── mobile-architecture.md
│   ├── offline-sync.md
│   └── qr-code.md
└── 13-ai/
    └── ai-development-guidelines.md
```

Isso vira a fonte de verdade do projeto.

---

## 16. Especialmente importante usando Opus + Claude Code + Codex

Eu não daria um prompt gigantesco diferente para cada IA.

O correto é:

```text
                     DOCUMENTAÇÃO
                         │
              ┌──────────┼──────────┐
              ▼          ▼          ▼
           OPUS      CLAUDE CODE    CODEX
        Arquitetura   Implementação  Implementação
```

Todos devem consultar a mesma documentação.

Além disso eu criaria na raiz:

- README.md
- AGENTS.md
- CLAUDE.md

### Regras para agentes

- ler /docs antes de modificar arquitetura
- não alterar schema sem migration
- não quebrar contratos da API
- todo endpoint necessita autorização
- respeitar tenant isolation
- não colocar regra normativa diretamente no código
- novas decisões arquiteturais exigem ADR
- novas funcionalidades exigem testes
- não armazenar secrets no repositório

Claude Code e Codex passam então a trabalhar sob as mesmas regras.

---

## 17. Divisão de responsabilidade entre as IAs

Eu utilizaria seu ambiente assim:

```text
COPILOT + OPUS
       │
       ├── análise de negócio
       ├── arquitetura
       ├── requisitos
       ├── modelagem
       ├── revisão arquitetural
       └── ADRs
               │
               ▼
        DOCUMENTAÇÃO
               │
        ┌──────┴──────┐
        ▼             ▼
 CLAUDE CODE       CODEX
        │             │
 implementação      revisão
 refactoring        implementação
 testes             testes
 arquitetura        diagnóstico
```

Mas nenhum deles deveria ter autoridade para espontaneamente mudar o desenho central.

A documentação versionada no Git é a autoridade.

---

## 18. MVP

Eu não tentaria construir tudo inicialmente.

### Fase 1 — Core

- Autenticação
- Multi-tenancy
- Usuários e permissões
- Clientes
- Unidades
- Ambientes
- Equipamentos

### Fase 2 — PMOC

- Templates
- Planos
- Atividades
- Periodicidades
- Responsável técnico
- Documentação

### Fase 3 — Operação

- Cronograma
- Ordens de serviço
- Checklists
- Execução
- Fotos
- Medições
- Não conformidades

### Fase 4 — Gestão

- Dashboard
- Relatórios
- Indicadores
- Exportação PDF
- Histórico
- Auditoria

Isso já seria um MVP comercial utilizável.

### Futuras fases

- Fase 5: PWA
- Fase 6: App Android/iOS, offline mode, QR Code, GPS, assinaturas, sincronização
- Fase 7: Integrações, IoT, sensores, telemetria, automação, IA, manutenção preditiva

---

## 19. Infraestrutura

Para uma primeira versão em produção:

```text
Internet
   │
Cloudflare / WAF
   │
Load Balancer / Reverse Proxy
   │
Application Containers
   │
   ├── frontend
   ├── API
   └── worker
        │
        ├── PostgreSQL
        ├── Redis
        └── Object Storage
```

### Ambientes

- DEV
- HML
- PRD

completamente separados.

### Requisitos mínimos de operação

- CI/CD
- migrations
- backups
- logs centralizados
- métricas
- tracing
- health checks
- secrets management
- TLS
- MFA para contas privilegiadas
- restore test
- monitoramento

---

## 20. O primeiro documento que devemos construir

Antes de pedir ao Opus para projetar o banco ou escrever código, eu faria um documento chamado:

### PMOC Software — Product & Engineering Master Specification

E nele consolidaria:

1. Contexto do negócio
2. Problema
3. Objetivos
4. Visão do produto
5. Stakeholders
6. Escopo
7. Fora de escopo
8. Personas
9. Terminologia
10. Requisitos funcionais
11. Requisitos não funcionais
12. Regras do negócio
13. Requisitos legais
14. Fluxos
15. Modelo de domínio
16. Módulos
17. Segurança
18. LGPD
19. Arquitetura
20. Banco
21. APIs
22. Front-end
23. Infraestrutura
24. Mobile futuro
25. Integrações
26. Observabilidade
27. Backup/DR
28. Testes
29. CI/CD
30. Roadmap
31. Critérios de aceite
32. ADRs

Esse será essencialmente o contrato técnico do projeto.

---

## Conclusão

Eu não chamaria internamente isso de simplesmente “Sistema para preencher PMOC”.

A arquitetura deveria nascer com algo mais próximo de:

> Plataforma de Gestão de Manutenção, Ativos e Conformidade para Sistemas de Climatização.

O PMOC é o primeiro e principal domínio.
