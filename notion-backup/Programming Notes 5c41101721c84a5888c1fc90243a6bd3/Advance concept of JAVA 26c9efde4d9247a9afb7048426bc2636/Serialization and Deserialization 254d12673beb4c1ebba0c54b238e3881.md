# Serialization and Deserialization

What is Serialization and Deserialization?

- Converting JVM ordinary Object to File is called Serialization
- repeating the process Serialization process is called Deserialization

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled.png)

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled%201.png)

```java
package file;

import java.io.*;

class Car implements Serializable {
    String name;
    String color;

    public Car(String name, String color) {
        this.name = name;
        this.color = color;
    }
}

public class SerializationDeserializationDemo {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        Car car = new Car("Ferrari", "Red");

        //Serialization
        //FileOutputStream fileOutputStream = new FileOutputStream("abc.txt");
        ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream("abc.txt"));
        objectOutputStream.writeObject(car);

        //Deserialization
        //FileInputStream fileInputStream = new FileInputStream("abc.txt");
        ObjectInputStream objectInputStream = new ObjectInputStream(new FileInputStream("abc.txt"));
        Car car1 = (Car) objectInputStream.readObject();

        System.out.println(car1.color);
        System.out.println(car1.name);
    }
}
```

## Transient Keyword:

- Mainly Transient keyword is used to not serialize particular Variables like.. If you are serializing an object of username and password so you need to decide not to serialize password alone
- In that case we can use Transient Keyword

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled%202.png)

```java
package file;

import java.io.*;

class Car implements Serializable {
    String name;
    transient String color;//using transient here 

    public Car(String name, String color) {
        this.name = name;
        this.color = color;
    }
}

public class SerializationDeserializationDemo {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        Car car = new Car("Ferrari", "Red");

        //Serialization
        //FileOutputStream fileOutputStream = new FileOutputStream("abc.txt");
        ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream("abc.txt"));
        objectOutputStream.writeObject(car);

        //Deserialization
        //FileInputStream fileInputStream = new FileInputStream("abc.txt");
        ObjectInputStream objectInputStream = new ObjectInputStream(new FileInputStream("abc.txt"));
        Car car1 = (Car) objectInputStream.readObject();

        System.out.println(car1.color);
        System.out.println(car1.name);
    }
}
------------
Output:
//Without transient 
Red
Ferrari
//using tranient 
null
Ferrari
```