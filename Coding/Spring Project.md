### **Fase 1: A Fundação - O Esqueleto Funcional (Semanas 1 a 6)**

O objetivo aqui é construir o fluxo de segurança mais crítico e a base da nossa arquitetura.

**Semana 1: Setup do Ambiente e "Hello World" Distribuído**

- **Foco:** Garantir que os serviços se enxerguem e que o ambiente de desenvolvimento funcione.
    
- **Tarefas:**
    
    - [x] Criar um projeto Maven ou Gradle com múltiplos módulos (`api-gateway`, `auth-service`).
        
    - [x] Configurar o **Spring Cloud Gateway** no módulo `api-gateway`.
        
    - [x] Criar um endpoint de teste (ex: `GET /hello`) no `auth-service`.
        
    - [x] Configurar o Gateway para rotear as chamadas de `/api/auth/**` para o `auth-service`.
        
    - [x] Criar o arquivo `docker-compose.yml` para subir os dois serviços.
        
- **Entregável:** Ao executar `docker-compose up`, você consegue acessar `http://localhost:8080/api/auth/hello` (no Gateway) e receber a resposta do `auth-service`.
    

**Semana 2: Registro de Usuário e Segurança Básica**

- **Foco:** Persistir um usuário de forma segura.
    
- **Tarefas:**
    
    - [x] Adicionar Spring Security e Spring Data JPA ao `auth-service`.
        
    - [x] Criar a entidade `User` e seu repositório.
        
    - [x] Configurar o `SecurityFilterChain` para permitir acesso público ao endpoint de registro.
        
    - [x] Implementar o `PasswordEncoder` (usando `BCrypt`).
        
    - [x] Criar um endpoint `POST /register` que recebe os dados do usuário, hasheia a senha e salva no banco.
        
- **Entregável:** Você consegue enviar uma requisição via Postman para registrar um novo usuário e vê-lo no banco com a senha "hasheada".
    

**Semana 3: O Coração da Segurança - Emissão de JWT**

- **Foco:** Implementar o login e a geração do token.
    
- **Tarefas:**
    
    - [ ] Adicionar uma biblioteca JWT ao `auth-service` (ex: `io.jsonwebtoken.jjwt`).
        
    - [ ] Criar uma classe/serviço utilitário para gerar e validar tokens JWT.
        
    - [ ] Implementar o endpoint `POST /login`. Ele deve autenticar o usuário e, se for bem-sucedido, retornar um token JWT válido.
        
- **Entregável:** Ao enviar credenciais corretas para `/login`, a API retorna um token JWT.
    

**Semana 4: Protegendo o Primeiro Endpoint**

- **Foco:** Fazer o Spring Security de fato proteger um recurso.
    
- **Tarefas:**
    
    - [ ] Criar um endpoint de teste protegido no `auth-service`, como `GET /api/me`, que deve retornar os dados do usuário autenticado.
        
    - [ ] Configurar o `SecurityFilterChain` para exigir autenticação para o path `/api/**`.
        
    - [ ] Criar e registrar um filtro (`JwtAuthFilter`) que intercepta a requisição, extrai o token, valida-o e seta o `SecurityContextHolder`.
        
- **Entregável:** Requisições para `/api/me` sem token falham (401). Com um token válido no cabeçalho `Authorization`, a requisição funciona e retorna os dados do usuário.
    

**Semana 5: O Guardião - Segurança Centralizada no API Gateway**

- **Foco:** Mover a responsabilidade de validação do token para o Gateway.
    
- **Tarefas:**
    
    - [ ] Implementar um `GlobalFilter` customizado no API Gateway.
        
    - [ ] Neste filtro, adicionar a lógica para validar o token JWT de todas as requisições que chegam.
        
    - [ ] Se o token for válido, o filtro adiciona cabeçalhos à requisição antes de repassá-la (ex: `X-User-Id`, `X-User-Roles`).
        
    - [ ] Se for inválido, o filtro barra a requisição com um erro 401.
        
- **Entregável:** O Gateway agora é o único responsável por validar o token, simplificando os serviços internos.
    

**Semana 6: Conectando os Pontos e Criando o Serviço de Produtos**

- **Foco:** Validar o fluxo completo com um segundo serviço.
    
