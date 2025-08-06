[[Tecnologia e serviços da nuvem]]
Amazon Neptune é um banco de dados grafo gerenciado, otimizado para aplicativos que precisam trabalhar com relacionamentos complexos e navegar por grandes volumes de dados conectados. Ele suporta dois principais modelos de grafos: **Property Graph** e **RDF (Resource Description Framework)**, além de linguagens de consulta associadas, como Gremlin e SPARQL.
Amazon Neptune

O que é:
Amazon Neptune é um banco de dados grafo gerenciado, otimizado para aplicativos que precisam trabalhar com relacionamentos complexos e navegar por grandes volumes de dados conectados. Ele suporta dois principais modelos de grafos: Property Graph e RDF (Resource Description Framework), além de linguagens de consulta associadas, como Gremlin e SPARQL.
Características Técnicas

1. Suporte a Modelos de Grafo

    Property Graph: Usa Gremlin como linguagem de consulta para explorar grafos orientados a propriedades.
    RDF: Usa SPARQL como linguagem de consulta, ideal para grafos semânticos e ontologias.

2. Totalmente Gerenciado

    Automatiza tarefas como provisionamento, backups, restaurações, atualizações de software e replicação.
    Alta disponibilidade com replicação em várias zonas de disponibilidade (AZs).

3. Alta Performance

    Otimizado para grafos, suporta consultas de baixa latência para grandes volumes de dados conectados.
    Suporta até 15 réplicas de leitura para escalar operações de leitura intensiva.

4. Segurança

    Criptografia em Repouso: Usa AWS KMS para proteger dados.
    Criptografia em Trânsito: Comunicação segura com SSL/TLS.
    Controle de acesso com AWS IAM e integrações com políticas detalhadas.

5. Escalabilidade

    Armazena automaticamente dados de grafos em fragmentos distribuídos para escalabilidade horizontal.
    Capacidade de armazenamento que cresce automaticamente até 64 TB sem interrupções.

6. Suporte Multi-Model

    Suporta vários tipos de grafos simultaneamente, permitindo flexibilidade na modelagem de dados.

7. Monitoramento e Logs

    Integra-se com Amazon CloudWatch para rastrear métricas de performance, consumo de recursos e logs de consultas.

8. Casos de Uso Avançados

    Detecção de Fraudes: Identificar anomalias em padrões de transações conectadas.
    Recomendações Personalizadas: Criar sistemas de recomendação baseados em redes de usuários e itens.
    Gerenciamento de Redes: Monitorar redes sociais, redes de telecomunicações e estruturas de TI.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Cobrança com base no tipo e tamanho das instâncias do cluster.
    - Custos adicionais para armazenamento utilizado, backups e transferência de dados.
**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o Amazon Neptune como uma solução para bancos de dados grafo gerenciados.
- Reconhecer seu suporte a linguagens de consulta como Gremlin e SPARQL.
- Compreender como ele facilita a modelagem e análise de dados conectados em larga escala.