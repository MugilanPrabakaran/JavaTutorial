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
                System.out.println(e.toString());
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