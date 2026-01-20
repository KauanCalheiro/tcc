# **Justificativa do Projeto de TCC — Sistema para Gestão da Academia da Univates**

## Problema

A gestão atual da academia da Univates é majoritariamente manual: controle de presença realizado por funcionários e treinos registrados em papel. Esse processo gera falhas (entradas não registradas), perda de dados, dificuldade no acompanhamento do progresso dos alunos e desperdício de recursos.

Propõe-se desenvolver um sistema informatizado, acessível e seguro, para controlar presenças, agendar treinos, registrar a evolução dos alunos e integrar-se aos sistemas internos do complexo esportivo. O objetivo é aumentar a eficiência operacional, melhorar a experiência de alunos e instrutores e agregar valor ao serviço oferecido pela academia.

---

## Soluções Existentes

Existem diversos sistemas de gestão de academias no mercado; contudo, a maioria é paga e pode não compensar o custo para a realidade da Univates.

(Será realizada pesquisa detalhada sobre soluções disponíveis — funcionalidades, custos e adequação ao contexto universitário.)

---

## Limitações Identificadas

(Será realizada pesquisa detalhada sobre limitações das soluções comerciais e lacunas específicas do contexto da Univates — ex.: integração com sistemas internos, custo, usabilidade mobile, privacidade de dados.)

---

## Proposta do Projeto

O projeto propõe o desenvolvimento de um **sistema informatizado para a gestão da academia da Univates**, com foco em **mobilidade, praticidade e integração**. A solução permitirá o controle de presenças, o agendamento de treinos, o registro do progresso dos alunos e a comunicação direta entre alunos e instrutores, tudo em um ambiente digital unificado.

O sistema deverá ser **intuitivo, responsivo e seguro**, atendendo tanto a alunos quanto a instrutores e administradores. A seguir, são apresentadas as principais funcionalidades previstas:

* **Autenticação e perfis de usuário:** acesso individualizado para alunos, instrutores, personals e administradores, com permissões específicas conforme o perfil.
* **Controle de presenças:** registro automático de entrada na academia por meio de QR Code (infraestrutura já existente) ou confirmação direta via aplicativo/web. O sistema também poderá validar a presença com base na localização do usuário (GPS opcional, respeitando a privacidade).
* **Agendamento de treinos:** os alunos poderão agendar seus treinos de acordo com horários e modalidades disponíveis, podendo optar por sessões com personal trainer quando aplicável.
* **Registro de treinos e acompanhamento:** funcionalidade para registrar detalhes dos exercícios realizados (séries, repetições, carga, medidas e observações), possibilitando o acompanhamento do histórico e da evolução dos alunos.
* **Chamar um Personal / Atendimento Imediato:** o sistema contará com um botão de **chamada rápida de atendimento**, permitindo que o aluno solicite ajuda diretamente de um instrutor ou atendente. Assim que acionado, o pedido será exibido em tempo real na tela do personal (via **WebSocket** ou tecnologia equivalente), indicando o aluno solicitante. O atendente poderá então deslocar-se até o local para prestar o suporte necessário, agilizando o atendimento e melhorando a experiência do usuário.
* **Relatórios e estatísticas:** geração de relatórios e gráficos com dados sobre frequência, tipos de treino mais realizados e progresso dos alunos, com opção de exportação em PDF ou CSV.
* **Integração com sistemas internos:** comunicação direta com o sistema do complexo esportivo para verificação de matrículas e pagamentos, garantindo a consistência dos dados e simplificando os processos administrativos.
* **Notificações e comunicações:** envio de lembretes automáticos, confirmações de agendamentos e avisos importantes via push, e-mail ou SMS.
* **Interface mobile-first:** desenvolvimento voltado para dispositivos móveis, proporcionando uma experiência fluida e otimizada para alunos que utilizam o sistema durante os treinos.
* **Sistema de feedback:** canal interno para sugestões, reclamações e avaliação do atendimento, permitindo que a academia colete percepções e melhore continuamente seus serviços.
* **Gestão operacional:** definição de horários de funcionamento da academia, registro de feriados, dias especiais e controle de disponibilidade de instrutores e personals.
* **Documentação e suporte:** o sistema incluirá manuais técnicos e guias de utilização para usuários e equipe administrativa, garantindo autonomia no uso e manutenção da plataforma.

---

## Objetivos

Melhorar a eficiência da gestão da academia da Univates, proporcionar uma melhor experiência para alunos e instrutores, facilitar o controle de presenças, agendamento de treinos e acompanhamento do progresso dos alunos, promovendo um ambiente mais organizado e produtivo. No processo, busca-se agregar valor ao serviço prestado e fortalecer a inovação tecnológica dentro da instituição.

---

## Escopo Previsto

1. **Autenticação e gestão de usuários** (cadastro, login, papéis e permissões).
2. **Módulo de controle de presença** (QR Code e check-in via web/app).
3. **Agendamento de treinos** (reserva de horários e modalidades).
4. **Registro e acompanhamento de treinos** (histórico individual e por aluno).
5. **Módulo “Chamar um Personal”** (solicitação em tempo real, notificação via WebSocket e registro de atendimento).
6. **Painel administrativo** (visualização de presenças, agendamentos e atendimentos).
7. **Relatórios e estatísticas** (frequência, adesão e progresso).
8. **Integração com o sistema do complexo esportivo** (dados de matrícula e pagamento).
9. **Notificações automáticas** (confirmações, lembretes e comunicados).
10. **Sistema de feedback** (avaliações e sugestões dos usuários).
11. **Documentação técnica e manual de uso** (para alunos, instrutores e administradores).