- **Tarefas:**
    
    - [ ] Criar o módulo do `product-service` e adicioná-lo ao Docker Compose.
        
    - [ ] Configurar o Gateway para rotear para o `product-service`.
        
    - [ ] Criar um endpoint `POST /products` no `product-service` e protegê-lo com `@PreAuthorize("hasRole('ARTESAO')")`.
        
    - [ ] Testar o fluxo completo: Login -> Pegar Token -> Chamar `POST /products` com o token.
        
- **Entregável:** O MVP está pronto! O fluxo de segurança distribuído funciona.
    

---

### **Fase 2: Construindo a Plataforma (Semanas 7 a 12)**

Agora que a base está sólida, vamos adicionar as funcionalidades.

**Semanas 7-8: Serviço de Produtos Completo**

- **Foco:** Finalizar um microservice com lógica de negócio e autorização complexa.
    
- **Tarefas:**
    
    - [ ] Implementar o CRUD completo de Produtos (Create, Read, Update, Delete).
        
    - [ ] Implementar a lógica de autorização: apenas o artesão dono do produto pode atualizá-lo ou deletá-lo. (Isso exigirá criar um serviço de segurança customizado para usar com `@PreAuthorize`).
        

**Semanas 9-10: Serviço de Pedidos**

- **Foco:** Criar o serviço mais complexo em termos de regras de negócio.
    
- **Tarefas:**
    
    - [ ] Modelar e implementar as entidades `Order` e `OrderItem`.
        
    - [ ] Implementar os endpoints para criar um pedido e listar os pedidos de um usuário.
        
    - [ ] Implementar a autorização: um usuário só pode ver seus próprios pedidos.
        

**Semana 11: Login Social com OAuth2/OIDC**

- **Foco:** Adicionar um método de login alternativo e muito valorizado.
    
- **Tarefas:**
    
    - [ ] Configurar o `spring-boot-starter-oauth2-client` no `auth-service`.
        
    - [ ] Registrar sua aplicação no Google Cloud Console para obter `client-id` e `client-secret`.
        
    - [ ] Implementar o fluxo para que, após o login com Google, sua API gere o seu próprio JWT para o usuário.
        

**Semana 12: Refresh Tokens**

- **Foco:** Melhorar a segurança e a experiência do usuário.
    
- **Tarefas:**
    
    - [ ] Modificar o endpoint de login para retornar também um `refresh_token`.
        
    - [ ] Criar um endpoint `POST /auth/refresh` que recebe um `refresh_token` válido e retorna um novo `access_token` (JWT).
        

---

### **Fase 3: Polimento para o Portfólio (Semanas 13 a 16)**

Esta fase é o que diferencia um "projeto de curso" de um "projeto de portfólio profissional".

**Semana 13: Documentação Interativa (Swagger/OpenAPI)**

- **Foco:** Tornar sua API fácil de entender e usar.
    
- **Tarefas:**
    
    - [ ] Adicionar o SpringDoc em todos os microservices.
        
    - [ ] Anotar os controllers e DTOs para gerar uma documentação clara.
        
    - [ ] Configurar o Swagger UI para entender e enviar o token JWT.
        

**Semana 14: Escrevendo Testes**

- **Foco:** Garantir a qualidade e a robustez do seu código.
    
- **Tarefas:**
    
    - [ ] Escrever testes unitários para as regras de negócio nos seus serviços.
        
    - [ ] Escrever testes de integração para os controllers, usando `@SpringBootTest` e simulando a segurança com `@WithMockUser`.
        

**Semana 15: O README.md Perfeito**

- **Foco:** Criar a "página de vendas" do seu projeto no GitHub.
    
- **Tarefas:**
    
    - [ ] Escrever a descrição do projeto, a história do "Nexo Criativo".
        
    - [ ] Criar e adicionar o diagrama da arquitetura.
        
    - [ ] Detalhar as instruções de setup.
        
    - [ ] Fornecer exemplos de `curl` e/ou uma coleção do Postman para facilitar os testes.
        

**Semana 16: Revisão Final e Buffer**

- **Foco:** Catch-up e revisão final.
    
- **Tarefas:**
    
    - [ ] Revisar todo o backlog e finalizar tarefas que possam ter atrasado.
        
    - [ ] Refatorar o código, remover comentários desnecessários, padronizar a formatação.
        
    - [ ] Pedir a um amigo para tentar rodar o projeto seguindo seu README. O feedback é valiosíssimo!