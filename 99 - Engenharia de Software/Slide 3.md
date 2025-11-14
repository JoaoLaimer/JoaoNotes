## Processo de SW
Conjunto estruturado de atividades necessárias para produção, desenvolvimento e evolução do software.
- Artefatos: qualquer produto intermediário produzido durante o projeto.

Pessoal interessadas (stakeholders).

## Atividades Essenciais 
- Comunicação (levantamento de necessidades)
- Planejamento (cronograma, estimativas, etc)
- Modelagem (analise e projeto)
- Construção (codificação e testes)
- Entrega (suporte)
- Atividades Metodológicas (gerencia)

## Modelos de Processo
Representação do processo
Também chamado de ciclo de vida

### Fluxo Linear
Uma atividade só pode ser realizada após a anterior ser concluída, em sequência:
Comunicação -> Planejamento -> Modelagem -> Construção -> Entrega

### Fluxo Paralelo 
Executa uma ou mais atividades em paralelo

### Fluxo Evolucionário
Cada **volta** conduz a uma versão mais evoluída ou completa do software

### Fluxo Iterativo
Repete uma ou outra atividade antes de passar para próxima etapa. 
Atividades são repetidas, por exemplo, para tratar mudanças de requisitos, que exigem mudanças no projeto e na implementação.

### Modelos de Processo de SW
### Codificar e Consertar 
Construir com o cliente um entendimento preliminar sobre o sistema, implementar uma primeira versão do sistema, interagir com o cliente de forma a corrigir a versão, fazer testes e corrigir erros e no fim entregar o produto.
Modelo simples.

### Modelo Cascata (waterfall)
Também conhecido como Clássico.
Fluxo linear (sequencial), saída de uma fase é a entrada para a seguinte.

Funciona bem:
- Requisitos bem conhecidos e estáveis
- Preocupação com qualidade está acima do custo e tempo
- Ideal para equipes fracas.
Ruim:
- Alto tempo de espera
- Pouco flexível
- Pouco feedback
- Teste ocorre somente ao final

### Prototipação
Técnica de criação de protótipos para entender melhor requisitos e reduzir riscos.
#### Cornerstone (exploratória)
- Entender melhor requisitos e reduzir riscos
- Permite envolvimento com os usuários para convergir o sistema.
- Evoluir protótipo com acréscimo de características requeridas.
#### Throwaway (Descartável)
- Tem objetivo  compreender melhor os requisitos do sistema
- Se concentra em fazer experimentos com partes de requisitos
- Após é descartado
#### Evolucionária
- Implementação inicial e exposta ao usuário
- Com base nos comentários do usuário, refina-se.
- Mais eficaz que o cascata.
Problemas
- Falta visibilidade ao processo (prever tempo)
- Podem exigir mais ferramentas e técnicas
- Menos documentação
- Qualidade do produto
Melhor para sistemas de pequeno e médio porte.

### Modelo Espiral
Reduzir problemas com definições.
Fluxo evolucionário.
Adequado para projetos complexos.
Composto de 3 a 6 regiões de tarefas
Exemplo de 4 regiões:
- Planejamento
- Análise de Riscos
- Engenharia
- Avaliação
Cada volta ou iteração corresponde a uma fase do desenvolvimento.
Vantagens: 
- Menor risco
- Prototipação
Desvantagem:
- Requer boa capacidade para Análise de Riscos
- Dificuldade para definir cronograma.

### Entregas em Estágios
Modelo Incremental
Combina elementos do cascata com o iterativo da prototipação evolucionária.
Prevê que a equipe planeje o que vai entregar.
Depois da concepção, análise de requisitos, projeto arquitetural, teremos varias iterações de: projeto detalhado, codificação, teste, entrega. (tipo scrum)

Vantagens
- Colocar funcionalidades úteis nas mãos dos clientes antes de completar o projeto. 
- Entrega contínua
- Menor risco de fracasso
- Base para métodos ágeis.
Desvantagens:
- Incrementos pequenos
- Cada incremento deve representar uma funcionalidade
- Dificuldade de identificar facilidades comuns.