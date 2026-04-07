[[Tecnologia e serviços da nuvem]]
O **Amazon EBS** é um serviço de **armazenamento em bloco** projetado para uso com **instâncias EC2**, oferecendo armazenamento persistente de baixa latência. Ele é ideal para aplicações que exigem acesso rápido e consistente a dados, como bancos de dados, sistemas de arquivos e aplicativos críticos.

---

### Características Técnicas

- **Tipos de Volumes**:
    
    - **General Purpose SSD (gp3/gp2)**: Otimizado para workloads gerais, como sistemas operacionais e bancos de dados de pequeno a médio porte.
        - **gp3**: Custo menor e maior capacidade de provisionar IOPS e throughput separadamente.
    - **Provisioned IOPS SSD (io1/io2)**: Projetado para aplicações que exigem alta performance de IOPS, como grandes bancos de dados e sistemas transacionais.
        - **io2**: Maior durabilidade e disponibilidade (99,999%).
    - **Throughput Optimized HDD (st1)**: Para workloads intensivos em leitura sequencial, como processamento de Big Data.
    - **Cold HDD (sc1)**: Opção de baixo custo para dados acessados com pouca frequência.
    - **Magnetic (standard)**: Suportado apenas para compatibilidade retroativa.
- **Elasticidade e Escalabilidade**:
    
    - Capacidade de redimensionar volumes (aumentar tamanho, IOPS ou throughput) sem downtime.
    - Suporte a até **64.000 IOPS** por volume (dependendo do tipo).
- **Snapshot**:
    
    - **Backups incrementais** armazenados no Amazon S3.
    - Podem ser usados para criar novos volumes ou replicar dados em diferentes regiões.
    - Suporte para **SnapStart** em EC2 Nitro, que acelera inicializações de volumes.
- **Performance**:
    
    - A performance varia conforme o tipo de volume e o tamanho provisionado.
    - **Bursting** disponível em volumes gp2 para picos temporários de IOPS.
- **Segurança**:
    
    - Criptografia em repouso usando **AWS KMS**.
    - Integração com **IAM** para controle de permissões.

---

### Informações Extras

- Cada volume EBS é automaticamente replicado dentro da mesma **Zona de Disponibilidade** para maior durabilidade.
- Volumes não são automaticamente excluídos quando a instância EC2 é encerrada, a menos que explicitamente configurado para isso.
- Volumes EBS podem ser anexados a qualquer instância EC2 dentro da mesma Zona de Disponibilidade.
- Snapshots podem ser compartilhados entre contas ou tornados públicos.

---

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **EBS** está dentro do **Amazon EC2** e abrange:

- **Snapshots**: Para backups e replicação.
- **Volumes EBS**: Tipos gp3, io2, st1, entre outros, para atender diferentes workloads.
- **AWS Backup**: Integração para gerenciamento centralizado de backups.
- **IAM**: Controle granular de acesso a volumes e snapshots.

---

### Custos

- **Modelo de Custos**:
    - Cobrança por GB provisionado por mês.
    - Custos adicionais para IOPS provisionados em volumes io1/io2.
    - Snapshots são cobrados pelo espaço armazenado no S3.
    - Transferência de dados entre regiões ao restaurar snapshots gera custos adicionais.

---

### Casos de Uso Comuns no Exame

- Identificar o tipo de volume ideal para diferentes workloads, como **gp3** para aplicações gerais ou **io2** para bancos de dados críticos.
- Diferenciar entre **Throughput Optimized HDD** e **Cold HDD** para workloads de leitura sequencial.
- Configurar backups automáticos com snapshots.
- Entender como EBS é integrado com **IAM** para gerenciar permissões de acesso.
- Selecionar o tipo de volume com base em custos e requisitos de performance.