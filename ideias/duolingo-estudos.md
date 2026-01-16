# 📱 Nome de Código: "ClassSync" (Nome Provisório)
**Visão:** Uma plataforma de microlearning social que utiliza IA para transformar materiais universitários em percursos gamificados, combatendo a procrastinação através de pressão social positiva (streaks de turma) e adaptação temporal.

---

## 1. Módulos Funcionais (O que o App faz)

### Módulo 1: Ingestão de Conteúdo e IA (O "Cérebro")
* **Upload de Materiais:** Suporte a arquivos PDF, DOCX e PPTX.
* **Processamento OCR:** Leitura de textos em imagens (para slides fotografados ou digitalizações antigas).
* **Geração Generativa (GenAI):** A IA analisa o documento e gera automaticamente:
    * Flashcards (Termo vs. Definição).
    * Quizzes de Múltipla Escolha (com explicação do erro).
    * Resumos em Tópicos (Bullet points).
    * Estimativa de tempo de leitura.
* **Curadoria Colaborativa:** Alunos podem editar/corrigir perguntas geradas pela IA e dar "upvote" nos melhores resumos.

### Módulo 2: O Motor de Estudo (A "Interface")
* **Seletor de Tempo (Time Slider):**
    * Entrada do usuário: "Tenho [5] [15] [30] [60] minutos".
    * Lógica: O algoritmo seleciona o conteúdo mais prioritário que cabe nesse intervalo.
* **Modo "Foco Rápido" (5-10 min):** Apenas Flashcards e 1 Pergunta de Quiz.
* **Modo "Sessão Profunda" (30+ min):** Leitura de resumo + Bateria de Exercícios + Revisão de erros passados.
* **Spaced Repetition System (SRS):** Algoritmo que traz de volta perguntas que o aluno errou há 2 dias, garantindo a memorização.

### Módulo 3: Gamificação e Social (O "Coração")
* **Estrutura de Turmas:**
    * Criação de turma por código/link convite.
    * Feed da Turma (Log de atividades: *"João acabou de estudar Anatomia"*).
* **Sistema de Streaks (Dupla Camada):**
    * 🔥 **Streak Pessoal:** Dias seguidos que o usuário estudou.
    * 🛡️ **Streak da Turma (Class Shield):** Dias seguidos em que *pelo menos X%* da turma atingiu a meta diária. Se a turma falhar, todos perdem bónus (pressão social).
* **Ranking/Leaderboard:** Quem contribuiu com mais arquivos e quem tem mais XP na semana.

### Módulo 4: Gestão e Planeamento (O "Organizador")
* **Input de Datas:** O aluno (ou admin da turma) insere a data da Prova/Entrega.
* **Algoritmo de Cálculo Reverso:**
    * O sistema calcula o volume total de conteúdo vs. dias restantes.
    * Define a "Meta Diária Dinâmica" (ex: "Hoje precisas de 20 min para chegar à prova tranquilo").
* **Notificações Inteligentes:** Push notifications baseadas na urgência ("A turma toda já estudou hoje, só faltas tu!").

---

## 2. Perfis de Usuário (Personas)

1.  **O Estudante Padrão:** Consome conteúdo, usa o seletor de tempo, quer manter o streak.
2.  **O "Escriba" (Criador):** O aluno organizado que faz upload dos PDFs e organiza os tópicos (ganha XP extra e badges de perfil).
3.  **O Moderador:** Pode remover arquivos duplicados ou incorretos da turma.

---

## 3. Requisitos Técnicos (Como será construído)

### Frontend (App Mobile)
* **Tecnologia:** Flutter ou React Native (para sair em iOS e Android simultaneamente).
* **UX/UI:** Interface minimalista, "Dark Mode" nativo (estudantes usam muito à noite), animações de feedback (confetti ao acertar perguntas).

### Backend & API
* **Linguagem:** Python (Django ou FastAPI) ou Node.js.
* **Integração IA:** OpenAI API (GPT-4o mini) ou Anthropic (Claude 3 Haiku) para custo-benefício e velocidade.
* **Vector Database:** Pinecone ou Weaviate (para permitir que a IA "leia" PDFs gigantes sem alucinar).

### Banco de Dados
* **Relacional (PostgreSQL):** Para dados de usuários, turmas, notas e streaks.
* **Armazenamento de Arquivos:** AWS S3 ou Google Cloud Storage (para guardar os PDFs originais).

---

## 4. Roteiro de Desenvolvimento (Roadmap MVP)

Para não tentar fazer tudo de uma vez, divide-se em fases:

### Fase 1: MVP (Mínimo Produto Viável) - 2 a 3 meses
* Login e Criação de Perfil.
* Criação de Turma (Básica).
* Upload de PDF e Geração automática de Quizzes (IA).
* Modo de estudo padrão (sem seletor de tempo complexo).
* Streak Individual.

### Fase 2: Social & Retenção - +2 meses
* Streak de Turma (A "Killer Feature").
* Ranking e Feed de atividades.
* Seletor de Tempo Inteligente ("Tenho X minutos").

### Fase 3: Inteligência de Prazos - +2 meses
* Calendário de Provas.
* Cálculo reverso de estudo.
* Algoritmo de Repetição Espaçada refinado.

---

## 5. Modelo de Negócio (Sugestão)

* **Freemium:**
    * *Grátis:* Entrar em turmas, estudar ilimitado, upload limitado (ex: 3 PDFs/semana), IA padrão.
    * *Premium (Assinatura Mensal):* Uploads ilimitados, IA mais rápida/precisa, Estatísticas avançadas de desempenho, "Congelador de Streak" (ferramenta para recuperar dias perdidos).
