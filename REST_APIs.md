# REST (Representational State Transfer)

## What is REST?

**REST** (Representational State Transfer) is an architectural style for designing networked applications. It was introduced by **Roy Fielding** in his doctoral dissertation in 2000. RESTful APIs use standard HTTP methods to perform operations on resources, making them simple, scalable, and easy to implement.

---

## Key Principles of REST

For an API to be truly RESTful, it must follow these six constraints:

1. **Client-Server**  
   Separation of concerns between the client (UI) and the server (data and logic).

2. **Stateless**  
   Each request from the client must contain all the information needed; the server does not store session state.

3. **Cacheable**  
   Responses should indicate if they are cacheable to improve performance.

4. **Uniform Interface**  
   A consistent way of interacting with resources using URIs and standard HTTP methods.

5. **Layered System**  
   The client should not assume it is directly communicating with the end server.

6. **Code on Demand (optional)**  
   Servers can extend client functionality by sending executable code (e.g., JavaScript).

---

## Common HTTP Methods in REST

| Method | Description               | CRUD Equivalent |
| ------ | ------------------------- | --------------- |
| GET    | Retrieve a resource       | Read            |
| POST   | Create a new resource     | Create          |
| PUT    | Update a resource fully   | Update          |
| PATCH  | Update part of a resource | Partial Update  |
| DELETE | Remove a resource         | Delete          |

---

## Example RESTful Endpoints

```http
GET    /students          → Get all students
GET    /students/15       → Get student with ID 15
POST   /students          → Create a new student
PUT    /students/15       → Fully update student with ID 15
DELETE /students/15       → Delete student with ID 15

```

## Advantages of REST

- Simplicity: Based on standard HTTP protocols.

- Performance: Supports caching to reduce server load.

- Scalability: Stateless nature allows horizontal scaling.

- Language Agnostic: Works with any programming language.

- Readability: Clean and intuitive URLs.

## Disadvantages of REST

- No strict standards: Unlike SOAP, REST has flexible design, which can lead to inconsistency.

- Limited in complex operations: May not be ideal for highly transactional or multi-step operations.

- Security: Requires external measures (e.g., HTTPS, tokens) to ensure secure data transmission.

## REST vs. SOAP

| Feature            | REST                | SOAP                    |
| ------------------ | ------------------- | ----------------------- |
| Type               | Architectural style | Protocol                |
| Protocol           | HTTP only           | HTTP, SMTP, more        |
| Message Format     | JSON, XML           | XML only                |
| Simplicity         | Simpler and lighter | More complex            |
| Security Standards | Not built-in        | WS-Security             |
| Performance        | Faster              | Slower due to verbosity |

## When to Use REST

- Complex Applications: Ideal for feature-rich systems like e-commerce platforms.

- Frequent UI Changes: Allows UI updates without changing business logic.

- Reusable Components: Promotes modularity and reuse across projects.

- Testing Requirements: Enables easier unit and integration testing.

## When Not to Use REST

- Simple Applications: Might introduce unnecessary complexity.

- Real-Time Applications: Less suited for instant updates (e.g., live games, chats).

- Tightly Coupled UI and Logic: Could complicate development.

- Limited Resources or Experience: Smaller teams may benefit from simpler patterns.

## Common Use Cases for REST

- Web and mobile app backends

- Microservices communication

- Public APIs for third-party integration

- CRUD operations for databases
