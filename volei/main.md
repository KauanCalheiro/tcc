# **Justificativa do Projeto de TCC – Sistema de Gerenciamento de Campeonatos de Vôlei**

## Problema

O gerenciamento de campeonatos de voleibol ainda enfrenta desafios significativos, especialmente em **ligas amadoras, torneios universitários e campeonatos locais** organizados por clubes ou entidades comunitárias. Apesar do surgimento de plataformas digitais voltadas ao esporte, muitas soluções apresentam limitações que impactam diretamente a experiência de organizadores, atletas e público.

## Soluções Existentes

Entre as soluções existentes, destacam-se:

1. **VS Score** – aplicativo móvel voltado ao registro de partidas e placares. Embora eficiente para controle local, seu gerenciamento é **offline**, sem suporte a multi-idiomas ou acompanhamento público em tempo real, o que limita o uso em torneios maiores e em contextos internacionais.
2. **Competize** – plataforma web e mobile voltada à organização de torneios e acompanhamento de placares em tempo real. Apesar de oferecer resultados online e algumas estatísticas, trata-se de um sistema **exclusivamente pago e proprietário**, voltado ao controle administrativo de competições. Não contempla o **gerenciamento técnico da partida em si**, como **rotação, substituições, entrada e saída de líbero, tempos e sanções**.
3. **Playinga** – sistema de gerenciamento completo para torneios, com atualização de resultados em tempo real e sites personalizados para ligas. Contudo, também é um **serviço pago e fechado**, com foco na **divulgação de resultados**, não no **acompanhamento técnico detalhado da dinâmica da partida**.

## Limitações Identificadas

Essas limitações geram algumas “dores” importantes:

* **Ausência de acompanhamento técnico em tempo real**, dificultando o registro preciso de eventos de jogo, escalações e situações de quadra.
* **Falta de atualização pública imediata**, impedindo que espectadores acompanhem partidas ao vivo fora dos aplicativos oficiais.
* **Ausência de sistema open-source**, que permita personalização e adoção livre por clubes e ligas menores.
* **Modelos comerciais inacessíveis para entidades locais**, que muitas vezes não possuem recursos financeiros para plataformas pagas.

<!-- Diante desse cenário, o presente projeto propõe o desenvolvimento de um **sistema open-source de gerenciamento de campeonatos de voleibol**, voltado principalmente a **entidades e organizações locais** que desejam estruturar e modernizar seus torneios sem custos adicionais. -->

## Proposta do Projeto

O sistema terá foco em:

* **Atualização ao vivo via WebSocket**, permitindo um modo público de exibição em tempo real para qualquer dispositivo.
* **Gerenciamento técnico da partida**, incluindo **rotação, substituições, entrada e saída de líbero, pedidos de tempo e sanções**.
* **Estatísticas definidas e acessíveis** para organizadores e público.
* **Histórico completo de torneios e rankings transparentes**, promovendo o acompanhamento contínuo de equipes e atletas.
* **Suporte a múltiplos idiomas, incluindo PT-BR**, ampliando o alcance e a inclusão da plataforma.

## Objetivos do Projeto

Com isso, o projeto busca **democratizar o acesso a ferramentas de gestão esportiva**, contribuindo para a **melhoria da organização, da transparência e da experiência dos espectadores**. Além disso, pretende **estimular o crescimento e a difusão dos campeonatos locais de vôlei**, fortalecendo o cenário esportivo regional e incentivando o engajamento das comunidades envolvidas.

Com a funcionalidade de suporte a múltiplos idiomas, o sistema permite **expansão para outras entidades menores**, com traduções colaborativas proporcionadas pela natureza **open-source** do projeto. Dessa forma, equipes ou organizações especializadas podem **adotar o projeto, realizar forks e adaptá-lo a diferentes realidades regionais**, ampliando o alcance e a utilidade da plataforma.


## **Escopo Previsto**

O escopo inicial do projeto inclui:

1. **Cadastro de Usuários**: Permitir o registro e autenticação de organizadores, atletas e espectadores.
2. **Cadastro de Jogadores (extensão e usuário)**: Criação e gerenciamento de perfis de jogadores, incluindo estatísticas individuais.
3. **Cadastro de Times**: Criação e gerenciamento de equipes, incluindo informações de jogadores e técnicos.
4. **Gerenciamento de Campeonatos**: Criação, edição e exclusão de campeonatos, incluindo cadastro de equipes, jogadores e partidas. Permite a **inclusão do regulamento/documento oficial** e definição de regras básicas da competição.
5. **Check-in de times e jogadores**: Confirmação de presença antes das partidas.
6. **Gerenciamento de Partidas Individuais**: Controle detalhado de cada partida, incluindo sets, pontuação, tempos pedidos, substituições e rotação de jogadores.
7. **Controle de Sanções e Advertências**: Registro de cartões, faltas técnicas e suspensões, refletindo no histórico e estatísticas.
8. **Acompanhamento em Tempo Real**: Atualização instantânea de placares, sets e estatísticas durante as partidas via WebSockets.
9. **Modo de Exibição Pública**: Interface dedicada para espectadores acompanharem partidas ao vivo, com suporte a múltiplos dispositivos.
10. **Chaveamento e Tabelas**: Montagem automática de tabelas e classificação com base nos resultados das partidas.
11. **Estatísticas Detalhadas**: Registro e exibição de dados de desempenho individual e coletivo, como aces, bloqueios, erros e eficiência por set.
12. **Geração de Súmula e Relatórios de Partidas**: Criação de súmula detalhada de cada jogo e relatórios com resultados, estatísticas e desempenho das equipes.
13. **Relatório Geral do Campeonato**: Geração de relatório completo do torneio, incluindo desempenho de equipes e jogadores, bem como **quantidade de pessoas que acompanharam os jogos via ferramenta**.
14. **Sistema de notificações**: Alertas para eventos importantes, como início de partidas, resultados e atualizações de estatísticas (WebPush e/ou WhatsApp via API oficial).
15. **Suporte a Múltiplos Idiomas**: Implementação de sistema de internacionalização (i18n) para suportar diferentes idiomas (concepção em PT-BR com possibilidade de expansão para outros idiomas).
16. **Controle de Perfis e Permissões**: Definição de diferentes níveis de acesso (organizador, técnico, árbitro, espectador).
17. **Sistema Open-Source**: Disponibilização do código-fonte em plataforma pública (como GitHub), permitindo personalização e contribuições da comunidade.
18. **Sistema de Feedback e Colaboração**: Possibilidade de usuários sugerirem melhorias ou reportarem erros, especialmente importante em software open-source.
19. **Documentação Completa**: Criação de documentação técnica e de usuário para facilitar a adoção e utilização do sistema.
20. **Interface Responsiva**: Design adaptável para diferentes dispositivos, garantindo acessibilidade.
