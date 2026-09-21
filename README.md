# C4 — Sistema de loja de vinil

Diagrama C4 completo (Contexto, Container, Componente e Código) do sistema, feito com Mermaid.

## Nível 1 — Contexto

```mermaid
C4Context
    title Diagrama de Contexto - Sistema de loja de vinil

    Person(cliente, "Cliente", "Busca e compra discos de vinil")
    Person(funcionario, "Funcionário", "Gerencia o catálogo e os pedidos")

    System(sistema, "Sistema de loja de vinil", "Permite comprar discos de vinil online")

    System_Ext(pagamento, "Sistema de pagamento", "Processa pagamentos")
    System_Ext(frete, "Serviço de frete", "Calcula e rastreia entregas")

    Rel(cliente, sistema, "Usa")
    Rel(funcionario, sistema, "Gerencia")
    Rel(sistema, pagamento, "Envia cobranças")
    Rel(sistema, frete, "Solicita envios")
```

## Nível 2 — Container

```mermaid
C4Container
    title Diagrama de Container - Sistema de loja de vinil

    Person(cliente, "Cliente")

    System_Boundary(sistema, "Sistema de loja de vinil") {
        Container(web, "Aplicação web", "React", "Catálogo, carrinho e checkout")
        Container(api, "API", "Node.js", "Regras de negócio e pedidos")
        ContainerDb(db, "Banco de dados", "PostgreSQL", "Armazena vinis, pedidos e clientes")
    }

    System_Ext(pagamento, "Sistema de pagamento")

    Rel(cliente, web, "Acessa via navegador")
    Rel(web, api, "Faz requisições JSON/HTTPS")
    Rel(api, db, "Lê e grava dados")
    Rel(api, pagamento, "Solicita cobrança")
```

## Nível 3 — Componente

```mermaid
C4Component
    title Diagrama de Componentes - API

    Container_Boundary(api, "API") {
        Component(catalogo, "Controlador de catálogo", "Controller", "Lista e busca discos")
        Component(pedidos, "Controlador de pedidos", "Controller", "Cria e confirma pedidos")
        Component(repo, "Repositório", "Repository", "Consulta o banco de dados")
        Component(servicoPag, "Serviço de pagamento", "Service", "Comunica com o gateway externo")
    }

    ContainerDb(db, "Banco de dados")
    System_Ext(pagamento, "Sistema de pagamento")

    Rel(catalogo, repo, "Usa")
    Rel(pedidos, repo, "Usa")
    Rel(pedidos, servicoPag, "Usa")
    Rel(repo, db, "Consulta")
    Rel(servicoPag, pagamento, "Chama")
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
