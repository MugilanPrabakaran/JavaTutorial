# Parallel Stream

![Untitled](Parallel%20Stream%20b0f2f38e13af4c2196d740c1e23a6156/Untitled.png)

![Untitled](Parallel%20Stream%20b0f2f38e13af4c2196d740c1e23a6156/Untitled%201.png)

```java
package ParallelStream;

import MapReduce.Employee;
import MapReduce.EmployeeDatabase;

import java.util.List;
import java.util.stream.IntStream;

public class ParallelStreamDemo {
    public static void main(String[] args) {
        //Initializing the time
        long start = 0;
        long end = 0;
        //Normal Stream
        start = System.currentTimeMillis();
        IntStream.range(1,100).forEach(System.out::println);
        end = System.currentTimeMillis();
        System.out.println("Normal Stream timing : "+(end-start));

        System.out.println("==========================================");
        //Parallel Stream
        start = System.currentTimeMillis();
        IntStream.range(1,100).parallel().forEach(System.out::println);
        end = System.currentTimeMillis();
        System.out.println("Normal Stream timing : "+(end-start));
        //Find Thread name and time
        IntStream.range(1,10).forEach(x->{
            System.out.println("Thread : "+Thread.currentThread().getName()+" : "+x);
        });
        IntStream.range(1,10).parallel().forEach(x->{
            System.out.println("Thread : "+Thread.currentThread().getName()+" : "+x);
        });
        List<Employee> employees = EmployeeDatabase.getEmployees();

        //normal
        start=System.currentTimeMillis();
        double salaryWithStream = employees.stream()
                .map(Employee::getSalary).mapToDouble(i -> i).average().getAsDouble();
        end=System.currentTimeMillis();

        System.out.println("Normal stream execution time : "+(end-start)+" : Avg salary : "+salaryWithStream);
        //Parallel Stream
        start=System.currentTimeMillis();
        double salaryWithParallelStream = employees.parallelStream()
                .map(Employee::getSalary).mapToDouble(i -> i).average().getAsDouble();

        end=System.currentTimeMillis();

        System.out.println("Parallel stream execution time : "+(end-start)+" : Avg salary : "+salaryWithParallelStream);

    }
}
--------
Output: //output for double stream types
Normal stream execution time : 16 : Avg salary : 505368.3243243243
Parallel stream execution time : 0 : Avg salary : 505368.3243243243

```