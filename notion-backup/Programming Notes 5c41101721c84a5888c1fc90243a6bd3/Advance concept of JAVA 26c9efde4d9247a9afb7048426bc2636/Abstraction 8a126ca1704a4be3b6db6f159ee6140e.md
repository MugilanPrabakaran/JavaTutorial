# Abstraction

Abstraction is an oops principle. Abstraction means focusing only on what
is important.

Examples scenarios :

- If you want to travel from San Jose to San Francisco, you will need a
car. Now you are going to ask for a car for this and not a specific car
like Ferrari or Audi.
- If your goal is to stop the car while driving you are going to apply
brakes, now here you won’t care about the specifics like what
happens when you apply brakes or how brakes work.

### How can abstraction be achieved in java?

- Abstract classes and methods
- Interfaces

### What is an abstract class and abstract method?

Abstract class is a class that is declared as abstract using abstract
keywords. Abstract methods are methods without its body.
Points to remember about abstraction.

- Abstract classes and objects can be declared using abstract keyword
- If you declare a single method as abstract in a class, you have to
declare the class as abstract.
- Whenever a class extends an abstract class it has to provide the
definition of the methods declared in parent class as abstract

```java
public class Audi extends Car{
    @Override
    void accelrating() {
        System.out.println("Audi accelrating");
    }

    @Override
    void breaking() {
        System.out.println("Audi breaking");
    }
}
```

```java
public class Ferrai extends Car{
    public static void main(String[] args) {
    }

    @Override
    void accelrating() {
        System.out.println("Ferrai accelrating");
    }

    @Override
    void breaking() {
        System.out.println("Ferrai breaking");
    }
}
```

```java
abstract class Car {
    String name;
    int tyres;
    String colors;

    abstract void accelrating();
    abstract void breaking();
}
```

```java
public class Main {
    public static void main(String[] args) {
        Car car = new Ferrai();
        car.breaking();
        car.accelrating();

        car =new Audi();
        car.breaking();
        car.accelrating();
    }
}
```

```java
Output:
Ferrai breaking
Ferrai accelrating
Audi breaking
Audi accelrating
```