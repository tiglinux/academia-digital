# Academia Digital

Projeto de Academia Digital desenvolvido em SpringBoot, JPA, ORM e JAVA

## 📋 Descrição

Sistema de gerenciamento para academias que permite cadastrar alunos, matrículas e avaliações físicas. O projeto utiliza Spring Boot com JPA/Hibernate para persistência de dados em banco H2.

## 🚀 Tecnologias Utilizadas

- Java 11
- Spring Boot 2.7.18
- Spring Data JPA
- Hibernate (ORM)
- H2 Database (in-memory)
- Lombok
- Maven

## 📦 Estrutura do Projeto

```
academia-digital/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── me/dio/academia/digital/
│   │   │       ├── controller/        # Controladores REST
│   │   │       ├── entity/           # Entidades JPA
│   │   │       │   └── form/         # DTOs para entrada
│   │   │       ├── repository/       # Repositórios JPA
│   │   │       └── service/          # Camada de serviço
│   │   │           └── impl/         # Implementações
│   │   └── resources/
│   │       └── application.properties
│   └── test/
└── pom.xml
```

## 🏗️ Entidades

### Aluno
- id (Long)
- nome (String)
- cpf (String) - único
- bairro (String)
- dataDeNascimento (LocalDate)

### Matrícula
- id (Long)
- aluno (Aluno)
- dataDaMatricula (LocalDateTime)

### Avaliação Física
- id (Long)
- aluno (Aluno)
- dataDaAvaliacao (LocalDateTime)
- peso (double)
- altura (double)

## 🔌 Endpoints da API

### Alunos
- `POST /alunos` - Criar novo aluno
- `GET /alunos` - Listar todos os alunos
- `GET /alunos?dataDeNascimento=yyyy-MM-dd` - Filtrar por data de nascimento
- `GET /alunos/{id}` - Buscar aluno por ID
- `PUT /alunos/{id}` - Atualizar aluno
- `DELETE /alunos/{id}` - Remover aluno

### Matrículas
- `POST /matriculas` - Criar nova matrícula
- `GET /matriculas` - Listar todas as matrículas
- `GET /matriculas?bairro=nome` - Filtrar por bairro
- `GET /matriculas/{id}` - Buscar matrícula por ID
- `DELETE /matriculas/{id}` - Remover matrícula

### Avaliações Físicas
- `POST /avaliacoes` - Criar nova avaliação
- `GET /avaliacoes` - Listar todas as avaliações
- `GET /avaliacoes/{id}` - Buscar avaliação por ID
- `DELETE /avaliacoes/{id}` - Remover avaliação

## 🛠️ Como Executar

### Pré-requisitos
- Java 11 ou superior
- Maven 3.6+

### Compilar o projeto
```bash
mvn clean install
```

### Executar a aplicação
```bash
mvn spring-boot:run
```

A aplicação estará disponível em: `http://localhost:8080`

### Acessar o Console H2
```
URL: http://localhost:8080/h2-console
JDBC URL: jdbc:h2:mem:testdb
Username: sa
Password: (deixar em branco)
```

## 📝 Exemplos de Uso

### Criar um Aluno
```json
POST /alunos
{
  "nome": "João Silva",
  "cpf": "12345678901",
  "bairro": "Centro",
  "dataDeNascimento": "1990-05-15"
}
```

### Criar uma Matrícula
```json
POST /matriculas
{
  "alunoId": 1
}
```

### Criar uma Avaliação Física
```json
POST /avaliacoes
{
  "alunoId": 1,
  "peso": 75.5,
  "altura": 1.75
}
```

## 🏛️ Arquitetura

O projeto segue uma arquitetura em camadas:

1. **Controller**: Recebe requisições HTTP e retorna respostas
2. **Service**: Contém a lógica de negócio
3. **Repository**: Interface com o banco de dados usando Spring Data JPA
4. **Entity**: Entidades mapeadas com JPA/Hibernate

## 📄 Licença

Este projeto foi desenvolvido para fins educacionais.