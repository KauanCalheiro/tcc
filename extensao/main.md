## **Extensão Chromium para Execução Supervisionada de Provas Online**

## **Problema**

Com o avanço do ensino remoto e híbrido, as avaliações online tornaram-se parte essencial do cotidiano acadêmico. No entanto, plataformas amplamente utilizadas como **Google Forms**, **Moodle** e **Microsoft Forms** carecem de mecanismos nativos que assegurem a **integridade e autenticidade** das provas.

Hoje, professores enfrentam limitações sérias: não há controle sobre **mudança de abas**, **copiar e colar**, **acesso a outros sites**, ou **uso de atalhos**. Isso compromete a equidade e a confiabilidade dos resultados obtidos.

Soluções comerciais existem, mas são **caras, restritas a certos sistemas operacionais** ou **pouco transparentes**, inviabilizando sua adoção em contextos acadêmicos diversos, especialmente em instituições públicas ou ambientes heterogêneos.

## **Soluções Existentes**

Algumas ferramentas de mercado tentam mitigar o problema:

- **Safe Exam Browser (SEB):** cria um ambiente bloqueado, mas exige instalação e configuração complexas.
- **Respondus LockDown Browser:** solução robusta, porém paga e restrita a Windows/macOS.
- **Google Chromebook Lock Mode:** eficiente, mas exclusivo do ecossistema Google.
- **Extensões simples de monitoramento:** detectam trocas de abas, mas sem relatórios, histórico ou centralização de dados.

## **Limitações Identificadas**

- **Dependência de hardware ou SO específico** (como Chromebooks ou Windows).
- **Custo de licenciamento** inviável para instituições públicas.
- **Ausência de integração com plataformas amplamente utilizadas.**
- **Falta de transparência:** logs inacessíveis ou enviados a servidores de terceiros.
- **Falta de flexibilidade:** regras rígidas e pouco configuráveis.
- **Experiência do aluno comprometida** por soluções excessivamente restritivas.

## **Proposta do Projeto**

O projeto propõe o desenvolvimento de uma **extensão Chromium multiplataforma** voltada à **execução supervisionada de provas online**, com base em um modelo **self-hosted, transparente e acessível**.

A arquitetura é composta por três elementos:

1. **Painel do Professor:** para criação da sala, configuração das regras de monitoramento e acompanhamento dos alunos.
2. **Extensão do Aluno:** executa o monitoramento local, registra eventos e interage com o servidor.
3. **Servidor Self-Hosted:** hospedado pela instituição ou professor, responsável por armazenar logs e gerar relatórios de integridade sem depender de serviços externos.

### **Fluxo Operacional**

1. **Criação da Sala:**
   O professor acessa o painel, define regras de monitoramento (por exemplo: detectar trocas de aba, copiar/colar, inspeção de código, inatividade) e, opcionalmente, carrega um **template de configuração** já salvo.
   Após salvar, o sistema gera um **código da sala**, e o professor compartilha com os alunos o **código e o DNS/IP do servidor**.

2. **Entrada do Aluno:**
   O aluno abre o navegador com a extensão instalada e informa:

   - **E-mail institucional** (identificação);
   - **Código da sala**;
   - **DNS/IP do servidor** (fornecido pelo professor).

   A extensão valida as informações com o servidor, solicita permissão para a gravação de tela e aguarda o início da sessão.

3. **Início da Prova:**
   Quando o professor inicia a sala, todos os alunos conectados recebem uma notificação automática com a **mensagem inicial** (que pode incluir o **link da prova**).
   A partir desse momento, o monitoramento é ativado, e o cronômetro de prova (se configurado) é sincronizado entre todos os participantes.

4. **Monitoramento em Tempo Real:**
   Durante a prova, a extensão monitora continuamente:

   - Trocas de aba e perda de foco da janela;
   - Tentativas de abrir DevTools/inspecionar código;
   - Uso de atalhos suspeitos (Ctrl+C, Ctrl+V, Alt+Tab);
   - Longos períodos de inatividade;
   - Mudança de URL fora do domínio autorizado.

   Cada evento gera um log com **timestamp, tipo e gravidade**.

5. **Gravação Sob Suspeita:**
   A função de **gravação de tela** é **ativada somente em eventos suspeitos** e **apenas com consentimento do aluno**.
   Trechos curtos da tela são capturados, comprimidos localmente e enviados ao servidor de forma segura.
   Caso o aluno recuse a permissão, o sistema registra a recusa no relatório.
   Apenas o professor (ou administrador da sala) tem acesso às capturas.

6. **Sincronização e Encerramento:**
   Durante a prova, pequenos pacotes de logs são enviados periodicamente ao servidor (**sincronização incremental**).
   Ao encerrar, tanto o aluno quanto o professor disparam uma **sincronização final**.
   O servidor compila os dados e gera o **relatório de integridade**, que é exibido no painel do professor e pode ser enviado por e-mail.

## **Objetivos do Projeto**

- Desenvolver uma **extensão Chromium multiplataforma** (Windows, Linux, macOS).
- Implementar um **modelo self-hosted**, garantindo **transparência e controle total**.
- Permitir **criação e monitoramento de salas de prova** sem necessidade de cadastro prévio de alunos.
- Oferecer **notificações e mensagens sincronizadas** entre professor e alunos.
- Monitorar eventos relevantes de comportamento e registrar **indicadores de foco e suspeita**.
- Gerar **relatórios automáticos de integridade**, vinculados à sessão de cada aluno.
- Oferecer uma solução leve, acessível e aberta à comunidade acadêmica.

## **Escopo Previsto**

### **Painel do Professor**

- Criação e encerramento de salas de prova.
- Definição e salvamento de templates de monitoramento.
- Envio de mensagens aos alunos (incluindo o link da prova).
- Visualização em tempo real dos alunos conectados.
- Acesso aos relatórios e gravações de tela.

### **Extensão do Aluno**

- Entrada via e-mail, código e IP/DNS do servidor.
- Monitoramento passivo e gravação sob suspeita (com consentimento).
- Envio incremental de logs ao servidor.
- Encerramento automático e sincronização final.

### **Servidor Self-Hosted**

- API REST para controle de salas, logs e eventos.
- Armazenamento seguro e criptografado.
- Geração automática de relatórios.
- Interface web transparente e auditável.

## **Conclusão**

A proposta busca conciliar **segurança, leveza e transparência** no contexto das avaliações online.
Com um modelo self-hosted e extensão multiplataforma, o sistema evita dependência de soluções proprietárias e garante **autonomia total à instituição**.

A extensão visa equilibrar **integridade acadêmica e respeito à privacidade**, capturando apenas o necessário para assegurar a confiabilidade das avaliações.

Além de gratuito e aberto à comunidade, o projeto promove uma visão **ética e transparente** da supervisão digital em que professores, alunos e instituições compartilham o mesmo acesso às informações e relatórios de forma justa e auditável.
