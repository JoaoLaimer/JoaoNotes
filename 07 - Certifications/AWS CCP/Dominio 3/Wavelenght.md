[[Tecnologia e serviços da nuvem]]
Serviço que integra recursos de computação e armazenamento da AWS a redes móveis 5G, permitindo a execução de aplicativos com baixa latência na borda (edge) da rede.
- **Computação na Borda**: Implanta serviços da AWS em data centers de operadoras de telecomunicações para reduzir a latência no acesso a aplicativos.
- **Suporte a Aplicações de Baixa Latência**: Ideal para jogos online, streaming em tempo real, realidade aumentada/virtual (AR/VR), e Internet das Coisas (IoT).
- **Integração com Outros Serviços AWS**: Recursos como Amazon EC2, Amazon ECS e Amazon EKS podem ser implantados em zonas Wavelength para oferecer computação próxima aos usuários.
- **Compatibilidade com Infraestrutura AWS**: Usa as mesmas APIs, ferramentas e práticas da AWS, facilitando a integração e o gerenciamento de workloads híbridos.
- **Redução de Latência**: Processa dados na borda da rede móvel, eliminando a necessidade de transferir dados para Regiões AWS distantes.
**Modelo de Preços**:

- **Pague pelo uso**:
    - Custos baseados nos recursos utilizados (instâncias EC2, armazenamento, etc.) dentro das zonas AWS Wavelength.
    - Tarifas adicionais podem ser aplicadas pelas operadoras de telecomunicações.

**Casos de Uso Comuns no Exame AWS Cloud Practitioner**:

- Reconhecer o AWS Wavelength como uma solução para reduzir a latência de aplicativos em redes 5G.
- Identificar a compatibilidade do Wavelength com aplicativos de computação na borda e cenários como jogos em tempo real ou IoT.
- Compreender como o Wavelength integra serviços da AWS em data centers de operadoras de telecomunicações.