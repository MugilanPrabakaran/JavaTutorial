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

### Custom Serialization:

```java
package file;

import java.io.*;

class CarCustom implements Serializable{
    String name;
    transient String color;

    public CarCustom(String name, String color) {
        this.name = name;
        this.color = color;
    }
//Below are techinques to custom serialization 
    private void writeObject(ObjectOutputStream objectOutputStream) throws IOException {
        objectOutputStream.defaultWriteObject();
        String colorTemp = "aa"+color;//appending aa before color
        objectOutputStream.writeObject(colorTemp);
    }

    private void readObject(ObjectInputStream objectInputStream) throws IOException, ClassNotFoundException {
        objectInputStream.defaultReadObject();
        String colorTemp = (String) objectInputStream.readObject();
        color = colorTemp.substring(2);//getting color(begining index) after 2 string that is after "aa"
    }

}

public class CustomSerializationDemo {
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        CarCustom car = new CarCustom("Ferrari", "Red");

        //Serialization
        ObjectOutputStream objectOutputStream =
                new ObjectOutputStream(new FileOutputStream("abc.txt"));
        objectOutputStream.writeObject(car);

        //Deserialization
        ObjectInputStream objectInputStream =
                new ObjectInputStream(new FileInputStream("abc.txt"));
        CarCustom car1 = (CarCustom) objectInputStream.readObject();

        System.out.println(car1.name);
        System.out.println(car1.color);
    }
}
---------
Output:
Ferrari
Red
```

### Serialization Inheritance:

```java
import java.io.*;
    class Cardemo implements Serializable{//Parent class is Serialize once 
        String name ;
        String color;
        int tyres;

        public Cardemo(String name, String color, int tyres) {
            this.name = name;
            this.color = color;
            this.tyres = tyres;
        }
    }
    class Ferrai extends Cardemo{
        public Ferrai(String name, String color, int tyres) {
            super(name, color, tyres);
        }
    }
public class SerializationInherit{
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        Cardemo Ferrai1 = new Cardemo("Ferrai","Red",4);
				//Child class automatcially Serialize
        //Serialization
        ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream("new.txt"));
        objectOutputStream.writeObject(Ferrai1);
        //Deserilization
        ObjectInputStream objectInputStream = new ObjectInputStream((new FileInputStream("new.txt")));
        Cardemo Ferrai2 = (Cardemo) objectInputStream.readObject();
        System.out.println(Ferrai2.color);
        System.out.println(Ferrai2.name);
        System.out.println(Ferrai2.tyres);
    }
}
----------
Output:
Red
Ferrari
4
```

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled%203.png)

## Externalization

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled%204.png)

### writeExternal();

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled%205.png)

### readExternal();

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled%206.png)

```java
import java.io.*;
    class Cardemo implements Externalizable{
        String name ;
        String color;
        int tyres;

				public Cardemo() { // empty construtor for .InvalidClassException: Cardemo; no valid constructor
        }

        public Cardemo(String name, String color, int tyres) {
            this.name = name;
            this.color = color;
            this.tyres = tyres;
        }

        @Override
        public void writeExternal(ObjectOutput out) throws IOException {
            out.writeObject(name);
            out.writeObject(color);
            out.writeObject(tyres);
        }

        @Override
        public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
            name = (String) in.readObject();
            color = (String) in.readObject();
            tyres = (int) in.readObject();
        }
    }

public class ExternalizationDemo{
    public static void main(String[] args) throws IOException, ClassNotFoundException {
        Cardemo Ferrai1 = new Cardemo("Ferrai","Red",4);

        //Serialization
        ObjectOutputStream objectOutputStream = new ObjectOutputStream(new FileOutputStream("new.txt"));
        objectOutputStream.writeObject(Ferrai1);
        //Deserilization
        ObjectInputStream objectInputStream = new ObjectInputStream((new FileInputStream("new.txt")));
        Cardemo Ferrai2 = (Cardemo) objectInputStream.readObject();
        System.out.println(Ferrai2.color);
        System.out.println(Ferrai2.name);
        System.out.println(Ferrai2.tyres);
    }
}

-------------
Output1 : //without adding empty constructor
 Exception in thread "main" java.io.InvalidClassException: Cardemo; no valid constructor
	at java.base/java.io.ObjectStreamClass$ExceptionInfo.newInvalidClassException(ObjectStreamClass.java:172)
	at java.base/java.io.ObjectStreamClass.checkDeserialize(ObjectStreamClass.java:791)
	at java.base/java.io.ObjectInputStream.readOrdinaryObject(ObjectInputStream.java:2249)
	at java.base/java.io.ObjectInputStream.readObject0(ObjectInputStream.java:1760)
	at java.base/java.io.ObjectInputStream.readObject(ObjectInputStream.java:538)
	at java.base/java.io.ObjectInputStream.readObject(ObjectInputStream.java:496)
	at ExternalizationDemo.main(ExternalizationDemo.java:37)

Process finished with exit code 1

-------------------
Output2: //with empty constructor
Red
Ferrai
4
```

## Serialization vs Externalization

![Untitled](Serialization%20and%20Deserialization%20254d12673beb4c1ebba0c54b238e3881/Untitled%207.png)