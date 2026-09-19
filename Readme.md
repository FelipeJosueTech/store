# Projeto Web Services com Spring Boot e JPA / Hibernate

Este projeto foi desenvolvido como parte do **Curso Java COMPLETO** (Dr. Nelio Alves - DevSuperior). O objetivo principal é construir uma API RESTful (Web Services) estruturada em camadas, utilizando os recursos fundamentais do Spring Boot, JPA e Hibernate.

## 🎯 Objetivos do Projeto
* Criar um projeto Spring Boot Java.
* Implementar um modelo de domínio complexo com associações.
* Estruturar o sistema em camadas lógicas: Resource (Controladores REST), Service (Regras de negócio) e Repository (Acesso a dados).
* Configurar um banco de dados de teste em memória (H2).
* Executar o povoamento automático do banco de dados (Database Seeding).
* Implementar operações de CRUD (Create, Retrieve, Update, Delete).
* Realizar o tratamento de exceções de forma personalizada.
* Configurar perfis de projeto (Test, Dev, Prod).
* Realizar o deploy da aplicação (ex: Heroku) utilizando PostgreSQL.

## 🚀 Tecnologias Utilizadas
* **Java** (JDK 17+)
* **Spring Boot**
* **Spring Data JPA / Hibernate**
* **Maven**
* **Banco de Dados H2** (Perfil de Teste)
* **PostgreSQL** (Perfil de Dev/Prod)
* **Postman** (Para testes da API REST)

## 📦 Estrutura de Camadas (Logical Layers)
A aplicação foi desenvolvida seguindo o padrão de arquitetura em três camadas principais:
1. **Resource Layer:** Controladores REST responsáveis por receber as requisições HTTP e retornar as respostas (JSON).
2. **Service Layer:** Camada responsável por abrigar as regras de negócio e realizar a comunicação entre os controladores e os repositórios.
3. **Data Access Layer (Repositories):** Interfaces que estendem o `JpaRepository`, responsáveis por realizar as operações no banco de dados.

## 🧩 Modelo de Domínio
O projeto abrange um sistema simplificado de pedidos de produtos, contendo as seguintes entidades:
* **User:** Clientes do sistema.
* **Order:** Pedidos realizados pelos usuários.
* **Category:** Categorias dos produtos (Eletrônicos, Livros, Computadores, etc.).
* **Product:** Produtos disponíveis para venda.
* **OrderItem:** Classe de associação que representa os itens de um pedido (Produto, Quantidade, Preço).
* **Payment:** Pagamento associado a um pedido (relação 1-para-1).
* **OrderStatus:** Enumeração que gerencia o status do pedido (*WAITING_PAYMENT, PAID, SHIPPED, DELIVERED, CANCELED*).

## 🛠️ Como Executar o Projeto

1. Clone o repositório em sua máquina local.
2. Certifique-se de ter o **Java 17+** e o **Maven** instalados.
3. O projeto está configurado por padrão para rodar o perfil de **test**, utilizando o banco de dados H2.
4. Execute a classe principal da aplicação na sua IDE de preferência ou via linha de comando:
   ```bash
   mvn spring-boot:run
   ```
5. A API estará disponível em `http://localhost:8080`.
6. Para acessar o console do banco H2, acesse `http://localhost:8080/h2-console` e conecte-se com as configurações do `application-test.properties`.

## ⚠️ Tratamento de Exceções
A API possui tratamento customizado (via `ResourceExceptionHandler`) para garantir que mensagens de erro claras sejam devolvidas ao cliente HTTP. Exceções tratadas incluem:
* `ResourceNotFoundException`: Quando um ID buscado não existe no banco de dados (ex: Erro 404).
* `DatabaseException`: Quando ocorre uma violação de integridade no banco, como tentar deletar um usuário que possui pedidos associados (ex: Erro 400).