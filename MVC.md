# MVC Design Pattern ( Model View Controller)

## Table of Contents

- [What is the MVC Design Pattern?](#what-is-the-mvc-design-pattern)
- [Components of the MVC Design Pattern](#components-of-the-mvc-design-pattern)
- [Communication between the Components](#communication-between-the-components)
- [Example of the MVC Design Pattern](#example-of-the-mvc-design-pattern)
- [Advantages of the MVC Design Pattern](#advantages-of-the-mvc-design-pattern)
- [When Not to Use the MVC Design Pattern](#when-not-to-use-the-MVC-design-pattern)

## What is the MVC Design Pattern?

The MVC (Model-View-Controller) design pattern is a software architecture approach that divides an application into three core parts: the Model, the View, and the Controller. This separation simplifies code management and maintenance, encourages modular development, and supports component reuse. Each component is responsible for a specific aspect of the application's functionality.

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

The MVC design pattern separates an application into three parts—Model, View, and Controller—allowing for independent development, easier maintenance, better testing, and improved software quality.

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

## Example of the MVC Design Pattern

```text
+-----------------------+           +---------------------------+
|       Student         |<--------- |     StudentController     |
+-----------------------+           +---------------------------+
| - rollNo: String      |           | - model: Student          |
| - name: String        |           | - view: StudentView       |
|-----------------------|           |---------------------------|
| + getRollNo(): String |           | + StudentController(model:|
| + setRollNo(String):  |           |   Student, view: StudentView): void |
| + getName(): String   |           | + setStudentName(String): void      |
| + setName(String):    |           | + getStudentName(): String          |
|   void                |           | + setStudentRollNo(String): void    |
+-----------------------+           | + getStudentRollNo(): String        |
                                    | + updateView(): void                |
                                    +---------------------------+
                                                |
                                                |
                                                v
                                    +-----------------------------+
                                    |        StudentView          |
                                    +-----------------------------+
                                    | + printStudentDetails(      |
                                    |     name: String,           |
                                    |     rollNo: String): void   |
                                    +-----------------------------+

[Model] -------------> Student
[View]  -------------> StudentView
[Controller] --------> StudentController
```

This class diagram maps directly to the MVC components:

- **Model**: `Student`
- **View**: `StudentView`
- **Controller**: `StudentController`

1. Model (Student class)

The Model holds the student's data (name and roll number) and offers methods to retrieve and update this information.

```java
class Student {
    private String rollNo;
    private String name;

    public String getRollNo() {
        return rollNo;
    }

    public void setRollNo(String rollNo) {
        this.rollNo = rollNo;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

2. View (StudentView class)

The View defines how data (e.g., student details) is presented to the user and includes a method to display the student's name and roll number.

```java
class StudentView {
    public void printStudentDetails(String studentName, String studentRollNo) {
        System.out.println("Student:");
        System.out.println("Name: " + studentName);
        System.out.println("Roll No: " + studentRollNo);
    }
}
```

3. Controller (StudentController class)

The Controller functions as a bridge between the Model and the View. It holds references to both and includes methods to modify the Model and refresh the View accordingly.

```java
class StudentController {
    private Student model;
    private StudentView view;

    public StudentController(Student model, StudentView view) {
        this.model = model;
        this.view = view;
    }

    public void setStudentName(String name) {
        model.setName(name);
    }

    public String getStudentName() {
        return model.getName();
    }

    public void setStudentRollNo(String rollNo) {
        model.setRollNo(rollNo);
    }

    public String getStudentRollNo() {
        return model.getRollNo();
    }

    public void updateView() {
        view.printStudentDetails(model.getName(), model.getRollNo());
    }
}
```

## When to Use the MVC Design Pattern

Consider using the MVC pattern in the following situations:

- **Complex Applications**  
  Ideal for large-scale apps with multiple features and user interactions (e.g., e-commerce platforms), as MVC helps keep the code organized and manageable.

- **Frequent UI Updates**  
  If your application’s interface changes often, MVC allows you to update the View independently from the logic behind it.

- **Component Reusability**  
  The modular design of MVC makes it easier to reuse components across different projects or parts of the same project.

- **Need for Testing**  
  MVC supports better testing practices by allowing you to test the Model, View, and Controller separately, leading to higher code quality.

---

## When Not to Use the MVC Design Pattern

Avoid using the MVC pattern in the following cases:

- **Simple Applications**  
  For basic apps with minimal functionality, MVC can introduce unnecessary overhead. A simpler design might be more efficient.

- **Real-Time Systems**  
  Apps that require instant updates, like live chat or online games, may not perform well with MVC due to its structured flow.

- **Tightly Coupled Logic and UI**  
  If your application’s logic and user interface are deeply interconnected, implementing MVC could complicate development.

- **Limited Resources or Experience**  
  For small teams or developers
