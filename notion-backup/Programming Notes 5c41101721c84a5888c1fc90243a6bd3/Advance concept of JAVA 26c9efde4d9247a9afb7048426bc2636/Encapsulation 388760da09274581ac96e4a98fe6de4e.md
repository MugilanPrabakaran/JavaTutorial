# Encapsulation

Encapsulation is a oop principle. Encapsulation is wrapping up data and
code into a single unit.

### Private Access Modifier

Variables and methods declared as private can only be access within the
class

### Public Access Modifiers

Variables and methods declared as public can be accessed from anywhere

### How to achieve encapsulation in java?

 Encapsulation can be achieved by following steps :
   ●  Encapsulation in java can be achieved by declaring some variables
as private
   ● Providing getters and setters for the corresponding variables declared
as private

### What are getters and setters?

Getter is a method which only returns the value of a particular variable
declared as private in the class. Method declared as getter are declared as
public
Setter is a method which only updates the value of a particular variable
declared as private in the class. Method declared as setters are declared
as public

### Benefits of encapsulation

- More control over data : You can define what kind of values you want
- Create read only classes

```java
public class Car {
    private int model =2;
    private String name = "TATA";

    public int getModel() {
        return model;
    }

    public void setModel(int model) {
        this.model = model;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

```java
import org.w3c.dom.ls.LSOutput;

public class Main{
    public static void main(String[] args) {
        Car car = new Car();
        System.out.println("Getting the value of Car " + car.getName());
         car.setName("MG Hector ");
        System.out.println("Getting the value of Car " + car.getName());
        System.out.println("Getting the model" + car.getModel());
        car.setModel(8);
        System.out.println("Getting the model" + car.getModel());
    }
}
------------------
Output:
Getting the value of Car TATA
Getting the value of Car MG Hector 
Getting the model2
Getting the model8
```