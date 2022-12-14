# Exceptions

What are exceptions in java?
Exceptions by definition are unexpected, unwanted events which prevents
normal execution of the program. In programming world you might face
scenarios where in normal flow of program is disrupted because of some
unexpected event
Example :

1. Suppose you are reading a file from the remote server. For some
reason remote file is not accessible, this unwanted event is called
exception FileNotFoundException is thrown
2. If you are reading data from a database you have a flow. Open db
connection → read data → close db connection. If there is some
exception while read data then program will terminate and throw
exception
3. If you are preparing a presentation and you missed saving and
suddenly power is gone. You will lose your work. Here power cut is
exception.

### Runtime Stack Mechanism

![Screenshot_20221109_082116.png](Exceptions%20d655eb61cfa34f3ab07b481d5703f1d4/Screenshot_20221109_082116.png)

### Default Exception

```java
public  class Expdemo{
    public static void main(String[] args) {
        Expdemo a = new Expdemo();
        a.A();
    }
    void A(){
        B();
    }
    void B() {
        System.out.println(10/0);
    }
}
----------
Output:
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at Expdemo.B(Expdemo.java:10)
	at Expdemo.A(Expdemo.java:7)
	at Expdemo.main(Expdemo.java:4)
```

Exception Hierarchy 

![Screenshot_20221109_092147.png](Exceptions%20d655eb61cfa34f3ab07b481d5703f1d4/Screenshot_20221109_092147.png)

### Basic Exception Handling

```java
public  class Expdemo{
    public static void main(String[] args) {
        System.out.println("First Phase");
        try {
            System.out.println(10/0);
        } catch (Exception e) {
            System.out.println(10/2);
        }
        System.out.println("Last Phase after Exception");
    }
}
---------
Output:
First Phase
5
Last Phase after Exception
```

### Flow of Try and Catch

There are Four types flow in Try and catch

1. If there is no exception catch statement will not execute 

```java
public  class Expdemo{
    public static void main(String[] args) {

        try {
            System.out.println("Statement 1");
            System.out.println("Statement 2");
            System.out.println("Statement 3");
        } catch (Exception e) {
            System.out.println("Statement 4");
        }
        System.out.println("Statement 5");
    }
}
--------
Output:
Statement 1
Statement 2
Statement 3
Statement 5
```

1. If exception occurs next statement will not execute 

```java
public  class Expdemo{
    public static void main(String[] args) {

        try {
            System.out.println("Statement 1");
            System.out.println(10/0);
            System.out.println("Statement 3");
        } catch (Exception e) {
            System.out.println(10/2);
        }
        System.out.println("Statement 5");
    }
}
-------------
Output:
Statement 1
5
Statement 5
```

1. what if wrong exception in catch

```java
ublic  class Expdemo{
    public static void main(String[] args) {

        try {
            System.out.println("Statement 1");
            System.out.println(10/0);
            System.out.println("Statement 3");
        } catch (NullPointerException e) {
            System.out.println(10/2);
        }
        System.out.println("Statement 5");
    }
}
---------
Output:
Statement 1
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at Expdemo.main(Expdemo.java:6)
```

1. What if Exception Catch statement also have exception

```java
public  class Expdemo{
    public static void main(String[] args) {

        try {
            System.out.println("Statement 1");
            System.out.println(10/0);
            System.out.println("Statement 3");
        } catch (Exception e) {
            System.out.println(10/0);
            System.out.println("Statement 4");
        }
        System.out.println("Statement 5");
    }
}
------------
Output:
Statement 1
Exception in thread "main" java.lang.ArithmeticException: / by zero
	at Expdemo.main(Expdemo.java:9)
```

### Methods of Printing Exception Messages

There are three types of error messages 

1. PrintStackTrace
    
    ```java
    public  class Expdemo{
        public static void main(String[] args) {
    
            try {
                System.out.println("Statement 1");
                System.out.println(10/0);
                System.out.println("Statement 3");
            } catch (Exception e) {
                e.printStackTrace();
            }
            System.out.println("Statement 5");
        }
    }
    ------------
    Output:
    Statement 1
    Statement 5
    java.lang.ArithmeticException: / by zero
    	at Expdemo.main(Expdemo.java:6)
    ```
    
2. toString()
    
    ```java
    public  class Expdemo{
        public static void main(String[] args) {
    
            try {
                System.out.println("Statement 1");
                System.out.println(10/0);
                System.out.println("Statement 3");
            } catch (Exception e) {
                System.out.println(e.toString());d
            }
            System.out.println("Statement 5");
        }
    }
    ----------
    Output:
    Statement 1
    java.lang.ArithmeticException: / by zero
    Statement
    ```
    
