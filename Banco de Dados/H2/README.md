# Banco de Dados H2 no Spring Boot

Este documento apresenta uma visão geral sobre o banco de dados **H2** dentro de aplicações **Spring Boot**, abordando sua finalidade, como configurá-lo, como utilizá-lo e um exemplo prático de aplicação.

---

## O que é o H2?

O **H2** é um banco de dados relacional, open-source, escrito em Java, amplamente utilizado para:

- Desenvolvimento rápido de aplicações;
- Testes locais sem necessidade de um banco de dados externo;
- Banco de dados embarcado (rodando em memória ou em arquivo local);
- Protótipos e provas de conceito.

---

## ⚙Configuração no Spring Boot

### 1️⃣ Dependência no `pom.xml`
Para usar o H2 em um projeto **Maven**, adicione a seguinte dependência:

```xml
<dependency>
    <groupId>com.h2database</groupId>
    <artifactId>h2</artifactId>
    <scope>runtime</scope>
</dependency>
```

---

### 2️⃣ Configurações no `application.properties` ou `application.yml`

#### Usando `application.properties`:

```properties
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=
spring.h2.console.enabled=true
spring.jpa.hibernate.ddl-auto=update
```

#### Usando `application.yml`:

```yaml
spring:
  datasource:
    url: jdbc:h2:mem:testdb
    driverClassName: org.h2.Driver
    username: sa
    password:
  h2:
    console:
      enabled: true
  jpa:
    hibernate:
      ddl-auto: update
```

---

### 3️⃣ Acessando o Console Web do H2

Após iniciar a aplicação, o console do H2 pode ser acessado no navegador:

```
http://localhost:8080/h2-console
```

- **JDBC URL:** `jdbc:h2:mem:testdb`
- **Usuário:** `sa`
- **Senha:** (em branco)

---

## Como usar o H2 no projeto

1. **Criar entidades** usando `@Entity` do JPA;
2. **Criar repositórios** usando `JpaRepository` ou `CrudRepository`;
3. Rodar a aplicação e permitir que o Spring Boot gerencie a criação das tabelas;
4. Acessar o console H2 para visualizar e manipular os dados em tempo real.

---

## Vantagens do H2

- Simples e rápido para configurar;
- Não requer instalação de um servidor de banco de dados;
- Ideal para testes automatizados;
- Permite alternar facilmente para bancos reais (MySQL, PostgreSQL, etc.) posteriormente.

---

## Exemplo de Projeto Usando H2

Como exemplo prático, utilizei o repositório:

🔗 [andressasmedeiros/cognizant-dev-week](https://github.com/andressasmedeiros/cognizant-dev-week)

Neste projeto, foi utilizado o banco H2 inicialmente para fins de **desenvolvimento e testes rápidos**, antes de migrar para um banco de dados persistente.

---

## Referências

- [Documentação oficial do H2 Database](https://www.h2database.com)
- [Documentação Spring Boot - Data Access](https://docs.spring.io/spring-boot/docs/current/reference/html/data.html)

---

> 💡 **Dica:** O H2 é excelente para prototipagem e desenvolvimento local.  
> Em produção, recomenda-se usar bancos de dados mais robustos e persistentes como PostgreSQL, MySQL ou outros.
