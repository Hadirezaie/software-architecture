# Factory Pattern - Comprehensive Guide with Java Examples

## Table of Contents

1. [Introduction to Factory Pattern](#introduction-to-factory-pattern)
2. [Benefits of Using Factory Pattern](#benefits-of-using-factory-pattern)
3. [Simple Factory Pattern Implementation](#simple-factory-pattern-implementation)
4. [Abstract Factory Pattern](#abstract-factory-pattern)
5. [Comparison: Factory vs Abstract Factory](#comparison-factory-vs-abstract-factory)
6. [When to Use Each Pattern](#when-to-use-each-pattern)
7. [Best Practices](#best-practices)
8. [Real-World Applications](#real-world-applications)
9. [Exercises for Practice](#exercises-for-practice)

---

# Introduction to Factory Pattern

The **Factory Pattern** is a creational design pattern that provides an interface for creating objects while allowing subclasses to alter the type of objects that will be created. It promotes loose coupling by eliminating the need to bind application-specific classes into the code.

**Key Concept:**
"Define an interface for creating an object, but let subclasses decide which class to instantiate."

## Benefits of Using Factory Pattern

- ✅ **Reduced Coupling:** Client code doesn't depend on concrete implementations.
- 🏗 **Centralized Object Creation:** Creation logic is encapsulated in one place.
- 🔄**Enhanced Flexibility:** New product types can be added easily.
- 🛠 **Improved Maintainability:** Changes to object creation affect only the factory.
- 📦 **Simplified Complex Initialization:** Factories can handle complex setup logic.

---

## Structure of Factory Pattern

**Components:**

1. **Product Interface/Abstract Class:** Defines the common interface for objects.
2. **Concrete Products:** Implementations of the product interface.
3. **Factory Class:** Contains the creation logic.
4. **Client:** Uses the factory to create objects.

# UML Diagram:

## UML Diagram for Factory Pattern

```text
[Client] --> [Factory]
[Factory] --> [Product]
[Product] <|-- [ConcreteProduct1]
[Product] <|-- [ConcreteProduct2]
```

## Simple Factory Pattern Implementation

1. Product Interface

```java
public interface Shape {
    void draw();
}
```

2. Concrete Products

```java
public class Circle implements Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a Circle");
    }
}

public class Square implements Shape {
    @Override
    public void draw() {
        System.out.println("Drawing a Square");
    }
}
```

3. Factory Class

```java
public class ShapeFactory {
    public Shape getShape(String shapeType) {
        if (shapeType == null) {
            return null;
        }
        if (shapeType.equalsIgnoreCase("CIRCLE")) {
            return new Circle();
        } else if (shapeType.equalsIgnoreCase("SQUARE")) {
            return new Square();
        }
        return null;
    }
}
```

4. Client Code

```java
public class Main {
    public static void main(String[] args) {
        ShapeFactory shapeFactory = new ShapeFactory();

        Shape shape1 = shapeFactory.getShape("CIRCLE");
        shape1.draw();  // Output: Drawing a Circle

        Shape shape2 = shapeFactory.getShape("SQUARE");
        shape2.draw();  // Output: Drawing a Square
    }
}
```

# Abstract Factory Pattern

## Overview

The Abstract Factory Pattern provides an interface for creating families of related or dependent objects without specifying their concrete classes.

**When to Use:**

- When your system needs multiple product families
- When you need to enforce consistency among products
- When you want to hide implementation details from clients

## GUI Theme Example

1. **Abstract Products**

```java
public interface Button {
    void paint();
}

public interface Checkbox {
    void paint();
}
```

2. Concrete Products

```java
// Light Theme
public class LightButton implements Button {
    @Override
    public void paint() {
        System.out.println("Rendering light button");
    }
}

// Dark Theme
public class DarkCheckbox implements Checkbox {
    @Override
    public void paint() {
        System.out.println("Rendering dark checkbox");
    }
}
```

3. Abstract Factory

```java
public interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}
```

4. Concrete Factories

```java
public class LightThemeFactory implements GUIFactory {
    @Override
    public Button createButton() {
        return new LightButton();
    }

    @Override
    public Checkbox createCheckbox() {
        return new LightCheckbox();
    }
}
```

5. Client Code

```java
public class Application {
    private Button button;
    private Checkbox checkbox;

    public Application(GUIFactory factory) {
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void render() {
        button.paint();
        checkbox.paint();
    }
}
```

## Comparison: Factory vs Abstract Factory

| Feature          | Factory Pattern         | Abstract Factory Pattern       |
| ---------------- | ----------------------- | ------------------------------ |
| Purpose          | Creates single objects  | Creates families of objects    |
| Complexity       | Simpler                 | More complex                   |
| Use Case         | Single product type     | Related product families       |
| Extensibility    | Add new products easily | Add new families easily        |
| Client Knowledge | Knows about factory     | Knows only abstract interfaces |

---

# When to Use Each Pattern

## Use Factory Pattern When:

- You need to create objects of a single type
- The creation logic is complex
- You want to decouple client code from concrete classes

## Use Abstract Factory Pattern When:

- Your system needs multiple product families
- You need to enforce product compatibility
- You want to provide a library of products

---

# Best Practices

1. Favor interfaces over concrete implementations
2. Keep factories focused on a single responsibility
3. Consider using dependency injection with factories
4. Document your factory methods clearly
5. Use meaningful names for factory methods

# Real-World Applications

1. JDBC Connection Factory: Creating different database connections
2. Logger Factories: Creating file/console/database loggers
3. UI Toolkit Factories: Creating platform-specific UI components
4. Payment Gateway Factories: Creating different payment processors

---

# Exercises for Practice

1. Extend the ShapeFactory to support Rectangle and Triangle
2. Create a DocumentFactory that can produce PDF, Word, and Excel documents
   3.Implement a cross-platform UI factory for Windows and macOS
3. Design a database factory for MySQL, PostgreSQL, and Oracle
