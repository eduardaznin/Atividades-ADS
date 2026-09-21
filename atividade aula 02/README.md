D
# C4 — Sistema de loja de vinil
 
Diagrama C4 completo (Contexto, Container, Componente e Código) do sistema, feito com Mermaid.
 
## Nível 1 — Contexto
 
```mermaid
flowchart TD
    Cliente(["Cliente<br/>Busca e compra discos"])
    Funcionario(["Funcionário<br/>Gerencia o catálogo"])
    Sistema["Sistema de loja de vinil<br/>Vende discos online"]
    Pagamento[["Sistema de pagamento<br/>Processa pagamentos"]]
    Frete[["Serviço de frete<br/>Calcula e rastreia entregas"]]
 
    Cliente --> Sistema
    Funcionario --> Sistema
    Sistema --> Pagamento
    Sistema --> Frete
 
    classDef person fill:#378ADD,stroke:#185FA5,color:#fff
    classDef system fill:#7F77DD,stroke:#534AB7,color:#fff
    classDef ext fill:#B4B2A9,stroke:#5F5E5A,color:#000
 
    class Cliente,Funcionario person
    class Sistema system
    class Pagamento,Frete ext
```
 
## Nível 2 — Container
 
```mermaid
flowchart TD
    Cliente(["Cliente"])
 
    subgraph Sistema["Sistema de loja de vinil"]
        Web["Aplicação web<br/>React"]
        Api["API<br/>Node.js"]
        Db[("Banco de dados<br/>PostgreSQL")]
        Web --> Api
        Api --> Db
    end
 
    Pagamento[["Sistema de pagamento"]]
 
    Cliente --> Web
    Api --> Pagamento
 
    classDef person fill:#378ADD,stroke:#185FA5,color:#fff
    classDef container fill:#5DCAA5,stroke:#0F6E56,color:#000
    classDef ext fill:#B4B2A9,stroke:#5F5E5A,color:#000
 
    class Cliente person
    class Web,Api,Db container
    class Pagamento ext
```
 
## Nível 3 — Componente
 
```mermaid
flowchart TD
    subgraph Api["API"]
        Catalogo["Controlador de catálogo"]
        Pedidos["Controlador de pedidos"]
        Repo["Repositório"]
        ServicoPag["Serviço de pagamento"]
        Catalogo --> Repo
        Pedidos --> Repo
        Pedidos --> ServicoPag
    end
 
    Db[("Banco de dados")]
    Pagamento[["Sistema de pagamento"]]
 
    Repo --> Db
    ServicoPag --> Pagamento
 
    classDef comp fill:#F0997B,stroke:#993C1D,color:#000
    classDef ext fill:#B4B2A9,stroke:#5F5E5A,color:#000
 
    class Catalogo,Pedidos,Repo,ServicoPag comp
    class Db,Pagamento ext
```
 
## Nível 4 — Código
 
```mermaid
classDiagram
    class Pedido {
        +id
        +itens
        +total()
        +confirmar()
    }
    class GatewayPagamento {
        <<interface>>
        +cobrar(valor)
    }
    class GatewayCartao {
        +cobrar(valor)
    }
    class ServicoPagamento {
        +processar(pedido)
    }
 
    Pedido --> GatewayPagamento : usa
    GatewayCartao ..|> GatewayPagamento : implementa
    GatewayCartao --> ServicoPagamento : usa
```
 
