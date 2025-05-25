# Singleton Pattern – Detailed Explanation

## What is the Singleton Pattern?

The **Singleton Pattern** is a **creational design pattern** that ensures a class has **only one instance** and provides a **global point of access** to that instance.

### Why use Singleton?

- When you want to control access to some shared resource (e.g., configuration, logging, database connection).
- To ensure that there is exactly one object managing a specific task.
- To save memory by reusing the single instance instead of creating multiple ones.

---

## Key Characteristics

1. **Single Instance:** Only one object of the class is created.
2. **Global Access:** The instance is accessible globally through a well-known access point (usually a static method).
3. **Lazy Initialization:** The instance is created when it is first needed (optional optimization).
4. **Thread Safety:** In multithreaded environments, special care is needed to ensure only one instance is created.

---

## How Singleton is Implemented

- Make the class constructor **private** to prevent external instantiation.
- Create a **static variable** inside the class to hold the single instance.
- Provide a **public static method** (e.g., `getInstance()`) that returns the single instance.

---

## Example in Python

```python
class Singleton:
    _instance = None

    def __new__(cls):
        if cls._instance is None:
            print("Creating the singleton instance")
            cls._instance = super(Singleton, cls).__new__(cls)
            # Initialization can go here
        return cls._instance

# Usage
obj1 = Singleton()
obj2 = Singleton()

print(obj1 == obj2)  # True, both are the same instance
```
