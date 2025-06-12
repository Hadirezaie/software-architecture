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

1. Model
   The data and business logic of an application.

2. View
   Displays the data from the Model to the user and sends user inputs to the Controller.

3. Controller
   The Controller serves as a link between the Model and the View. It processes user input, modifies the Model based on that input, and then updates the View to display the changes.

## Communication Between Components (MVC)

- **User interacts with the View**

  - Example: Clicking a button or entering text.

- **View forwards user input to the Controller**

- **Controller processes the input**

  - Interprets the action and applies logic.

- **Controller updates the Model**

  - Modifies data based on input or logic.

- **Model notifies the View of changes**

- **View requests updated data from the Model**

- **Controller may also update the View directly**

- **View renders the updated user interface**

> This flow ensures each component has a specific role, improving maintainability and scalability of the application.
