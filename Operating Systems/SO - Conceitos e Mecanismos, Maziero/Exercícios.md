## Capítulo 1:
1. Quais os dois principais objetivos de um sistema operacional?
_Os principais objetivos de um SO são: A abstração de recursos e a gerencia dos mesmos_.
2. Por que a abstração de recursos é importante para os desenvolvedores de
aplicações? Ela tem alguma utilidade para os desenvolvedores do próprio
sistema operacional?
_Acesso a recursos do hardware, se não abstraídos, é muito complexo, dificultando o desenvolvimento de programas e aplicações_.
3. A gerência de tarefas permite compartilhar o processador, executando mais de
uma aplicação ao mesmo tempo. Identifique as principais vantagens trazidas
por essa funcionalidade e os desafios a resolver para implementá-la.
_Distribuir a capacidade de processamento de forma justa entre as aplicações.
Evitar que uma aplicação monopolize o recurso do processador.
Respeitar as prioridades definidas pelos usuários._
4. O que caracteriza um sistema operacional de tempo real? Quais as duas
classificações de sistemas operacionais de tempo real e suas diferenças?
_São sistemas operacionais onde o tempo é critico para o funcionamento, ou seja, que suas aplicações tenham comportamento temporal previsível. Eles podem ser críticos ou não críticos, onde um a perde de tempo pode gerar consequências graves e o outro a perda de tempo, por mais que não desejável, não possui consequências pesadas.__
5. Relacione as afirmações aos respectivos tipos de sistemas operacionais: distri-
buído (D), multi-usuário (M), desktop (K), servidor (S), embarcado (E) ou de
tempo-real (T):
( T ) Deve ter um comportamento temporal previsível, com prazos de resposta
claramente definidos.
( S ) Sistema operacional usado por uma empresa para executar seu banco de
dados corporativo.
( E ) São tipicamente usados em telefones celulares e sistemas eletrônicos
dedicados.
( D ) Neste tipo de sistema, a localização física dos recursos do sistema compu-
tacional é transparente para os usuários.
( M ) Todos os recursos do sistema têm proprietários e existem regras controlando
o acesso aos mesmos pelos usuários.
( E ) A gerência de energia é muito importante neste tipo de sistema.
( K ) Sistema que prioriza a gerência da interface gráfica e a interação com o
usuário.
( S ) Construído para gerenciar de forma eficiente grandes volumes de recursos.
( K ) O MacOS X é um exemplo típico deste tipo de sistema.
( E ) São sistemas operacionais compactos, construídos para executar aplicações
específicas sobre plataformas com poucos recursos.
6. Sobre as afirmações a seguir, relativas aos diversos tipos de sistemas operacionais, indique quais são incorretas, justificando sua resposta:
(a) Em um sistema operacional de tempo real, a rapidez de resposta é menos
importante que a previsibilidade do tempo de resposta.
_Sim, em um sistema de tempo real a previsibilidade de um sistema é mais importante que sua rapidez, pois assim, podemos construir aplicações que dependem dessa previsibilidade._
(b) Um sistema operacional multi-usuários associa um proprietário a cada
recurso do sistema e gerencia as permissões de acesso a esses recursos.
__
(c) Nos sistemas operacionais de rede a localização dos recursos é transparente
para os usuários.
(d) Um sistema operacional de tempo real deve priorizar as tarefas que intera-
gem com o usuário.
(e) Um sistema operacional embarcado é projetado para operar em hardware
com poucos recursos.