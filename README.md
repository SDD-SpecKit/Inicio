# Inicio
**Primeiros passos com SDD - Specify Drive Development**

A metodologia **Spec-Driven Development (SDD)**, ou Desenvolvimento Orientado por Especificações, é uma abordagem na qual **especificações estruturadas e detalhadas são escritas antes do código** e atuam como a **única fonte da verdade** para todo o ciclo de vida do software.

Diferente de práticas como o "vibe coding" ou abordagens *code-first*, no SDD a intenção do produto, regras de negócio, critérios de aceite e restrições técnicas são formalizadas documentalmente antes de qualquer implementação. Esse documento guia tanto **agentes de IA** quanto desenvolvedores humanos, assegurando que a geração de código seja previsível, rastreável e alinhada à arquitetura definida, reduzindo significativamente retrabalho e ambiguidades.

**Principais características do SDD:**

*   **Especificação Prévia:** Requisitos detalhados são criados e validados antes de escrever uma única linha de código de produção.
*   **Fonte Única da Verdade:** A especificação versionada torna-se o contrato central entre negócio, engenharia e ferramentas de IA.
*   **Foco em Intenção e Arquitetura:** Em vez de improvisar soluções, os desenvolvedores definem invariantes, fluxos e comportamentos esperados que devem ser estritamente seguidos.
*   **Integração com IA:** O SDD é frequentemente associado ao uso de agentes de IA, onde a especificação funciona como um *prompt* complexo e estruturado para gerar código executável e testes automatizados.
*   **Diferenças com TDD/BDD:** Enquanto o Test-Driven Development (TDD) foca em testes unitários técnicos e o Behavior-Driven Development (BDD) em cenários de negócio, o SDD foca na **definição completa da intenção e planejamento** que orquestra todo o processo, incluindo a própria geração do código.

**Três Níveis de Compromisso com a Spec**
Nível	Descrição
Spec-first	A spec é escrita antes e usada durante o desenvolvimento assistido por IA
Spec-anchored	A spec permanece viva após a entrega, guiando evolução e manutenção
Spec-as-source	A spec é o artefato principal; o humano edita apenas a spec, nunca o código diretamente

Workflow Completo (GitHub Spec Kit)
O fluxo canônico tem 6 fases, cada uma produzindo um artefato Markdown que alimenta a próxima:

/speckit.constitution — Define princípios inegociáveis do projeto (regras de teste, padrões de UX, governança).  Vira um constitution.md versionado.
/speckit.specify — Captura requisitos funcionais e não-funcionais, user stories priorizadas (P1 = MVP), critérios de aceite em formato Given-When-Then ou EARS.
/speckit.clarify — Resolve ambiguidades, dependências e edge cases.  Máximo de 3 perguntas de esclarecimento por spec.
/speckit.plan — Gera arquitetura, modelo de dados, contratos de API (OpenAPI/GraphQL), pesquisa técnica e identificação de riscos.  Inclui um Constitution Check automático. 
/speckit.tasks — Decompõe o plano em tarefas pequenas, autocontidas e ordenadas por dependência — cada uma implementável em uma única sessão de agente.
/speckit.implement — O agente de IA executa as tarefas seguindo test-first (red → green → refactor), validando contra os critérios de aceite. 
Exemplo prático do fluxo:

/speckit.specify "Sistema de chat em tempo real com histórico e presença"
  → Cria specs/003-chat-system/spec.md

/speckit.plan "WebSocket, PostgreSQL, Redis"
  → Gera plan.md, research.md, data-model.md, contracts/

/speckit.tasks
  → Gera tasks.md com T001, T002, ...

/speckit.implement
  → Executa cada tarefa, valida e reporta progresso

Estrutura de Arquivos Típica
specs/
  001-user-auth/
    spec.md          # Requisitos e user stories
    plan.md          # Arquitetura e decisões técnicas
    tasks.md         # Tarefas ordenadas (T001, T002, ...)
    research.md      # Comparativos técnicos
    data-model.md    # Entidades e relacionamentos
    contracts/       # OpenAPI, GraphQL, eventos
    quickstart.md    # Cenários de validação

**Ferramentas Principais**
Ferramenta	Foco

GitHub Spec Kit	Toolkit agnóstico, CLI + slash commands, 30+ agentes
AWS Kiro	IDE agêntica com SDD integrado nativamente
Tessl	SDD com trilhas de auditoria (indústrias reguladas)
OpenSpec	Abordagem leve e iterativa
BMAD-METHOD	Framework comunitário, multi-agente
Cursor Plan Mode	SDD dentro do IDE, com AGENTS.md
Claude Code + skills	Workflow terminal com menor fricção
