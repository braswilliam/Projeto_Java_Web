# Projeto:

Visão geral do sistema

Vamos construir um pequeno sistema (API REST) de usuários e departamentos, com os seguintes casos de uso:

- Buscar todos usuários
- Buscar um usuário pelo seu id
- Inserir um novo usuário

![https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/dominio.png](https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/dominio.png)

### Desenvolvimento moderno: relacional -> objeto -> json

![https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/objetos.png](https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/objetos.png)

### Passos da aula

- Criar o projeto
- Implementar o modelo de domínio
- Mapeamento objeto-relacional com JPA
- Configurar o banco de dados H2
- Criar os endpoints da API REST

### Trechos de código para copiar

### Configuração do Maven Resources Plugin

`<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-resources-plugin</artifactId>
	<version>3.1.0</version>
</plugin>`

### Configurações do banco de dados

`# Dados de conexão com o banco H2
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

# Configuração do cliente web do banco H2
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Configuração para mostrar o SQL no console
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true`

### Script SQL

````
INSERT INTO tb_department(name) VALUES ('Gestão');
INSERT INTO tb_department(name) VALUES ('Informática');

INSERT INTO tb_user(department_id, name, email) VALUES (1, 'Maria', 'maria@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (1, 'Bob', 'bob@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (2, 'Alex', 'alex@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (2, 'Ana', 'ana@gmail.com');`
````

### Collection Postman
````
[{"id":1,"name":"Maria","email":"maria@gmail.com","department":{"id":1,"name":"Gestão"}},
{"id":2,"name":"Bob","email":"bob@gmail.com","department":{"id":1,"name":"Gestão"}},
{"id":3,"name":"Alex","email":"alex@gmail.com","department":{"id":2,"name":"Informática"}},
{"id":4,"name":"Ana","email":"ana@gmail.com","department":{"id":2,"name":"Informática"}},
{"id":5,"name":"Joaquim","email":"joaquim@gmail.com","department":{"id":1,"name":"Gestão"}}]
````

