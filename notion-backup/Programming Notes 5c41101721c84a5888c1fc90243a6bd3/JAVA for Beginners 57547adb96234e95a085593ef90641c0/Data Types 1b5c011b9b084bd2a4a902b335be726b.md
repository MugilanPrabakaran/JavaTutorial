# Data Types

Now we are going to see Data 

1. There are two types of data
    - Primitive Types
        - It store a integer values
        - There are 8 primitive types
        - Out of 8 , 6 types are numbers
        
        ```java
        		byte aSingleByte = 100 ; // -128 to 127
            short aSmallNumber = 20000 ; // -32,768 to 32,767
            int anInteger = 2147483647 ; // -2147483648 to 2147483647
            long aLargeNumber = 9223372036854775807L ; // -9223372036854775808 to 9223372036854775807
            // decimal types
            double aDouble = 1.79769313 ; // 4.9E - 324 to 1.7976931348623157E308
            float aFloat = 3.4028F ; // 1.4E - 45 to 3.4028235E38
        ```
        
    - Non-Primitive Types or Reference Types
        
        It stores reference to a  memory location  where a dynamic object is bring stored 
        

```java
class HelloWorld {
  public static void main ( String [ ] args ) {
    // integer types
    byte aSingleByte = 100 ; // -128 to 127
    short aSmallNumber = 20000 ; // -32,768 to 32,767
    int anInteger = 2147483647 ; // -2147483648 to 2147483647
    long aLargeNumber = 9223372036854775807L ; // -9223372036854775808 to 9223372036854775807
    // decimal types
    double aDouble = 1.79769313 ; // 4.9E - 324 to 1.7976931348623157E308
    float aFloat = 3.4028F ; // 1.4E - 45 to 3.4028235E38
    // booleans
    boolean isWeekend = false ;
    boolean isWorkday = true ;
    // characters
    char copyrightSymbol = ' \ u00A9 ' ;
    System.out.println ( " This is the copyright symbol" +copyrightSymbol ) ;
		}
}
 -------------------------------------------
Output:
This is the copyright symbol©
                                                             
```

1. Implicit or Narrowing type conversion
- Int to double conversion
    
    ```java
    class main {
        public static void main(String[] args) {
            int number1 =5;
            double number2 = number1;
            System.out.println(number2);
        }
    }
    --------------------------
    Output:
    5.0
    ```
    
- Double to Int
    
    ```java
    class main {
        public static void main(String[] args) {
            double number1 =5.4;
            int number2 =number1;
            System.out.println(number2);
        }
    }
    ----------------
    Output:
    java: incompatible types: possible lossy conversion from double to int
     
    ```
    
    we can still do it manually by using int 
    
    ```java
    class main {
        public static void main(String[] args) {
            double number1 =5.4;
            int number2 =(int)number1;
            System.out.println(number2);
        }
    }
    -----------------------
    Output:
    5
    ```