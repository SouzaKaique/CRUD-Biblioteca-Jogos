#  📚 CRUD Biblioteca de Jogos

Este projeto é uma aplicação Spring Boot para gerenciar uma biblioteca de jogos.
Permite cadastrar, listar, editar, excluir e pesquisar jogos por título, autor e gênero.

## 🚀 Tecnologias utilizadas

Java 21

Spring Boot 3 (Web, Data JPA, Thymeleaf)

PostgreSQL

Maven

Hibernate

Thymeleaf (para renderização das views)

## 📂 Estrutura do projeto
src/main/java/br/com/bibliotecajogos/
│── controller/        
│── entity/            
│── repository/        
│── service/           
│── config/            
│── BibliotecajogosApplication.java  


---

## ⚙️ Pré-requisitos

Antes de rodar a aplicação, você precisa ter instalado:

- [Java 21](https://adoptium.net/)  
- [Maven 3.9+](https://maven.apache.org/)  
- [PostgreSQL 15+](https://www.postgresql.org/download/)  

---

## 🛠️ Configuração do banco de dados

1. Crie um banco no PostgreSQL:

```sql
CREATE DATABASE biblioteca_jogos;
```
No arquivo src/main/resources/application.properties, configure a conexão:
```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/biblioteca_jogos
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.thymeleaf.cache=false
```

▶️ Como executar localmente

Clone o repositório:
```bash
git clone https://github.com/SouzaKaique/CRUD-Biblioteca-Jogos.git
cd CRUD-Biblioteca-Jogos
```

Compile e rode a aplicação:
```bash
mvn spring-boot:run
```

Ou, se preferir, gere o .jar e execute:
```bash
mvn clean package -DskipTests
java -jar target/bibliotecajogos-0.0.1-SNAPSHOT.jar
```

## 🌐 Acesso à aplicação


Após rodar, acesse no navegador:
```bash
http://localhost:8080/jogos
```

## 📌 Endpoints principais

GET /jogos → Lista todos os jogos

GET /jogos/novo → Formulário para cadastrar jogo

POST /jogos → Salvar novo jogo

GET /jogos/editar/{id} → Editar jogo existente

GET /jogos/excluir/{id} → Excluir jogo

GET /jogos/pesquisar?termo=...&tipo=... → Pesquisar jogos

🖼️ Telas (Thymeleaf)

Listagem de jogos

Formulário de cadastro/edição

Pesquisa filtrada por título, autor ou gênero

## 🐳 Executando com Docker (opcional)

Se quiser rodar com Docker, use o Dockerfile já incluído:
```bash
docker build -t biblioteca-jogos .
docker run -p 8080:8080 biblioteca-jogos
```
