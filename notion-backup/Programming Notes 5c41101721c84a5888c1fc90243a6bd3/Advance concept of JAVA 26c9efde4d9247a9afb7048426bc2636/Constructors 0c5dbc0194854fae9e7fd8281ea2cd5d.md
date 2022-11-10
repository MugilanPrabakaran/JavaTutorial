# Constructors

- Constructor is a piece of code which can be used to initialize objects
- Constructor of the class is executed when the object is created
- Java has a default constructor which is executed when there is no constructor defined
in the class.

### Constructors vs Methods

|  | Constructor | Methods |
| --- | --- | --- |
| Return Type | Constructors have no
return type | Methods can have return type |
| Name | Constructor name
should be same as
class name | Method name can be anything |
| Default Type | Java has a default
constructor | There is no such thing called
default method in java |

Rules for creating constructors
● Constructor should have same name as that class
● Constructors don’t have a return type
● Declaring constructors is not mandatory
● There won’t be any default constructor created by java if you have
declared a constructor
● Constructors cannot be inherited

```java
class Car {
    String carName;
    String color;
    int tyres;

    public Car(){
        carName = "Audi";
        color = "red";
        tyres = 4;
				System.out.println("First constructure");
    }

	/*Second constructure*/
    public Car(String carName, String color, int tyres) {
        this.carName = carName;
        this.color = color;
        this.tyres = tyres;
    }

    public  void display() {
        System.out.println("CAR name is " + carName);
        System.out.println("Car color is "+ color);
        System.out.println("Tyre count is "+ tyres);
    }
}
```

```java
class main {
    public static void main(String[] args) {
        Car car = new Car();
        car.display();
    }
}
```