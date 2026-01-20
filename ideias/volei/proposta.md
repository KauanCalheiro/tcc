# **Justificativa do Projeto de TCC - Sistema de Gerenciamento de Campeonatos de Vôlei**

## Problema

O gerenciamento de campeonatos de voleibol ainda apresenta **lacunas entre a organização administrativa e o acompanhamento técnico das partidas**, especialmente em **ligas amadoras, torneios universitários e campeonatos locais**.

Apesar da existência de plataformas digitais, a maioria foca apenas em **tabelas, resultados e divulgação**, deixando de lado aspectos fundamentais como **rotação, substituições, controle de líbero, pedidos de tempo e registro de estatísticas em tempo real**.

Além disso, muitas dessas soluções são **pagas e proprietárias**, o que limita o acesso de **clubes e entidades menores** que buscam estruturar seus torneios de forma moderna, transparente e acessível.

## Soluções Existentes

1. **VS Score** - app móvel para registro de partidas e placares. Funciona majoritariamente **offline**, sem suporte a múltiplos idiomas ou exibição pública em tempo real.
2. **Competize** - plataforma web/mobile com placares online e estatísticas. É **exclusivamente pago e proprietário**; foca no controle de resultados, mas não cobre o **gerenciamento técnico da partida** (rotação, substituições, líbero, tempos, sanções).
3. **Playinga** - sistema para torneios com atualização em tempo real e sites personalizados. Também é **serviço pago e fechado**, com foco na divulgação de resultados, não no acompanhamento técnico detalhado.

## Limitações Identificadas

* **Ausência de acompanhamento técnico em tempo real** (registro preciso de rotação, substituições, líbero, tempos e sanções).
* **Falta de exibição pública imediata**, limitando o acesso de espectadores fora do app oficial.
* **Soluções proprietárias e pagas**, inacessíveis para muitas entidades locais.
* **Falta de opções open-source** que permitam adaptação e colaboração comunitária.

## Proposta do Projeto

Desenvolver um **sistema open-source de gerenciamento de campeonatos de voleibol**, voltado principalmente a entidades locais que buscam estruturar e modernizar seus torneios sem custos adicionais. O sistema prioriza:

* **Atualização ao vivo via WebSocket**, com modo público de exibição em tempo real para qualquer dispositivo;
* **Gerenciamento técnico da partida** (rotação, substituições, entrada/saída de líbero, pedidos de tempo e sanções);
* **Estatísticas definidas e acessíveis** para organizadores e público;
* **Histórico completo de torneios e rankings transparentes**;
* **Suporte a múltiplos idiomas, incluindo PT-BR**, permitindo expansão colaborativa.

## Objetivos

Democratizar o acesso a ferramentas de gestão esportiva, melhorar a organização e a transparência dos campeonatos locais e oferecer uma melhor experiência para espectadores e participantes. Habilitar também a expansão do sistema para outras realidades por meio de contribuições e forks, devido ao caráter open-source.

## Escopo Previsto

1. **Cadastro de Usuários**: registro e autenticação (organizadores, atletas, espectadores).
2. **Cadastro de Jogadores**: perfis de jogadores com estatísticas individuais.
3. **Cadastro de Times**: gestão de equipes, jogadores e técnicos.
4. **Gerenciamento de Campeonatos**: criação/edição/exclusão de campeonatos; inclusão do **regulamento/documento oficial** e definição de regras básicas.
5. **Check-in de times e jogadores**: confirmação de presença antes das partidas.
6. **Gerenciamento de Partidas Individuais**: controle de sets, pontuação, tempos, substituições e rotação.
7. **Controle de Sanções e Advertências**: registro de cartões, faltas e suspensões.
8. **Acompanhamento em Tempo Real**: atualização instantânea via WebSockets.
9. **Modo de Exibição Pública**: interface para espectadores acompanhar partidas ao vivo em múltiplos dispositivos.
10. **Chaveamento e Tabelas**: geração automática de tabelas e classificação.
11. **Estatísticas Detalhadas**: registro de aces, bloqueios, erros, eficiência por set etc.
12. **Geração de Súmula e Relatórios de Partidas**: súmula detalhada por jogo; exportação para PDF/CSV.
13. **Relatório Geral do Campeonato**: relatório completo do torneio (desempenho e **quantidade de pessoas que acompanharam via ferramenta**).
14. **Sistema de Notificações**: alertas (WebPush e/ou WhatsApp via API oficial).
15. **Suporte a Múltiplos Idiomas**: i18n (concepção em PT-BR; possibilidade de contribuição de traduções).
16. **Controle de Perfis e Permissões**: papéis (organizador, técnico, árbitro, espectador).
17. **Sistema Open-Source**: código público (ex.: GitHub) para personalização e contribuição.
18. **Sistema de Feedback e Colaboração**: canal para sugestões e correções da comunidade.
19. **Documentação Completa**: guias técnicos e de usuário.
20. **Interface Responsiva**: compatível com diferentes dispositivos.

<!-- ## Considerações finais (viabilidade)

O projeto une um escopo técnico factível para um TCC com impacto social relevante: atende demandas reais de entidades que não podem arcar com soluções pagas e oferece ganhos imediatos na organização e visibilidade dos campeonatos. A abordagem open-source e o suporte multilíngue aumentam a probabilidade de adoção e de evolução colaborativa do sistema. -->

<br>
<br>
<br>