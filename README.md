# <span style="color:lightblue">Projeto:</span>

## <span style="color:lightblue">Visão geral do sistema</span> 

Vamos construir um pequeno sistema (API REST) de usuários e departamentos, com os seguintes casos de uso:

- Buscar todos usuários
- Buscar um usuário pelo seu id
- Inserir um novo usuário

![https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/dominio.png](https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/dominio.png)

### <span style="color:lightblue">Desenvolvimento moderno: relacional -> objeto -> json</span>

![https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/objetos.png](https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/objetos.png)

### <span style="color:lightblue">Passos do projeto</span> 

- Criar o projeto
- Implementar o modelo de domínio
- Mapeamento objeto-relacional com JPA
- Configurar o banco de dados H2
- Criar os endpoints da API REST

### <span style="color:lightblue">Trechos de código para copiar</span> 

### <span style="color:lightblue">Configuração do Maven Resources Plugin</span> 

`<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-resources-plugin</artifactId>
	<version>3.1.0</version>
</plugin>`

### <span style="color:lightblue">Configurações Configuração do Maven Resources Plugando banco de dados</span> 

`# Dados de conexão com o banco H2
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

### <span style="color:lightblue">Configuração do cliente web do banco H2</span> 
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

### <span style="color:lightblue">Configuração para mostrar o SQL no console</span> 
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true`

### <span style="color:lightblue">Script SQL</span> 

````
INSERT INTO tb_department(name) VALUES ('Gestão');
INSERT INTO tb_department(name) VALUES ('Informática');

INSERT INTO tb_user(department_id, name, email) VALUES (1, 'Maria', 'maria@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (1, 'Bob', 'bob@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (2, 'Alex', 'alex@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (2, 'Ana', 'ana@gmail.com');`
````

### <span style="color:lightblue">Collection Postman</span>
````
[{"id":1,"name":"Maria","email":"maria@gmail.com","department":{"id":1,"name":"Gestão"}},
{"id":2,"name":"Bob","email":"bob@gmail.com","department":{"id":1,"name":"Gestão"}},
{"id":3,"name":"Alex","email":"alex@gmail.com","department":{"id":2,"name":"Informática"}},
{"id":4,"name":"Ana","email":"ana@gmail.com","department":{"id":2,"name":"Informática"}},
{"id":5,"name":"Joaquim","email":"joaquim@gmail.com","department":{"id":1,"name":"Gestão"}}]
````

### <span style="color:lightblue">Comandos das requisições:</span>

<span style="color:Orange">Pegando lista de Usuários:</span> <span style="color:Green">GET</span>
``http://localhost:8080/users``

<span style="color:Orange">Pegando  Usuário:</span> <span style="color:Green">GET</span>
``http://localhost:8080/users/1``

<span style="color:Orange">Adicionando um novo Usuário:</span> <span style="color:Green">POST</span>
``http://localhost:8080/users``

<span style="color:Orange">COMANDO JSON:</span>

```
{
"name": "Joaquim",
"email": "joaquim@gmail.com",
"department": {
"id": 1
}
}
```

