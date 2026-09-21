## 1. Diagrama C4 nível 1 (contexto)
 
```mermaid
flowchart TD
    Vendedor(["Vendedor<br/>Registra pedidos"])
    Administrador(["Administrador<br/>Cadastra e remove produtos"])
    Estoque(["Time de estoque<br/>Controla a quantidade disponível"])
    Sistema["Sistema de vendas e estoque"]
 
    Vendedor --> Sistema
    Administrador --> Sistema
    Estoque --> Sistema
 
    classDef person fill:#378ADD,stroke:#185FA5,color:#fff
    classDef system fill:#7F77DD,stroke:#534AB7,color:#fff
 
    class Vendedor,Administrador,Estoque person
    class Sistema system
```
 
## 2. Diagrama C4 nível 2 (contêineres)
 
```mermaid
flowchart TD
    Vendedor(["Vendedor"])
    Administrador(["Administrador"])
    Estoque(["Time de estoque"])
 
    subgraph Sistema["Sistema de vendas e estoque"]
        App["Aplicação<br/>Interface de pedidos, produtos e estoque"]
        Api["API<br/>Regras de negócio"]
        Db[("Banco de dados<br/>Produtos, pedidos e estoque")]
        App --> Api
        Api --> Db
    end
 
    Vendedor --> App
    Administrador --> App
    Estoque --> App
 
    classDef person fill:#378ADD,stroke:#185FA5,color:#fff
    classDef container fill:#5DCAA5,stroke:#0F6E56,color:#000
 
    class Vendedor,Administrador,Estoque person
    class App,Api,Db container
```
 
## 3. Nível 2 anotado com as camadas
 
```mermaid
flowchart TD
    Vendedor(["Vendedor"])
    Administrador(["Administrador"])
    Estoque(["Time de estoque"])
 
    subgraph Sistema["Sistema de vendas e estoque"]
        App["Aplicação<br/>Camada de apresentação"]
        Api["API<br/>Camada de domínio"]
        Db[("Banco de dados<br/>Camada de dados")]
        App --> Api
        Api --> Db
    end
 
    Vendedor --> App
    Administrador --> App
    Estoque --> App
 
    classDef person fill:#378ADD,stroke:#185FA5,color:#fff
    classDef apresentacao fill:#B5D4F4,stroke:#185FA5,color:#000
    classDef dominio fill:#FAC775,stroke:#854F0B,color:#000
    classDef dados fill:#9FE1CB,stroke:#0F6E56,color:#000
 
    class Vendedor,Administrador,Estoque person
    class App apresentacao
    class Api dominio
    class Db dados
```
 
- **Apresentação**: a Aplicação, por onde vendedor, administrador e time de estoque interagem com o sistema.
- **Domínio**: a API, que concentra as regras de negócio (registrar pedido, cadastrar/remover produto, dar baixa ou registrar entrada de estoque).
- **Dados**: o Banco de dados, que armazena produtos, pedidos e o controle de estoque.
