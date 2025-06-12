# Microservices

## Table of Contents
1. A Modern Architectural Approach
2. Microservices Architecture
   - What Are Microservices?
   - Key Characteristics
   - Comparison with Monolithic Architecture
3. Why Microservices?
4. Characteristics of Microservice Architecture - Summary
5. Products not Projects - Summary
6. Smart Endpoints and Dumb Pipes
7. Microservices and SOA
8. Decentralized Governance - Summary
   - Many Languages, Many Options
   - Decentralized Data Management
   - Battle-tested Standards and Enforced Standards
9. Infrastructure Automation
10. Design for Failure
11. The Circuit Breaker and Production Ready Code
12. Evolutionary Design
13. Are Microservices the Future?
14. Footnotes


## A Modern Architectural Approach

**Microservice Architecture** is a term that has gained popularity in recent years. It refers to a software design approach where applications are built as a collection of small, independent services that can be deployed separately.

Although there is no universally accepted definition, microservices generally share several key traits:

- They are **organized around business capabilities**, not technical layers.
- **Automated deployment** practices are commonly used to manage and release services.
- Each service endpoint is designed to be **intelligent and self-contained**, handling logic and communication independently.
- **Decentralization** is a core concept — different services can use different **programming languages**, **data storage solutions**, and **technology stacks**.

## This architecture promotes scalability, flexibility, and faster development cycles by allowing teams to work on, deploy, and scale services independently.

# Microservices Architecture

## What Are Microservices?

**Microservices** represent a modern architectural style where software applications are built as a suite of small, independently deployable services. Each service runs in its own process and communicates using lightweight protocols (commonly HTTP/REST APIs).

---

## Key Characteristics

- **Independent Services**: Each microservice handles a specific business capability.
- **Decentralized Management**: Services can use different languages and data stores.
- **Automated Deployment**: Enables continuous delivery and integration.
- **Intelligent Endpoints**: Logic is within services, not a central monolith.
- **Minimal Central Coordination**: Loose coupling and modular development.

---

## Comparison with Monolithic Architecture

| Feature           | Monolithic                      | Microservices                       |
| ----------------- | ------------------------------- | ----------------------------------- |
| Structure         | Single executable               | Multiple independent services       |
| Deployment        | Deploy whole system             | Deploy services individually        |
| Scalability       | Entire app                      | Scale only needed services          |
| Technology Choice | Usually unified tech stack      | Diverse languages and databases     |
| Modularity        | Difficult to maintain over time | Built-in through service boundaries |

---

## Why Microservices?

Monolithic apps are easy to build initially, but become harder to scale and maintain. Microservices address this by enabling:

- Independent deployment
- Better scalability
- Team autonomy
- Flexibility in technology use

---

## Final Thoughts

While microservices aren't a completely new idea (with roots in UNIX principles), their adoption is growing due to the demand for agility, scalability, and flexibility in modern software systems.

---

# Characteristics of Microservice Architecture - Summary

- **No Formal Definition:**  
  Microservice architecture has no strict formal definition but shares common traits across implementations.

- **Componentization via Services:**

  - Software is broken down into independently deployable services rather than just libraries.
  - Services communicate via remote calls (e.g., HTTP APIs), unlike in-memory function calls for libraries.
  - This enables independent deployment and evolution of each service.
  - Services provide explicit interfaces, reducing tight coupling.
  - Downsides include higher cost of remote calls and coarser-grained APIs.

- **Business Capability Organization:**

  - Services are organized around business capabilities rather than technical layers.
  - Teams are cross-functional, responsible for the full stack of a business area.
  - This approach avoids silos and coordination overhead typical in monolithic or layered teams.
  - Conway’s Law explains how team structure influences system design.

- **Monolith vs. Microservices:**

  - Monolithic apps are single deployable units; changes require redeploying the entire system.
  - Microservices allow more modular scaling and independent updates.
  - Large monoliths can be modularized by business capability but often lack clear team boundaries and modular discipline.

