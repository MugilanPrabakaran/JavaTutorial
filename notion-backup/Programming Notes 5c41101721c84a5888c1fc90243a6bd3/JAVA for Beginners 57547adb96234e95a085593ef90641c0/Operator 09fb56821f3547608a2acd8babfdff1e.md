# Operator

Java or programming in general are certain symbols that build the compiler to perform certain operations such as arithmetic relational or logical operations although there are six types of operators in Java.

### 1.Arithmetic operator

- Basically Arithmetic operator used for basic calculation like addition ,subtraction  ,multiply and divide.

```java
class Helloworld {
  public static void main ( String [ ] args ) {
    int number1 = 12 ;
    int number2 = 6 ;
    // addition
    System.out.println ( number1 + number2 ) ; // 18
    // subtraction
                                             I
    System.out.println ( number1 - number2 ) ; // 6
    // multiplication
    System.out.println ( number1 * number2 ) ; // 72
    // division
    System.out.println ( number1 / number2 ) ; // 2
    // remainder ( modulo / modulus )
    System.out.println ( number1 % number2 ) ; // 0
	}
}
--------------------------
Output:
18
6
72
2
0
```

### 2.Assignment operator

- Assignment is lets you assign different kind of  value to the variables.

```java
class Helloworld {
    public static void main ( String [ ] args ) {
        int number = 12 ;
        number +=  5;
        System.out.println ( number ) ;
    }
}
```

### 3.Realtional Operator

- Relational operator used for find the relationship between variables like finding greatest among two numbers

```java
class HelloWorld {
  public static void main ( String [ ] args ) {
    int number1 = 12 ;
    int number2 = 15 ;
    // is equal to
    System.out.println ( number1 == number2 ) ;
    // is not equal to
    // System.out.println ( number1 ! = number2 ) ;
    // is greater than
    // System.out.println ( number1 > number2 ) ;
    // is less than
    // System.out.println ( number1 < number2 ) ;
                                              I
    // is greater than or equal to
    // System.out.println ( number1 > = number2 ) ;
    // is less than or equal to
    // System.out.println ( number1 < = number2 ) ;
	}
}
-----------------------------
Output:
false
```

### 4. Logical Operators

- Logical Operators are based on the logical decision based on condition.
- It mainly uses AND(&&), OR( | | ) and NOT(!)
- AND(&&) means both condition needs to true

```java
class HelloWorld {
public static void main(String[] args) {
int age = 25;
// age >= 18
// age <= 40

System.out.println(age >= 18 && age <= 40);
}
-------------------------
Output:
TRUE
```

- OR( | | ) means needs to stratify any one condition

```java
class Helloworld {
    public static void main ( String [ ] args ) {
       boolean isStudent = true;
       boolean isLibarary = false;

       System.out.print(isStudent || isLibarary);
    }
}
------------------------------
Output:
true
```

- NOT (!) means it direct the opposite meaning of variables

```java
class Helloworld {
    public static void main ( String [ ] args ) {
       boolean isStudent = true;
       boolean isLibarary = false;

       System.out.print(!isStudent || isLibarary);
    }
}
------------------------------
Output:
false
```

### 5. Unary Operator

- Unary operator is works in the process of Increment and Decrement
- (++ ) → denotes Increment and ( -- ) → denotes Decrement

```java
INCREMENT:

class Helloworld {
    public static void main ( String [ ] args ) {
        int myAge = 12 ;
        System.out.println ( myAge ++) ;
        System.out.println ( myAge) ;
    }
}
------------
Output:
12
13

DECREMENT:

class Helloworld {
    public static void main ( String [ ] args ) {
        int myAge = 12 ;
        System.out.println ( myAge --) ;
        System.out.println ( myAge) ;
    }
}
-----------------
Output:
12
11
```

- What if Increment start from left ?

```java
INCREMENT:

class Helloworld {
    public static void main ( String [ ] args ) {
        int myAge = 12 ;
        System.out.println ( ++ myAge ) ;
        System.out.println ( myAge) ;
    }
}
------------
Output:
13
13

DECREMENT:

class Helloworld {
    public static void main ( String [ ] args ) {
        int myAge = 12 ;
        System.out.println ( -- myAge ) ;
        System.out.println ( myAge) ;
    }
}
-----------------
Output:
11
11
```