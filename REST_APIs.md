# REST (Representational State Transfer)

## What is REST?

**REST** (Representational State Transfer) is an architectural style for designing networked applications. It was introduced by **Roy Fielding** in his doctoral dissertation in 2000. RESTful APIs use standard HTTP methods to perform operations on resources, making them simple, scalable, and easy to implement.

---

## 1. Key Principles of REST

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

## 2. What is a Resource?

In REST, a **resource** is the core abstraction of information. It refers to anything that can be named, such as:

- A document or image
- A temporal service
- A collection of resources
- A real-world object (e.g., a person)

### Resource Representation

The current state of a resource is called its **representation**, which includes:

- **Data** – The actual content or information
- **Metadata** – Descriptive information about the data
- **Hypermedia Links** – Links that help clients navigate to related resources or states

> Resources and their representations form the foundation of RESTful interactions.

## 2.1 Resource Identifiers

In REST, each resource is uniquely identified using a **resource identifier**, typically a URI (Uniform Resource Identifier).  
These identifiers are used to locate and interact with resources during communication between the client and server.

> Example: `/students/25` identifies the student resource with ID 25.

## 2.2 Hypermedia

The format of a resource’s representation is called a **media type**, which defines how the data should be processed.

A RESTful API resembles hypertext, where every addressable piece of information includes an address. This address can be explicit (like links or IDs) or implicit (derived from the media type and representation structure).

> Hypermedia enables dynamic navigation between resources in RESTful systems.

---

> Hypertext (or hypermedia) means the simultaneous presentation of information and controls such that the information becomes the affordance through which the user (or automaton) obtains choices and selects actions.
>
> Remember that hypertext does not need to be HTML (or XML or JSON) on a browser. Machines can follow links when they understand the data format and relationship types.  
> — Roy Fielding

## 2.3. Self-Descriptive

Resource representations should be **self-descriptive**, meaning the client does not need prior knowledge about the nature of the resource (e.g., whether it's an employee or a device). Instead, clients should rely on the **media type** associated with the resource to understand how to process it.

In practice:

- Custom media types are often created, typically one per resource type.
- Each media type defines a **default processing model**.
  - Example: HTML has a defined rendering process and browser behavior for its elements.

> Media Types have no relation to the resource methods GET/PUT/POST/DELETE/… other than the fact that some media type elements will define a process model that goes like “anchor elements with an href attribute create a hypertext link that, when selected, invokes a retrieval request (GET) on the URI corresponding to the CDATA-encoded href attribute.”

## 2.4 Example

## Hypermedia in REST

A REST resource (e.g., a blog post) can include not only its own data but also **hypermedia links** to related resources, such as the author or comments. These links allow clients to **discover additional information** or **trigger actions** by following them, promoting a more dynamic and discoverable API.

```text
{
  "id": 123,
  "title": "What is REST",
  "content": "REST is an architectural style for building web services...",
  "published_at": "2025-06-12T14:30:00Z",
  "author": {
    "id": 123,
    "name": "John",
    "profile_url": "https://example.com/authors/123"
  },
  "comments": {
    "count": 5,
    "comments_url": "https://example.com/posts/123/comments"
  },
  "self": {
    "link": "https://example.com/posts/321"
  }
}
```

## 3. Common HTTP Methods in REST

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

## 4. REST and HTTP are Not the Same

> It's common for people to compare REST with HTTP, but they are not the same thing.

```text
REST != HTTP
```

While REST aims to bring more structure to the web, Roy Fielding emphasizes strict adherence to its principles. In his dissertation, he did not mandate any specific implementation or protocol—not even HTTP. An interface can be considered RESTful as long as it follows the six guiding principles.

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

## 5. Summary

In REST architecture, **data and functionality are treated as resources** accessed via URIs. These resources are manipulated using a standard set of operations, typically over HTTP (though REST is not limited to it).

Resources are **decoupled from their representations**, allowing clients to access them in formats like JSON, XML, HTML, or JPEG.

Clients and servers exchange resource representations through a **standardized interface**, and metadata is used for caching, error handling, content negotiation, and access control.

A critical principle is **statelessness**—each server interaction must contain all the necessary context.

## These principles make RESTful systems **simple, lightweight, and efficient**.

# Difference Between Stateless and Stateful

Understanding the difference between **Stateless** and **Stateful** is essential in software architecture, especially in web APIs and distributed systems.

---

## ✅ Stateless

In stateless systems:

- Each client request is **independent**.
- All necessary information is included **within the request itself**.
- The server does **not store any client context** between requests.

### ✔ Advantages

- High scalability
- Easier to implement and maintain
- No need for session management on the server

### ❌ Disadvantages

- Repetition of data in every request
- More complexity on the client side

### 🎯 Example

- RESTful APIs using JWT tokens in every request
- Stateless web services

---

## ✅ Stateful

In stateful systems:

- The server **remembers client state** between requests.
- Sessions or other mechanisms are used to **store user context**.

### ✔ Advantages

- Easier interactions for the client
- Suitable for complex, multi-step operations (e.g., shopping cart)

### ❌ Disadvantages

- More difficult to scale
- Requires server-side state management

### 🎯 Example

- Traditional web applications using login sessions
- Online banking systems or e-commerce platforms that store user state

---

## 🆚 Quick Comparison

| Feature             | Stateless               | Stateful                  |
| ------------------- | ----------------------- | ------------------------- |
| Server stores state | ❌ No                   | ✅ Yes                    |
| Request behavior    | Independent             | Depends on previous state |
| Scalability         | Easy                    | Harder                    |
| State storage       | On client (e.g., token) | On server (e.g., session) |
| Common in REST      | ✅ Yes                  | ❌ Usually not            |

---

## ✅ Summary

- **Stateless** systems are ideal for scalable, modular, and modern APIs like REST.
- **Stateful** systems are more suitable for complex, interactive applications where user state must be preserved.
