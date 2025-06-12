# MVC Design Pattern ( Model View Controller)

## The MVC (Model-View-Controller) design pattern is a software architecture approach that divides an application into three core parts: the Model, the View, and the Controller. This separation simplifies code management and maintenance, encourages modular development, and supports component reuse.

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
