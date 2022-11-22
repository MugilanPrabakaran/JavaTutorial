# Java 8 Lambda Expression

### What is Lambda Expression?

- The Expression through which we can represent an Anonymous function.
- Anonymous:→ Nameless or Unknown
- Anonymous function → A method who don’t have any name or modifier

Syntax:

Parameter      Expression        Body

()                  →                   System.out.println(”Lamba Syntax”)

```java
package FiirstPackage;

public class Demo {
    public void m(){
        System.out.println("Normal Method/Function");
    }
    (){//How to  call this Lambda Function before that we need to know Function Interface 
        System.out.println("Anonymous Method/Function");//This is Anonymous function
    }

    public static void main(String[] args)
    {
        new Demo().m();
    }
}
```

### What is Functional Interface?

The interface which contains only one abstract method with multiple default and  static method is called Functional Interface.

Eg:

Runnable —> run()

Callable —> call()

Comparator —> compare()

Comparable —> compare To()

```java
public interface CustomFuncInterface {

        void m1();//Abstract Method
        void m5();//not able to declare more than one abstract method

        default void m2(){
            System.out.println("Normal Method");
        }
        default void m3(){
            System.out.println("Normal default Method");
        }
        static void m4(){
            System.out.println("Normal Static Method");
        }

}
```