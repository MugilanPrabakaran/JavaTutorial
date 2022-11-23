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