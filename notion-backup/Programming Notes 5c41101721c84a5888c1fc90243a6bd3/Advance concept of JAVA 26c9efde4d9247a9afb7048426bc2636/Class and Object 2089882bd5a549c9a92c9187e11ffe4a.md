# Class and Object

### What are objects?

- Objects are anything that you see around you. E.g. - your house, table,
chair, bed, etc. Every object has a state and a behaviour.
- Example : if we consider a dog as an example, the state of the dog will be
color, no. of legs, height, weight, etc. Similarly, the behaviour of the dog will
be sleeping, barking, walking, etc.
- Objects can be defined as instances of class in java which means. Objects
have state and behaviour

### What are classes?

- Classes are nothing but a blueprint used to define an object. Classes will
   define all the state and behaviour that you wish objects to have. Classes
   are also known as user defined datatype in java.

### Why do we need classes and objects in Java?

- Java offers primitive data types which can be used normally but if you
need something custom, that is when classes and objects come into
picture
- Java also offers an easy way to simulate real world scenarios with the
help of classes and objects

```java
public class Car {

    public String model;/* Variables*/
    public String color; /*Variables*/
    public int seats;   /*Variables*/

    public void display(){
        System.out.println("Model is : " + model);  /* Method*/
        System.out.println("Color is : " + color);
        System.out.println("Seats is : " + seats);
    }

}
```

```java
public class ClassesMain {
    public static void main(String[] args) {

        Car ferrari = new Car();
        ferrari.model = "Ferrari F430";
        ferrari.seats = 4;
        ferrari.color = "Red";
        ferrari.display();

        Car tesla = new Car();
        tesla.model = "Model S";
        tesla.seats = 4;
        tesla.color = "Black";
        tesla.display();

        Car audi = new Car();
        audi.model = "Audi SQ5";
        audi.color = "Blue";
        audi.seats = 4;
        audi.display();

    }
}

-----------------
Output:

Model is : Ferrari F430
Color is : Red
Seats is : 4
Model is : Model S
Color is : Black
Seats is : 4
Model is : Audi SQ5
Color is : Blue
Seats is : 4
```