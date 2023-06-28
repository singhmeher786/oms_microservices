
## Software Architecture

Each business domain is segregated into their own microservices which exposes RESTful API endpoints for the client to consume.Each backend microservice & its associated data storage components are dockerized.The above mentions how this application is systemed up. It is built as a series of Docker containers that can be run anywhere.
For simulating a prod-like environment, this demo project would live on the AWS Cloud Platform and can be run as either Docker containers running directly inside EC2 instances or being managed by a container orchestration framework in Kubernetes (AWS EKS).


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

