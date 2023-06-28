
## Software Architecture

Each business domain is divided into its own microservices, which offer RESTful API endpoints to the client.Dockerizes each backend microservice and its accompanying data storage components.The above describes how this application is organised. It is composed of Docker containers that may be operated anywhere.
This showcase project would be hosted on the GCP Cloud Platform and run as either Docker containers running directly within Compute Engine or managed by a container orchestration framework in Kubernetes (GKE).


## Running Application



__Start Backend Services__
```bash
./start-backend-services.sh
```



## Project Development
This following section describes various aspects of the project's development covering:

- testing
  - unit test
  - integration test
  - end 2 end/ component test

  

### Backend

The backend is broken up into multiple smaller fine grained size microservices.
Each business functionality is broken into their own 'domain'. A technique of context boundaries from DDD (Domain Driven Design) is used to come to this conclusion:

| Microservice     | Domain             |
|:-----------------|:-------------------|
| User Service     | User Domain        | 
| Customer Service | Customer Domain    | 
| Order Service    | Order Domain       | 
| Product Service  | Product Domain     | 

#### Unit Test

Use [JUnit 5](https://junit.org/junit5/) coupled with [Mockito](https://site.mockito.org/) to mock dependencies for unit testing.

Both JUnit & Mockito comes pre-bundled with Spring Boot.

See individual backend microservices sub-project for more details.

#### Integration Test

This project demonstrates few types of integration tests as well.

