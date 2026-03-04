# Proposta de Projeto: Open-Source AI-Driven Test Automation Hub

### 1. Visão do Produto

Uma plataforma desktop **open-source**, **local-first** e **colaborativa por design**, projetada para democratizar e acelerar a automação de testes via BDD. A ferramenta atua como um orquestrador inteligente na máquina do desenvolvedor, alavancando o Git como fonte única de verdade para permitir colaboração de equipe, versionamento e integração com workflows de CI/CD existentes.

### 2. Os Problemas

A criação e manutenção de testes automatizados é lenta, propensa a erros e muitas vezes desconectada dos requisitos de negócio. Ferramentas atuais ou são SaaS (exigindo upload de código sensível para a nuvem) ou exigem configuração de ambientes excessivamente complexos e manuais.

**O Desafio dos Sistemas Legados:** A modernização e garantia de qualidade em sistemas legados é um desafio crítico. Esses sistemas frequentemente carecem de testes automatizados, tornando-os frágeis e arriscados para modificar. Esta ferramenta oferece um ponto de entrada de baixa fricção para introduzir testes BDD robustos, reduzindo os riscos na manutenção e evolução.

**Documentação Defasada:** A documentação de sistemas é frequentemente tratada como um artefato secundário, criada uma vez e rapidamente desatualizada. Equipes perdem tempo reconstruindo o entendimento de fluxos que já foram implementados, e novos membros não têm acesso a uma visão clara e confiável do comportamento esperado do sistema. A ausência de documentação sincronizada com o código real é um dos principais vetores de retrabalho e falhas de comunicação entre times técnicos e de negócio.

**Barreira Técnica na Criação de Testes:** A criação de testes automatizados de forma manual exige um nível de especialização técnica elevado, conhecimento de frameworks, linguagens de programação, padrões como Page Object Model e domínio de ferramentas de seleção de elementos. Para equipes sem um especialista dedicado em automação, o processo é lento, propenso a erros e frequentemente abandonado em favor de testes manuais repetitivos, resultando em ciclos de entrega mais lentos e menor confiança no software entregue.

**Custo e Exposição de Dados em Ferramentas SaaS:** As plataformas de automação baseadas em nuvem impõem um dilema crítico: ou o custo de licenciamento é proibitivo para equipes menores, ou o modelo de execução exige que a aplicação sob teste seja acessível externamente, expondo, de forma implícita ou explícita, sistemas internos, dados sensíveis e ambientes corporativos a terceiros. Para times que operam com orçamento reduzido ou que possuem restrições de segurança, compliance e isolamento de rede, essas soluções simplesmente não são uma opção viável.

**Falta de Acesso Democrático a IA na Automação:** As ferramentas que integram IA para automação de testes são frequentemente proprietárias e fechadas, oferecendo apenas o modelo de IA escolhido pelo fornecedor, sem possibilidade de customização ou troca. Equipes que desejam usar seu próprio modelo (LLM local, API própria ou provedor específico) não têm opção viável. Isso cria dependência de terceiros, dificulta a privacidade corporativa e impede que organizações aproveitem investimentos já realizados em infraestrutura de IA ou que tenham requisitos regulatórios específicos de onde e como os modelos de IA são executados. Além disso, a falta de suporte para modelos locais força as empresas a enviarem código sensível e contexto de negócio para provedores externos, criando riscos de vazamento de propriedade intelectual e violação de políticas de compliance.

**Falta de Integração com Pipelines de CI/CD:** As soluções de automação de testes, especialmente plataformas SaaS, frequentemente oferecem integrações limitadas ou complexas com ferramentas de CI/CD consolidadas (Jenkins, GitLab CI, GitHub Actions). Isso força equipes a criar scripts customizados, manuais e frágeis para orquestrar a execução de testes, resultando em workflows desconectados, dificuldade de manutenção e perda de visibilidade sobre o status dos testes no pipeline. Para times que já investiram em infraestrutura de automação, essa falta de integração nativa torna a adoção de novas soluções custosa e impraticável.

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