- **Overall:**  
   Microservice architecture promotes loosely coupled, independently deployable services organized by business domains, improving scalability and team autonomy at the cost of increased complexity in communication.
  ‍

---

# Products not Projects - Summary

- Most software development uses a **project model**: deliver software, then hand it off to maintenance and disband the team.
- Microservices favor a **product model**: teams own and maintain their software throughout its entire lifecycle.
- Inspired by Amazon’s “you build it, you run it” philosophy, promoting developer responsibility for production software.
- This model increases developer-user interaction and accountability, enhancing support and software quality.
- The product mindset aligns with organizing around business capabilities and ongoing improvement.
- While applicable to monoliths, smaller microservices make it easier to build close developer-user relationships.

---

# Smart Endpoints and Dumb Pipes

- Traditional systems often embed complex logic into communication layers (e.g., Enterprise Service Bus).
- Microservices prefer **smart endpoints** and **dumb pipes**:
  - Endpoints handle domain logic and processing.
  - Communication channels are kept simple and lightweight.
- Common communication protocols are HTTP REST APIs and lightweight messaging systems (e.g., RabbitMQ).
- Messaging infrastructure acts only as a simple router; intelligence resides at service endpoints.
- Transitioning from monoliths requires changing from fine-grained in-process calls to coarser, less chatty remote calls.
- This approach aligns with principles from the web and Unix, emphasizing simplicity and decoupling.

---

# Microservices and SOA

- Microservices share similarities with Service-Oriented Architecture (SOA), but SOA is a broad term with many interpretations.
- Many SOA implementations have focused on complex ESBs integrating monoliths, often leading to costly, ineffective projects.
- Microservices emphasize simplicity, decentralized governance, and lightweight protocols, learning from past SOA challenges.
- Some reject the SOA label for microservices, while others see microservices as a better, more practical form of SOA.
- Having a distinct term like "microservices" helps clarify this specific architectural style.

---

# Decentralized Governance - Summary

- Centralized governance often leads to rigid standardization on single technologies, which can be limiting.
- Microservices allow each service to choose the best technology or language for its specific needs (e.g., Node.js, C++, different databases).
- Teams prefer practical, shared tools and libraries over strict formal standards, often adopting internal open source practices.
- Netflix exemplifies this by sharing battle-tested libraries while allowing flexibility.
- Service contracts are still important but managed differently using patterns like Tolerant Reader and Consumer-Driven Contracts to allow independent evolution.
- Automated contract testing helps reduce coordination overhead and avoid overbuilding.
- The “build it / run it” model (popularized by Amazon) gives teams full ownership of software, including operations, encouraging higher quality.
- This approach contrasts strongly with traditional centralized governance and is increasingly adopted by organizations like Netflix.

# Many Languages, Many Options

- JVM’s growth illustrates mixing multiple languages on a single platform.
- Using higher-level languages for abstractions or lower-level languages for performance has been common for decades.
- Most monolithic applications don't require extreme performance optimization or extensive use of DSLs/higher abstractions.
- Typically, monoliths use a single language and tend to limit the variety of technologies in use.

---

# Decentralized Data Management

- Different systems often have varying conceptual models (e.g., sales vs. support views of a customer).
- This divergence also happens within applications divided into components; Domain-Driven Design's (DDD) Bounded Context helps clarify these boundaries.
- Microservices decentralize data storage, allowing each service to manage its own database (Polyglot Persistence), unlike monoliths which often use a single database.
- Managing updates via distributed transactions is difficult and leads to tight temporal coupling.
- Microservices favor transactionless coordination and eventual consistency, handling inconsistencies with compensating operations.
- This approach aligns with business realities where some inconsistency is tolerable for faster response, with reversal processes for corrections.

# Battle-tested Standards and Enforced Standards

- Microservice teams avoid rigid, centrally enforced corporate standards.
- They prefer and promote open standards like HTTP, ATOM, and microformats.
- Open standards are developed through real-world use and multiple live implementations, often emerging from successful open-source projects.
- These practical standards contrast with many corporate standards, which can be created by groups disconnected from current programming practices or heavily influenced by vendors.

# Infrastructure Automation

