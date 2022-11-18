# Software Architectures

## Monolith
One Large Codebase

Usually comprised of a Client and Server System

### Pros
- Easy to develop and get started
- Existing tooling is designed for monoliths
- Web Apps are easily testable
  
### Cons
- As the Application matures and features get added, it gets harder to add new things
- Complex and Big Applications require complex code in order to work
- Reliability Concerns, an error during runtime can lead to complete system downtime
- Incompatible with Agile coding due to high code complexity

## Service Oriented Architecture

### What is a service
A Service is a self contained system that can run by itself without dependencies to other systems.
It has a clearly defined bounded context, its interfaces describe its bounds

Externally the service is not directly accesible, it should only be accesible via the Gateway of the Service Oriented Application

### Pros
- Works well with Agile, as the application is split into multiple smaller applications

### Cons
- High Upfront setup costs
- Not easily testable
- Deploying can be very complicated

## Microservice
Microservices are a subtype of SOA

### Pros
- Highly maintable
- Open System, can be extended to your hearts content
- Language Agnostic
- Isolated, due to the nature of how microservices work the programmer is essentially forced to abide by low coupling
- Robust and resilient, the outage of service does not affect another service
- Independently Scalable, services in high demand can be independently scaled from others

### Cons
- High Upfront setup costs
- Not easily testable
- Deploying can be very complicated
