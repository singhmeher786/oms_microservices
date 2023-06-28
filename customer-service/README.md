# Customer Service

This is a backend microservice which provides services to interact with 'Customers'.

This is merely a very simple "entity-driven" microservice as it is just purely a CRUD wrapper. 

At this moment in time it allows users to:
- Create new customers
- Fetch whole list of customers
- Retrieve a customer by its customer id

This microservivce is backed by a relational MySQL database.



## Local Mode

Local mode is mainly used for developing this microservice.

Run directly from your IDE or from CLI using following command:

```bash
./mvnw spring-boot:run -Dspring.profiles.active=dev
```

You don't have to install MySQL but if have then can just launch it:

```bash
mysql -u root -p 
```

where password is _root_. See `application.properties` to see and/or to change if want.

Otherwise, can simply launch a docker container for it (via Docker-Compose):

```bash
docker-compose up -d customer-db-mysql
```

## Development Mode

You can run this microservice in "Development mode" which is a mode that allows firing up the Customer Service tech stack. This mode can be used for simple demo with the team or for functional testing by QAs/Testers.

This sub project is docker-composed to achieve this:

```bash
docker-compose up -d --build
```


### Building

First require to build a jar artifact:

```bash
./mvnw clean install
```

Then construct the Docker image:

```bash
docker build -t customer-service .
```

## Functional Testing (using Postman)

For doing functional testing of this microservice you can use a http client. I like to use Postman.

All of the API endpoints of this microservice are authenticated and thus require the user to be authorized to execute them. See Authenticated section below.

## API Documentation

You can access the documentation for the API using Swagger:

```bash
http://{customer-service-url}:8081/swagger-ui.html
```

## Authentication

As this whole project uses JWT (JSON Web Tokens) for authentication, it is required to get a valid JWT token first from the __User-Service__.

User-Service maintains a list of valid users of the Sales Order System application so it is required to have a valid user to use for it to return a valid JWT token. If required, sign up a new user. Please see __User Service__ for more details on this setup.

Once obtained a valid JWT token, first make a request to:

```bash
http://{user-service-url}:8080/authenticate
```

with the following body in request:

```json
{
    "username": [a valid username here],
    "password": [a valid password here]
}
```

Http Client Postman handles most header defaults for you but if using other mechanism such as Curl then must ensure:

- Content-Type of 'application/json' is set


## Technologies

- Java 8
- Spring:
    - Spring Boot
    - Spring Data JPA
    - Spring Security
      - JWT
- MySQL
- Swagger
- Docker:
    - Docker Compose
- Maven
- H2
- RestAssured
- TestContainers
  - (using MySQL module)