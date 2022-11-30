# Map and Reduce Operation

![Untitled](Map%20and%20Reduce%20Operation%209d6b2a59af8c4189bec4c9c0f277a61e/Untitled.png)

![Untitled](Map%20and%20Reduce%20Operation%209d6b2a59af8c4189bec4c9c0f277a61e/Untitled%201.png)

```java
package MapReduce;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;
import java.util.Optional;
import java.util.stream.IntStream;

public class MapReduceDemo {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(2,3,4,6,3);
        //Normal Method of Sum of number
       int sum =0;
        for (int n:numbers
             ) {
            sum = sum+n;
        }
        System.out.println(sum);
        //using Java 8 using method reference
        int num1 = numbers.stream().mapToInt(Integer::intValue).sum();
        System.out.println(num1);
        //using map
        int sum2 = numbers.stream().reduce(0,(a,b)->a+b);
        System.out.println(sum2);
        //Optimizing the above  code using method reference
        Optional<Integer> sum3 = numbers.stream().reduce(Integer::sum);
        System.out.println(sum3.get());
        //Multiplication
        Integer mul1 = numbers.stream().reduce(1,(a,b)-> a*b);
        System.out.println(mul1);
        //Find the maxvalue
        //(a > b ? a : b) if a > b then return a is max  else b is max --using ternary operator
        Integer maxvalue = numbers.stream().reduce(0,(a,b)->a > b ? a : b);
        System.out.println(maxvalue);
        //Optimizing the above code using method reference
        Integer MaxvaluewithMethodReference  = numbers.stream().reduce(Integer::max).get();
        System.out.println(MaxvaluewithMethodReference);
    //*************************************************************//
        //Find which word is longest
        List<String> words = Arrays.asList("computer science","civil","mechanical");
    //Requirement is about string so Identity is not required
        String longestWord = words.stream().reduce((words1,words2)-> words1.length() > words2.length() ? words1: words2).get();
        System.out.println(longestWord);
        //****Challenge****//
        //1.Get a employee with A grade
        //2.Average of that employee salary

        double emplist = EmployeeDatabase.getEmployees().stream()
                .filter(employee -> employee.getGrade().equalsIgnoreCase("A"))
                .map(Employee::getSalary).mapToDouble(i->i).average().getAsDouble();
        System.out.println(emplist);

        //Same question with sum of salary
        double sumlist = EmployeeDatabase.getEmployees().stream()
                .filter(employee -> employee.getGrade().equalsIgnoreCase("A"))
                .map(Employee::getSalary).mapToDouble(i->i).sum();
        System.out.println(sumlist);
    }
}
-----------
Output:
18
18
18
18
432
6
6
computer science
76666.66666666667
230000.0

Process finished with exit code 0
```