[[Segurança e conformidade]]
AWS Certificate Manager (ACM) é um serviço que facilita a criação, gerenciamento e renovação de certificados SSL/TLS usados para proteger conexões de rede e gerenciar identidades em aplicativos e sites.
- **Gerenciamento de Certificados**: Simplifica a emissão, renovação automática e revogação de certificados SSL/TLS.
- **Certificados Gratuitos**: Oferece certificados SSL/TLS sem custo para serviços integrados como Elastic Load Balancers (ELB), CloudFront e API Gateway.
- **Integração com Outros Serviços AWS**: Facilita a aplicação de certificados em serviços como CloudFront, ALB, NLB, e API Gateway.
- **Renovação Automática**: Certificados emitidos pelo ACM são renovados automaticamente, eliminando riscos de expiração.
- **Suporte a Certificados de Terceiros**: Permite importar e gerenciar certificados adquiridos de outras autoridades certificadoras.
- **Validadores de Propriedade do Domínio**: Suporte para validação por e-mail, DNS ou ambos para comprovar controle do domínio.
- **Segurança Avançada**: Integra-se ao AWS Identity and Access Management (IAM) para controle detalhado de acesso a certificados.
- **Compatibilidade com ACM Private CA**: Permite criar certificados privados para uso em redes internas ou sistemas corporativos.
**Modelo de Preços**:

- **Gratuito para Certificados Emitidos pelo ACM**: Para uso com serviços AWS integrados.
- **Pague pelo uso de ACM Private CA**: Taxas associadas à criação e gerenciamento de certificados privados.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Identificar o AWS Certificate Manager como a solução para emissão e gerenciamento de certificados SSL/TLS.
- Reconhecer sua integração com serviços AWS como CloudFront e ALB para simplificar a aplicação de certificados.
- Compreender como a renovação automática reduz o risco de interrupções causadas por certificados expirados.