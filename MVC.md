# MVC Design Pattern ( Model View Controller)

## Table of Content

    What is the MVC Design Pattern?
    Components of the MVC Design Pattern
    Communication between the Components
    Example of the MVC Design Pattern
    Advantages of the MVC Design Pattern
    Disadvantages of the MVC Design Pattern

## What is the MVC Design Pattern?

## The MVC (Model-View-Controller) design pattern is a software architecture approach that divides an application into three core parts: the Model, the View, and the Controller. This separation simplifies code management and maintenance, encourages modular development, and supports component reuse. Each component is responsible for a specific aspect of the application's functionality.

```text
                +-------------+
                | Controller |
                +-------------+
                  ^       |
   Send User      |       | Updates
    Actions       |       v
       -------->  |    +--------+
                  |    | Model  |
                  |    +--------+
                  |       |
                  | Notifies
                  |       v
              +--------+  |
              |  View  | <+
              +--------+
                  ^
                  |
              Updates
```

## Why use MVC Design Pattern?

### The MVC design pattern separates an application into three parts—Model, View, and Controller—allowing for independent development, easier maintenance, better testing, and improved software quality.

## Components of the MVC Design Pattern

```text
User
  |
  | 1. Request
  v
+-------------+
| Controller  |
+-------------+
      |
  2. Contacts
      v
+-------------+
|   Model     |
+-------------+
      |
  Abstraction Layer
      |
      v
+-------------+
|  Database   |
+-------------+
      ^
  3. Returns
      |
      v
+-------------+
| Controller  |
+-------------+
      |
  4. Delivers
      v
+-------------+
|    View     |
+-------------+
      ^
  5. Shows
      |
    User
```
