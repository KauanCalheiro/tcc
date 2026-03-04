# Acutis: Hub Local-first de Testes Automatizados com Ênfase em Documentação

### 1. Visão do Produto

Uma plataforma desktop **open-source**, **local-first** e **colaborativa por design**, projetada para democratizar e acelerar a automação de testes por meio de BDD, tendo a **documentação** como elemento central do processo.

A ferramenta atua como um orquestrador inteligente na máquina local, alavancando o Git como fonte única de verdade para permitir versionamento, rastreabilidade, colaboração em equipe e integração com workflows de CI/CD já existentes.

Mais do que apenas executar testes, a plataforma transforma especificações de comportamento em ativos versionados que funcionam simultaneamente como suíte de validação automatizada e como documentação técnica sincronizada com o código real. Dessa forma, reduz-se a fragmentação entre requisito, implementação e validação, promovendo maior transparência, previsibilidade e alinhamento entre áreas técnicas e de negócio.

### 2. Os Problemas

A criação e manutenção de testes automatizados permanece como um desafio estrutural no desenvolvimento de software contemporâneo. O processo é frequentemente lento, suscetível a falhas e desalinhado dos requisitos de negócio. As soluções disponíveis no mercado, em sua maioria, impõem um trade-off entre acessibilidade técnica e privacidade de dados, ou entre custo e capacidade de integração ao ecossistema já existente.

Os problemas identificados não são isolados: eles se inter-relacionam e se retroalimentam, contribuindo para um ciclo de baixa maturidade em qualidade de software, aumento de risco operacional e elevação do custo de manutenção. A seguir, apresentam-se três macroproblemas interdependentes que estruturam essa análise.

---

#### 2.1 Barreiras Técnicas e Déficit de Documentação

A automação de testes demanda conhecimento especializado em frameworks, linguagens de programação, padrões arquiteturais (como Page Object Model) e técnicas de identificação e manipulação de elementos de interface. Para equipes que não dispõem de profissionais dedicados à automação, esse conjunto de pré-requisitos eleva significativamente o custo de entrada e dificulta a adoção sistemática de testes automatizados.

Como consequência, testes manuais repetitivos tendem a substituir a automação, resultando em ciclos de entrega mais longos, maior incidência de regressões e menor previsibilidade na evolução do sistema. O impacto organizacional manifesta-se na redução da confiança no software entregue e no aumento do retrabalho.

Esse cenário é particularmente crítico em sistemas legados, que frequentemente carecem de cobertura automatizada. A ausência de testes torna tais sistemas frágeis e de alto risco para modificação, dificultando iniciativas de modernização e ampliando o custo da manutenção evolutiva. Cada alteração passa a representar uma incerteza quanto à integridade do comportamento previamente implementado.

Paralelamente, a documentação técnica é, em muitos contextos, tratada como artefato secundário: produzida pontualmente e rapidamente desatualizada. A falta de sincronização entre documentação e código gera descontinuidade informacional, exige reconstrução constante de conhecimento sobre fluxos existentes e dificulta o onboarding de novos membros. Esse desalinhamento constitui um fator relevante de retrabalho e falhas de comunicação entre áreas técnicas e de negócio.

Nesse contexto, abordagens como Behavior-Driven Development (BDD) apresentam-se como alternativa estruturante, ao posicionar a especificação de comportamento, descrita em linguagem Gherkin, como elemento central do processo. Ao servir simultaneamente como documentação executável e como suíte de testes, o BDD contribui para reduzir a fragmentação entre especificação, implementação e validação.

---

#### 2.2 Custo, Privacidade e Dependência de Plataformas SaaS

Grande parte das plataformas modernas de automação de testes adota o modelo Software as a Service (SaaS). Embora ofereçam facilidade inicial de uso, essas soluções impõem um dilema relevante: custos recorrentes potencialmente elevados ou a necessidade de tornar a aplicação sob teste acessível externamente.

Esse modelo pode implicar exposição, direta ou indireta, de sistemas internos, dados sensíveis e ambientes corporativos à infraestrutura de terceiros. Para organizações sujeitas a restrições orçamentárias, políticas rigorosas de segurança da informação, requisitos de compliance ou isolamento de rede, tal abordagem torna-se inviável ou incompatível com suas diretrizes institucionais.

A problemática se intensifica com a incorporação de inteligência artificial às ferramentas de automação. Muitas soluções baseadas em IA são proprietárias e fechadas, impondo o uso exclusivo do modelo de linguagem escolhido pelo fornecedor, sem possibilidade de substituição ou customização. Esse cenário limita a autonomia tecnológica das equipes e cria dependência estrutural de fornecedor (_vendor lock-in_).

Organizações que já realizaram investimentos em infraestrutura própria de IA, que necessitam utilizar modelos locais ou que estão sujeitas a requisitos regulatórios específicos quanto ao tratamento de dados não encontram alternativas compatíveis no ecossistema predominante. A obrigatoriedade de envio de código sensível e contexto de negócio a provedores externos eleva riscos relacionados à propriedade intelectual, confidencialidade e conformidade normativa.

---

#### 2.3 Integração Deficiente com Pipelines de CI/CD

A integração entre ferramentas de automação de testes e pipelines de integração e entrega contínua (CI/CD) constitui outro ponto crítico. Soluções baseadas em nuvem frequentemente oferecem integrações limitadas ou excessivamente complexas com ferramentas consolidadas, como Jenkins, GitLab CI e GitHub Actions.

Na prática, equipes acabam desenvolvendo scripts customizados e mecanismos de orquestração paralelos para viabilizar a execução de testes no pipeline. Essa fragmentação gera aumento da complexidade operacional, dificuldade de manutenção e redução da rastreabilidade das execuções.

Para organizações que já investiram na consolidação de sua infraestrutura de DevOps, a ausência de integração nativa representa um desalinhamento arquitetural que eleva o custo de adoção de novas ferramentas e compromete o retorno sobre investimentos previamente realizados. Além disso, soluções improvisadas tendem a comprometer a confiabilidade, a escalabilidade e a visibilidade do processo de garantia de qualidade.

---

Em conjunto, esses três macroproblemas evidenciam uma lacuna estrutural no ecossistema atual de automação de testes: a ausência de uma solução que concilie baixa barreira técnica, documentação sincronizada, execução local com preservação de privacidade, flexibilidade no uso de modelos de IA e integração nativa ao fluxo de entrega contínua. Essa lacuna fundamenta a motivação para a proposta apresentada neste trabalho.

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
