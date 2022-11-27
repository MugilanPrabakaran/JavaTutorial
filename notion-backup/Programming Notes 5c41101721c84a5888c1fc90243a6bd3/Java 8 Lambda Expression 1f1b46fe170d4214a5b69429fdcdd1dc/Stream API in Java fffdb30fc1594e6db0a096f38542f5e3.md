# Stream API in Java

- Stream API is used to process collections of objects.
    - Steam is a sequence of Objects that supports various methods to which can be pipelined
    
    to produce the desired result.
    
- A stream is not a data structure instead it take input from Collections , Arrays or I/O  channels.
- Stream does not change the original data data structure they only provide the result as per the pipelined methods.

## Why we need Stream API?

1. Functional Programming 
2. Code Reduce
3. Bulk Operation

## Methods:

Here we are going to two methods

- Filter → for conditional check
    
    ```java
    package StreaAPIDemo;
    
    import com.sun.jdi.Value;
    
    import java.security.Key;
    import java.util.ArrayList;
    import java.util.HashMap;
    import java.util.List;
    import java.util.Map;
    
    public class ForeachDemo {
        public static void main(String[] args) {
            List<String> list = new ArrayList<>();
            list.add("Mukil");
            list.add("Shri");
            list.add("MukilShri");
            //Normal way of filter
            for(String s : list){
                if (s.startsWith("M")){
                    System.out.println(s);
                }
            }
            //using Java 8
            list.stream().filter((t)-> t.startsWith("M")).forEach(t->System.out.println(t));
            //Normal way of Map
            Map<Integer,String> map = new HashMap<>();
            map.put(1,"a");
            map.put(2,"b");
            map.put(3,"c");
            for (String s : map.values()
                 ) {
                System.out.println(s);
            }
    //        //Optimizing Java 8
            map.entrySet().stream().filter(k->k.getKey()%2==0).forEach(k -> System.out.println(k));
        }
    }
    ------------
    Output:
    Mukil
    MukilShri
    Mukil
    MukilShri
    a
    b
    c
    2=b
    ```
    
- foreach → for iteration
    
    ```java
    package StreaAPIDemo;
    
    import com.sun.jdi.Value;
    
    import java.security.Key;
    import java.util.ArrayList;
    import java.util.HashMap;
    import java.util.List;
    import java.util.Map;
    
    public class ForeachDemo {
        public static void main(String[] args) {
            List<String> list = new ArrayList<>();
            list.add("Mukil");
            list.add("Shri");
            list.add("MukilShri");
            //Normal way of foreach
            for (String s :list){
                System.out.println(s);
            }
            //Java 8
            list.stream().forEach(t-> System.out.println(t));
            //Normal way of Map
            Map<Integer,String> map = new HashMap<>();
            map.put(1,"a");
            map.put(2,"b");
            map.put(3,"c");
            for (String s : map.values()
                 ) {
                System.out.println(s);
            }
            //Using Java 8
            map.forEach((key,value) -> System.out.println(key+" "+value+" ") );
            //Optimizing Java 8
            map.entrySet().stream().forEach(obj -> System.out.println(obj));
    
        }
    }
    --------
    Output:
    Mukil
    Shri
    MukilShri
    Mukil
    Shri
    MukilShri
    a
    b
    c
    1 a 
    2 b 
    3 c 
    1=a
    2=b
    3=c
    
    Process finished with exit code 0
    ```
    

## Real Time Example for Filter & ForEach

```java
package StreaAPIDemo;

import java.util.ArrayList;
import java.util.List;
//DAO layer
public class DataBase {

    public static List<Employee> getEmployees() {
        List<Employee> list = new ArrayList<>();
        list.add(new Employee(176, "Roshan", "IT", 600000));
        list.add(new Employee(388, "Bikash", "CIVIL", 900000));
        list.add(new Employee(470, "Bimal", "DEFENCE", 500000));
        list.add(new Employee(624, "Sourav", "CORE", 400000));
        list.add(new Employee(176, "Prakash", "SOCIAL", 1200000));
        return list;
    }

}
---------------------------
package StreaAPIDemo;

public class Employee {
    private int id;
    private String name;
    private String dept;
    private long salary;

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getDept() {
        return dept;
    }

    public void setDept(String dept) {
        this.dept = dept;
    }

    public long getSalary() {
        return salary;
    }

    public void setSalary(long salary) {
        this.salary = salary;
    }

    public Employee(int id, String name, String dept, long salary) {
        this.id = id;
        this.name = name;
        this.dept = dept;
        this.salary = salary;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "id=" + id +
                ", name='" + name + '\'' +
                ", dept='" + dept + '\'' +
                ", salary=" + salary +
                '}';
    }
}
---------------------------
package StreaAPIDemo;

import java.util.List;
import java.util.stream.Collectors;

public class Taxservice {
    public static List<Employee> evaluteTax(String input) {
//Normal Java 8 code

       /* if (input.equalsIgnoreCase("tax")) {
            return DataBase.getEmployees().stream().filter(emp -> emp.getSalary() > 500000).collect(Collectors.toList());
        } else {
            return DataBase.getEmployees().stream().filter(emp -> emp.getSalary() <= 500000).collect(Collectors.toList());
        }*/
//Optimizing the code
return (input.equalsIgnoreCase("tax"))
                ? DataBase.getEmployees().stream().filter(emp -> emp.getSalary() > 500000).collect(Collectors.toList())
                : DataBase.getEmployees().stream().filter(emp -> emp.getSalary() <= 500000).collect(Collectors.toList());
    }

    }

    public static void main(String[] args) {
        System.out.println(evaluteTax("non tax"));
				//System.out.println(evaluteTax("tax"));
			
    }
}
------------
Output:
[Employee{id=470, name='Bimal', dept='DEFENCE', salary=500000}, Employee{id=624, name='Sourav', dept='CORE', salary=400000}]
//[Employee{id=176, name='Roshan', dept='IT', salary=600000}, Employee{id=388, name='Bikash', dept='CIVIL', salary=900000}, Employee{id=176, name='Prakash', dept='SOCIAL', salary=1200000}]
```