- Infrastructure automation has advanced significantly, especially with cloud platforms like AWS.
- Teams experienced in Continuous Integration (CI) and Continuous Delivery (CD) extensively use automation in building, testing, and deploying microservices.
- Automated tests provide confidence in software quality, and deployments to environments are fully automated.
- Deploying multiple applications becomes manageable once automation pipelines are in place, making deployment routine and “boring.”
- While deployment automation can be similar for monoliths and microservices, managing microservices in production often presents a more complex operational environment.

# Make It Easy to Do the Right Thing

- Increased automation from continuous delivery/deployment leads to useful tooling for developers and operations.
- Common tools help with artifact creation, codebase management, service setup, monitoring, and logging.
- Netflix’s open-source tools are a prime example of this approach.
- Other popular tools include Dropwizard, widely used for building and managing services.

# Design for Failure

- Microservices must tolerate service failures gracefully, unlike monoliths where calls are internal.
- Failure handling adds complexity, requiring teams to constantly assess impact on user experience.
- Netflix’s Simian Army tests resilience by deliberately causing service and datacenter failures.
- Real-time monitoring is critical: tracks both system metrics (e.g., requests per second) and business metrics (e.g., orders per minute).
- Monitoring helps detect failures early and supports automatic recovery.
- Microservices’ choreography and event-driven collaboration can lead to emergent behavior, which can be good or bad.
- Effective monitoring helps quickly identify and fix negative emergent behavior.
- Sophisticated dashboards and logging are standard, showing service health, circuit breaker status, throughput, and latency.
- While monoliths can also be transparent, cross-process failures in microservices demand higher visibility.

# The Circuit Breaker and Production Ready Code

- Circuit Breaker pattern is critical for resilient communicating applications.
- Often implemented alongside other patterns like Bulkhead and Timeout (as described in _Release It!_).
- Netflix provides practical examples of these patterns in production.

## Synchronous Calls Considered Harmful

- Multiple synchronous service calls multiply system downtime risk (downtime = product of individual downtimes).
- Solutions:
  - Prefer asynchronous calls to reduce cascading failures.
  - Manage downtime carefully if synchronous calls are necessary.
- Example implementations:
  - Guardian enforces a rule of one synchronous call per user request.
  - Netflix has redesigned its platform API to be inherently asynchronous.

# Evolutionary Design

- Microservice practitioners often come from an evolutionary design background, using service decomposition to enable fast, controlled changes without slowing down development.
- Key principle: Components must be independently replaceable and upgradeable.
- Many microservices are expected to be scrapped and replaced rather than continuously evolved.
- Example:
  - The Guardian website started as a monolith but is evolving towards microservices for new features, especially temporary ones (e.g., special event pages).
  - Similar strategies seen in financial institutions for market-driven features.
- Modular design principle: Group parts that change together in the same module; separate those that change at different rates.
- Microservices allow more granular and faster release cycles since only modified services need redeployment.
- Versioning is considered a last resort; services should be designed to tolerate changes from their dependencies to reduce versioning needs.

# Are Microservices the Future?

- The article presents microservices as an important architectural style worth serious consideration for enterprise applications.
- Several notable organizations (Amazon, Netflix, The Guardian, UK Government Digital Service, etc.) have adopted or are moving toward microservices.
- Many existing systems effectively use microservices without explicitly naming them (often labeled SOA, with varied interpretations).
- The authors express cautious optimism but do not claim certainty that microservices are the ultimate future.
- Long-term consequences of architectural decisions take years to fully understand.
- Benefits of microservices include explicit service boundaries that may reduce architectural decay seen in monoliths.
- Challenges include:
  - Difficulty in finding correct service boundaries.
  - Harder refactoring across remote service boundaries versus in-process libraries.
  - Complexity may shift from within components to the connections between services, which can be harder to manage.
  - Team skill level greatly affects success; microservices may not solve problems caused by poor teams.
- Some recommend starting with a modular monolith and evolving into microservices only when needed.
- Overall, microservices represent a promising path, but decisions must be made with imperfect information.
