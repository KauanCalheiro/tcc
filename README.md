# Proposta de Projeto: Open-Source AI-Driven Test Automation Hub

### 1. Visão do Produto

Uma plataforma desktop **open-source**, **local-first** e **colaborativa por design**, projetada para democratizar e acelerar a automação de testes via BDD. A ferramenta atua como um orquestrador inteligente na máquina do desenvolvedor, alavancando o Git como fonte única de verdade para permitir colaboração de equipe, versionamento e integração com workflows de CI/CD existentes.

### 2. O Problema

A criação e manutenção de testes automatizados é lenta, propensa a erros e muitas vezes desconectada dos requisitos de negócio. Ferramentas atuais ou são SaaS (exigindo upload de código sensível para a nuvem) ou exigem configuração de ambientes excessivamente complexa.

**O Desafio dos Sistemas Legados:** A modernização e garantia de qualidade em sistemas legados é um desafio crítico. Esses sistemas frequentemente carecem de testes automatizados, tornando-os frágeis e arriscados para modificar. Esta ferramenta oferece um ponto de entrada de baixa fricção para introduzir testes BDD robustos, reduzindo os riscos na manutenção e evolução.

Falta uma solução que una a simplicidade da gravação visual com a robustez da engenharia de software (Page Objects, Clean Code), assistida por IA e focada em privacidade e funcionamento local.

### 3. Público-Alvo

Nosso público-alvo são profissionais técnicos que precisam automatizar testes, mas que podem não ser programadores especialistas. A ferramenta é desenhada para ser acessível o suficiente para que um QA manual possa começar a automatizar, e ao mesmo tempo poderosa o bastante para que um desenvolvedor experiente seja produtivo.

- **Engenheiros de QA (Automação e Manuais):** Que precisam transitar de testes manuais para automação robusta sem uma barreira técnica inicial alta.
- **Desenvolvedores de Software:** Que buscam integrar testes de aceitação no seu fluxo de desenvolvimento (TDD/BDD) de forma rápida.

---

### 4. Escopo Funcional Detalhado

#### Módulo A: Gestão de Projetos e Fluxos (Local & Git-based)

- **Arquitetura de Arquivos:** Leitura e escrita direta na estrutura de pastas do projeto local. Sincronização automática com Git para suportar múltiplos projetos e colaboração.
- **Gestão de Ambientes:** Configuração de variáves (Dev, Homolog, Prod) salvas localmente em arquivos `.env`, com suporte a criptografia.
   <!--
    VERIFICAR A POSSIBILIDADE CUCUMBER DE ISOLAR .FEATURE COM .JS MESMO QUE TENHAM O MESMO NOME
        * Guidance: Yes, this is standard in Cucumber.js. You configure glue code paths. Cucumber will scan all specified .js/.ts files and match step definitions to steps in any .feature file,
            regardless of file names. The key is to ensure your Gherkin steps are unique enough to avoid ambiguity. For example:
                * features/login/login.feature
                * features/login/steps.js
                * features/dashboard/dashboard.feature
                * features/dashboard/steps.js
            This works perfectly. Cucumber doesn't bind a .feature file to a single .js file.
    -->
- **Mapeamento de Page Objects:** Associação automática entre Steps Gherkin e métodos existentes no código local (JS/TS), respeitando o isolamento de escopo do Cucumber.js.
- **Organização:** Agrupamento lógico de `.feature` files, suítes e tags (`@smoke`, `@critical`).

#### Módulo B: Motor de Geração Híbrida de IA

- **Estratégia Híbrida (Core Feature):**
  - _Modo Online:_ Conexão via API (OpenAI/Claude) para raciocínio complexo e geração de cenários criativos.
  - _Modo Offline:_ Uso de LLMs locais (via Ollama ou similar) para privacidade total e funcionamento sem internet.
- **Gerador Contextual Gherkin:** Criação de cenários e tabelas de exemplos baseada no contexto do projeto (via RAG/Vector Store).
- **Conversor Visual Inteligente:** Transforma gravações de tela (cliques/screenshots) em passos semânticos ("Login" vs "Click #btn-22"), sugerindo a criação ou reutilização de Page Objects.
- **Gerador de Código (Snippet Engine):** Produz _Step Definitions_ seguindo padrões **Page Object Model**, incentivando a reutilização de código para evitar duplicação e garantir a manutenibilidade.

#### Módulo C: Execução e Monitoramento

- **Execução Local:** Runner integrado (foco em Cucumber.js) que roda processos Node.js locais. Suporte a Headless ou GUI para debug visual.
- **Relatórios e Debug:** Dashboard em tempo real, logs estruturados e captura de vídeo/screenshot em falhas.
- **Análise de Flaky Tests:** Identificação estatística de testes intermitentes.
- **Self-Healing (Roadmap):** Em uma versão futura, a IA poderá analisar o DOM em caso de falha de seletor e sugerir a correção do código automaticamente.

#### Módulos de Suporte (D, E, F)

- **Gestão de Dados:** Fábrica de dados sintéticos e mascaramento de dados sensíveis.
- **Extensibilidade:** API de Plugins para integrações (Slack, CI/CD, TestRail).
- **Analytics:** Métricas de cobertura e ROI da automação (tempo economizado).

---

### 5. Requisitos Técnicos e Arquitetura

**Arquitetura "Local-First" (Offline Capable)**
Para atender ao requisito de rodar localmente e manipular arquivos do usuário:

1.  **Frontend/Desktop Shell:**
    - **Electron** ou **Tauri**: Para criar uma aplicação desktop nativa com acesso ao _File System_ (FS) do usuário, permitindo a manipulação direta de arquivos do projeto (`.feature`, `.js/ts`).
    - **Integração com IDE:** Botão para "Abrir no VS Code" ou editor preferido.

2.  **Motor de IA (Camada de Abstração):**
    - Interface para provedores plugáveis, permitindo alternar entre LLMs locais (Ollama) para modo offline e APIs de nuvem (OpenAI, Anthropic) para modo online.

3.  **Banco de Dados (Metadados):**
    - **SQLite**: Para armazenar histórico de execuções, logs e configurações. É uma solução extremamente rápida e eficiente para este caso de uso local.

4.  **Vector Store Local (RAG):**
    - Uso de bibliotecas como **LanceDB** ou **ChromaDB** para criar um índice vetorial do código do projeto. Isso fornece o contexto necessário para a IA gerar código e testes coerentes.

---

### 6. Diferenciais Competitivos

1.  **Privacidade de Código:** Seu código nunca sai da sua máquina, a menos que você configure explicitamente uma IA de nuvem.
2.  **Sem Lock-in:** O output são arquivos padrão (Gherkin, JS/TS) que funcionam independentemente da ferramenta.
3.  **Performance:** Sem latência de rede para execução de testes ou para a interface do usuário.
4.  **Colaboração via Git:** A "verdade" do projeto reside nos arquivos versionados, facilitando Code Reviews e integração com workflows existentes.
5.  **Teste em Ambientes Restritos:** Suporta nativamente testes de aplicações em `localhost`, intranets ou atrás de firewalls corporativos, cenários impossíveis para a maioria das plataformas de nuvem.

---
