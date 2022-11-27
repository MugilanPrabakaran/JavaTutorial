# What is Lambda Expression?

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

### Basic Program for Lambda Expression:

```java
package Firstjava;

interface  Calculator{
//    void onswtich();
//    void sum (int input);
int subtraction(int i1 ,int i2);
}
public class CustoninterfaceDemo {
    public static void main(String[] args) {
//    Calculator calculator = () -> System.out.println("Swicth on");
//    calculator.onswtich();
//        Calculator calculator = (input) -> System.out.println("Sum : " + input);
 //       calculator.sum(56);
		Calculator calculator = (i1,i2) -> i2 - i1;
        System.out.println(calculator.subtraction(8 ,21));

    }
}
----------------
Output:
//Sum : 53
13
```

### Realtime Example of Lambda Expression:

```java
/*Sample Program for  Sorting Book */
import java.util.ArrayList;
import java.util.List;

public class BookDAO {

	public List<Book> getBooks() {
		List<Book> books = new ArrayList<>();
		books.add(new Book(101, "Core Java", 400));
		books.add(new Book(363, "Hibernate", 180));
		books.add(new Book(275, "Spring", 200));
		books.add(new Book(893, "WebService", 300));
		return books;
	}
}
----------------------------------------------
import java.util.Collections;
import java.util.List;

public class BookService {

	/*
	 * ( o1, o2) -> o2.getName().compareTo(o1.getName());
	 * 
	 */
	public List<Book> getBooksinSort() {
		List<Book> books = new BookDAO().getBooks();
		Collections.sort(books, (o1, o2) -> o1.getName().compareTo(o2.getName()));
		return books;
	}

	public static void main(String[] args) {
		System.out.println(new BookService().getBooksinSort());
	}
}

/*
 * class MyComparator implements Comparator<Book> {
 * 
 * @Override public int compare(Book o1, Book o2) { return
 * o2.getName().compareTo(o1.getName()); }
 */
------------------
Output:
[Book [id=101, name=Core Java, pages=400], Book [id=363, name=Hibernate, pages=180], Book [id=275, name=Spring, pages=200], Book [id=893, name=WebService, pages=300]]
```

### Consumer Functional Interface:

- Consumer<T> is an in-built functional interface introduced in Java 8.
- Consumer can be used in all context where an object need to be consumed
- i.e taken as input and some operation is to be performed on the object without returning any result.

/**

*Performs this operation on the given argument.

*@param t the input argument.

*/ 

void accept(T t);

```java
package ConsumerInter;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.function.Consumer;

public class CusDemo  {
/*Traditional Java way to use this method
    @Override
    public void accept(Integer t) {
        System.out.println("print : "+ t);
    }

    public static void main(String[] args) {
        CusDemo c = new CusDemo();
        c.accept(10);
    }*/
    //JAVA 8
public static void main(String[] args) {
/*Consumer c = (t) -> System.out.println("Print : "+ t);
    c.accept(10);*/
 List<Integer> list = Arrays.asList(1,2,3,4,5);
 list.stream().forEach( (t) -> System.out.println("print : "+ t));
}
}
--------------------
Output:
print : 1
print : 2
print : 3
print : 4
print : 5
```

### Predicate Functional Interface:

- This Function interface used for Conditional Statement
- we can use true/False returning functions in day to day programming we should Predicate
- /**
    - Evaluate this predicate on the given argument.
    - @param t the input argument.
    - */
    - Boolean test(T t);
    
    ```java
    package ConsumerInter;
    
    import java.util.function.Predicate;
    //Normal Method 
    /*public class PredicateDemo implements Predicate<Integer> {
    
        @Override
        public boolean test(Integer t) {
            if (t%2 == 0) {
                return true;
            }
            else{
                return false;
            }
        }
    
        public static void main(String[] args) {
            PredicateDemo pd = new PredicateDemo();
            System.out.println(pd.test(10));
        }*/
    //Using JAVA 8
    public class PredicateDemo{
        public static void main(String[] args) {
            Predicate<Integer> p = (t)-> {
                if(t%2 == 0){
                    return true;
                }
                else{
                    return false;
                }
            };
            System.out.println(p.test(11));
        }
    }
    /**/
    Output:
    False
    
    -----------
    public class PredicateDemo{
        public static void main(String[] args) {
    //        Predicate<Integer> p = t -> t % 2 == 0;
    //        System.out.println(p.test(5));
            List<Integer> list = Arrays.asList(1,2,3,4,5);
            //Here using filter method
    //        list.stream().filter(p).forEach( (t) -> System.out.println("print Even: "+ t));
            list.stream().filter(t->t%2==0).forEach( (t) -> System.out.println("print Even: "+ t));
    
        }
    }
    -------
    Output:
    print Even: 2
    print Even: 4
    ```
    

### Supplier Functional Interface:

- Supplier can be used in all context where there is no input but an output is expected.
- 

/**

- Gets a result.
- @return a result
*

T get();

```java
package ConsumerInterface;

import java.util.function.Supplier;

public class SuppllierInterfaceDemo implements Supplier<String> {
    @Override
    public String get() {
        return "Hi Mukilan";
    }

    public static void main(String[] args) {
        SuppllierInterfaceDemo sup = new SuppllierInterfaceDemo();
        System.out.println(sup.get());
    }
}
--------------
Output:
Hi Mukilan
--------------
package ConsumerInterface;

import java.util.function.Supplier;
//Using JAVA 8
public class SuppllierInterfaceDemo {
    public static void main(String[] args) {
         Supplier<String> s = () -> {return "Hi Mugilan";};
//Optimizeing above line
Supplier<String> s = () ->  "Hi Mugilan";
        System.out.println(s.get());
//Using List String
Supplier<String> s = () ->  "Hi Mugilan";
       // System.out.println(s.get());
        List<String> list = Arrays.asList("a","b");
        System.out.println(list.stream().findAny().orElseGet(s));
    }

}
------
Output:
a
//If there is no string it will print 
Hi Mugilan
```