3. getMessage()
    
    ```java
    
    public  class Expdemo{
        public static void main(String[] args) {
    
            try {
                System.out.println("Statement 1");
                System.out.println(10/0);
                System.out.println("Statement 3");
            } catch (Exception e) {
                System.out.println(e.getMessage());
            }
            System.out.println("Statement 5");
        }
    }
    -------
    Output:
    Statement 1
    / by zero
    Statement 5
    ```
    
    ### Final vs Finally vs Finalize
    
    **Final Keyword:**
    
    - Final is a modifier applicable for classes, methods and variables
    - If a class is final then we can’t extend that class, we can't inherit class
    neither we can create child class of that class
    
    **Finally Keyword:**
    
    - Finally is a block associated with try catch to maintain clean up code
    - The specialty of finally block is it will be executed irrespective of whether
    exception is raised or not raised and weather handled or not handled.
    
    ```java
    try{
    // code that generates exception
    } catch(Exception e){
    // handling code
    } finally {
    // clean up code
    }
    ```
    
    **Finalize Keyword:**
    
    - Finalize is a method always invoked by garbage collector just before
    destroying an object to perform cleanup activities.
    - Once the finalize method is completed immediately the garbage collector destroys that object.
    
    ## Throw Keyword:
    
    ```java
    class Expdemo {
    public static void main(String args[]){
    System.out.println(10/0);
    }
    }
    ```
    
    1. In the above example, the main method is creating the exception object
    and handing it over to jvm. Which means exception object is created
    implicitly and being handed over to jvm however sometimes we may want
    to create exception object explicitly and hand it over to jvm
    
    $$
    
    What is Throw Keyword?
    $$
    
    Throw keyword is used to create an exception object manually and hand it
    over to the jvm.
    
    **Syntax:**
    
    > <Exception-name> ex = new <Exception-name>("message");
    throw ex;
    > 
    
    > throw new <exception-name>("message");
    > 
    
    ### **Program1:**
    
    ```java
    public  class Expdemo {
        public static void main(String[] args) {
            System.out.println(10 / 0);
        }
    }
    ```
    
    Here, the main method is responsible to create an exception object and
    hand it over to jvm.
    
    ### **Program2:**
    
    ```java
    public  class Expdemo {
        public static void main(String[] args) {
            throw new ArithmeticException("/ by zero");
        }
    }
    ```
    
    Here, programmers are responsible to create the exception object explicitly
    and hand it over to jvm.
    
    ### Rule No 1:
    
    If exception object is not initialized then we get NullPointerException
    
    ```java
    public  class Expdemo {
        static ArithmeticException e = new ArithmeticException();
        public static void main(String[] args) {
            throw e;
        }
    ```
    
    ```java
    public  class Expdemo {
        static ArithmeticException e;
        public static void main(String[]args) {
            throw e;
        }
    }
    ------
    Output:
    Exception in thread "main" java.lang.NullPointerException: Cannot throw exception because "Expdemo.e" is null
    	at Expdemo.main(Expdemo.java:4)
    ```
    
    This code will throw NullPointerException. Since we have not initialized the
    ArithmeticException object.
    
    ### Rule No 2:
    
    After throw statement, we are not allowed to write any statement
    directly else we will get compile time error saying : “Unreachable
    statement”
    
    ```java
    class Expdemo {
    public static void main(String args[])(){
    System.out.println(10/0);
    System.out.println("hello");
    }
    }
    ```
    
    ![Compile time error unreachable statement](Exceptions%20d655eb61cfa34f3ab07b481d5703f1d4/Untitled.png)
    
    Compile time error unreachable statement
    
    ### Rule No 3:
    
    We can use the throw keyword only for throwable types. If we are
    trying to use for normal java objects we will get compile time error saying :
    “Incompatible types required java.lang.throwable”
    
    ![Untitled](Exceptions%20d655eb61cfa34f3ab07b481d5703f1d4/Untitled%201.png)
    
    Compile time error:
    java: incompatible types: Expdemo cannot be converted to java.lang.Throwable
    
    ```java
    public  class Expdemo extends RuntimeException {
        public static void main(String[] args) {
            throw new Expdemo();
        }
    }
    -----
    Output:
    Exception in thread "main" Expdemo
    	at Expdemo.main(Expdemo.java:3)
    ```
    
    Throws Keyword
    
    If there is a possibility of our code raising a checked exception then we will
    get a compile time error if we don’t handle it
    
    ![Untitled](Exceptions%20d655eb61cfa34f3ab07b481d5703f1d4/Untitled%202.png)
    
    - Above code have checked exception “FileNotFound Exception” In that case we can handle it two types
    1. **Using Try catch :**
    
    ```java
    public class Expdemo{
        public static void main(String[] args) {
            try {
                PrintWriter out = new PrintWriter("abc.txt");
            } catch (FileNotFoundException e) {
            }
        }
    ```
    
    1. **Using Throws Keyword:**
    
    ```java
    public class Expdemo{
        public static void main(String[] args) throws FileNotFoundException {
            PrintWriter out = new PrintWriter("abc.txt");
        }
    }
    ```
    
    **Adding PDF  for better understanding of Rules in Throws**
    
    [22428501-Throws-keyword.pdf](Exceptions%20d655eb61cfa34f3ab07b481d5703f1d4/22428501-Throws-keyword.pdf)
    
    ## **Custom Exceptions**
    
    Custom expections created by developers for their usage .If they want to have IncorrectAccountExceptions , InvalidNameExceptions , like they can create it , it is called custom exceptions
    
    ```java
    import java.util.Scanner;
    
    public class customException{
        public static void main(String[] args) {
            Scanner input = new Scanner(System.in);
            System.out.println("What is your age ? ");
            int age = input.nextInt();
            if (age < 18 ){
               throw new TooYoungException("you are too young");
            } else if (age > 55) {
               throw new TooOldException("Tou are too old");
            }
            else{
                System.out.println("your details will be available");
            }
    
        }
    }
    -----------------
    Output:
    What is your age ? 
    66
    Exception in thread "main" TooOldException: Tou are too old
    	at customException.main(customException.java:11)
    ```
    
    ```java
    public class TooOldException extends RuntimeException{
        public TooOldException(String message) {
            super(message);
        }
    }
    ```
    
    ```java
    public class TooYoungException extends RuntimeException{
        public TooYoungException(String message) {
            super(message);
        }
    }
    ```
    
    **Point to Remember**
    
    - We mention super() in customized exception class to make
    description available to default exception handler
    - It is highly recommended to define custom exceptions as unchecked
    ie. We have to extend RuntimeException but not Exception.
    - Throw keyword is best suitable for user defined or customized
    exceptions but not for predefined exceptions