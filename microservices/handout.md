- Start Date: 2021-09-22
- Issue: [#10](https://github.com/Geosoft2/geosoft2-2021/issues/10)
- Authors: [@JudithBre](http://github.com/JudithBre/), [@nschnierer](http://github.com/nschnierer/)

# Summary

A microservice is a architectural pattern to structure web applications into smaller services which are doing a specific job. These microservices communicate over a network to each other.

# Basic example

<img src="./basic-example.png" width="480px">

## API Gateway

Handles requests of the user and knows how to address the relevant microservice.

## Microservices

**User**

- `POST /login` -> Login with username and password
- `GET /me` -> Get the current user

**Invoice**

- `POST /invoices` -> Create a new invoice
- `GET /invoices` -> Get all invoices

**Customer**

- `POST /customers` -> Create a new customer
- `GET /customers` -> Get all customers

## Databases

Each microservice uses it's own database (DB) or an encapsulated instance on a database system.

# Motivation

- Scaling/planning of intensive processes
  - For example training a model or geoprocessing
  - Use resources efficiently
  - Scale on demand
- Distributed development
  - Developers are able to choose their language and technology
  - Independently teams which are working on different services
- Resilient
  - Independent services do not impact each other
  - Better testability of less complex services
- Easy Deployment
  - Easy to try out new ideas and roll back if something doesn't work
  - Accelerate new features

# Detailed design

This is the bulk of the RFC. Explain the design in enough detail for somebody
familiar with React to understand, and for somebody familiar with the
implementation to implement. This should get into specifics and corner-cases,
and include examples of how the feature is used. Any new terminology should be
defined here.

# Drawbacks

- The communication between services can be quickly complex
- Lack of documentation can lead to problems when using other services
- TBD...

# Alternatives

Monolith, Serverless

# Unresolved questions

Optional, but suggested for first drafts. What parts of the design are still
TBD?

# Resources

- https://www.redhat.com/en/topics/microservices/what-are-microservices
- https://aws.amazon.com/microservices/
- https://docs.nestjs.com/microservices/basics
