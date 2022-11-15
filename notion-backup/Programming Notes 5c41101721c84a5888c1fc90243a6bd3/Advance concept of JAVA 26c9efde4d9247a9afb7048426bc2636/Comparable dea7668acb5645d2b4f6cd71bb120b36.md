# Comparable

- Located in java.lang package
- Implementation states that the object of the class can be compared
- Implements compare to (Object) method.

### Syntax:

```java
package java.lang.*
pulic interface comparable<E>{
int compare(E);
}
```

![Untitled](Comparable%20dea7668acb5645d2b4f6cd71bb120b36/Untitled.png)

what is explains is 

1. 1st point denotes is return1 is larger values 
2. 2nd point is return 0 means equal 
3. 3rd point is return -1 means smaller values 

### Basic program for Sort

```java

import java.util.*;

public class Mainclass {
    public static void main(String[] args) {
        ArrayList<Integer> l1 = new ArrayList<>();
        l1.add(21);
        l1.add(33);
        l1.add(11);
        Collections.sort(l1);
        System.out.println(l1);
    }
}
----------------
Output:
[11, 21, 33]
```

What if the requirement is custom like students and roll numbers

```java
public class Student implements Comparable {
   int rollno;
    String stuname;

    public int getRollno() {
        return rollno;
    }

    public String getStuname() {
        return stuname;
    }

    public Student(int rollno, String stuname) {
        this.rollno = rollno;
        this.stuname = stuname;
    }

    @Override
    public int compareTo(Object o) {
        Student s= (Student) o;
        if(this.rollno >s.rollno )return 1;
        else if (this.rollno == s.rollno)return 0;
        else
        return -1;
    }
}
```

```java
import java.security.Key;
import java.util.*;

public class Mainclass {
    public static void main(String[] args) {
     Student s1 = new Student(202,"Jay");
     Student s2 = new Student(101,"Phil");
     ArrayList<Student> studentArrayList = new ArrayList<>();
        studentArrayList.add(s1);
        studentArrayList.add(s2);
     Collections.sort(studentArrayList);

        for (Student s: studentArrayList
             ) {
            System.out.println(s.getRollno()+ "-" + s.getStuname());
        }
    }

}
---------
OutPut:
101-Phil
202-Jay
```