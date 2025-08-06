[[Tecnologia e serviços da nuvem]]
O **Route 53** é um serviço de **DNS** (Domain Name System) gerenciado, altamente disponível e escalável. Ele permite o roteamento de tráfego de usuários para aplicações na **AWS**, on-premises ou em outras nuvens. Suporta **políticas de roteamento avançadas** e integração com outros serviços da AWS.

### Características Técnicas

- **Gerenciamento de DNS**:
    
    - Resolve nomes de domínio para endereços IP usando **zonas hospedadas** e **registros de DNS**.
    - Suporte a tipos de registro como **A, AAAA, CNAME, MX, TXT, NS**, entre outros.
- **Políticas de Roteamento**:
    
    - **Simple**: Rota única para um recurso específico. Ideal para cenários simples.
    - **Weighted**: Permite dividir o tráfego entre vários recursos com pesos configurados.
    - **Latency-based**: Direciona usuários para o recurso com menor latência.
    - **Failover**: Redireciona tráfego para um recurso secundário caso o principal falhe.
    - **Geolocation**: Roteia tráfego com base na localização geográfica do usuário.
    - **Geoproximity**: Similar ao geolocation, mas permite ajuste por **bias** para expandir ou reduzir a área de cobertura.
    - **Multi-value Answer**: Retorna várias respostas, útil para balanceamento de carga simples.
- **Registro de Domínios**:
    
    - Funciona como um **registrador de domínios** para TLDs comuns.
    - Suporte a gerenciamento de **DNSSEC** para maior segurança.
- **Health Checks**:
    
    - Monitora a saúde dos recursos associados aos registros DNS.
    - Integração com notificações via **Amazon CloudWatch**.
- **Integração com VPC**:
    
    - Suporte a **DNS privado** dentro de uma **Amazon VPC**, permitindo resolver nomes internos.

### Informações Extras

- Os registros de políticas de roteamento, como **Weighted** e **Latency-based**, são avaliados na ordem definida pelo administrador.
- Os health checks podem monitorar URLs externos ou internos e incluem opções como **HTTP, HTTPS** e portas TCP.
- Zone files são armazenados globalmente para alta disponibilidade e resiliência.

### Serviços Abrangidos ou Onde o Serviço Está Abrangido

O **Route 53** abrange:

- **Health Checks**: Verificam disponibilidade e desempenho.
- **Hosted Zones**: Repositório para gerenciar registros de DNS.
- **Registro de Domínios**: Facilita compra e gerenciamento de nomes de domínio.

### Custos

- **Modelo de Custos**:
    - Taxas por **zonas hospedadas ativas**.
    - Custo por **consulta DNS** (mais barato para DNS privado).
    - Registro de domínios varia conforme o TLD.
    - Health checks possuem cobrança separada com base em número e frequência de monitoramento.

### Casos de Uso Comuns no Exame

- Escolher a **política de roteamento** mais apropriada para um caso de uso (e.g., geolocation para conformidade com regulamentações).
- Configurar **failover** para alta disponibilidade.
- Utilizar health checks para garantir resiliência e performance.
- Criar **DNS privado** para isolar a resolução de nomes dentro de uma VPC.
- Reconhecer custos associados a consultas DNS e domínios registrados.