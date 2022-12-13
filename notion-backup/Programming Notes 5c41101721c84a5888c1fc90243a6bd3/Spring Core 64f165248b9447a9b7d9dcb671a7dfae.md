# Spring Core

**What is Spring?**

- Spring is a Framework to work with java
- Spring helps us to create light weight  application
- Light weight means if we create an class it  contain many object
- If it has many objects we have to declare so it has some weight .
- Less Weight = More Performance

Why we need Spring?

- basically in Java we call function using objects  and call another functions using another object
- In Spring it will take creating objects work via IOC (Inversion of Control)
- IOC is used to create a object in that we can call that object using Spring bean.

![Untitled](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled.png)

Use Below GitHub link get code

[GitHub - MugilanPrabakaran/SpringCore-: This Repo is basically learning for Spring Framework](https://github.com/MugilanPrabakaran/SpringCore-)

## What is Dependency Injection?

- Basically Dependency means  in real life we depend on one thing to sustain a situation.
- Example : 1. Driving licenses ( we cannot drive without license ) 2. Passport(we cannot travel to other country without passport)
- Above examples are the explanation Dependency in real life

```java
For eample :
class Me{   /* Me(Mukil) as a class what Mukil have Family,Job , house no*/
//-------
}
class Family{
}
class Job{
}
/*we are combining all classes into one class*/
class Me{
String name = "Mukil";
int house no ;
Family f; //Dependence in form of object (because it was class before)
Job j ;
```

![Untitled](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled%201.png)

> Basically Dependency Injection is it will insert value in variables without hardcode
> 

### Please Find code for Setter Dependency Injecting  below GitHub .

[GitHub - MugilanPrabakaran/SpringCore-: This Repo is basically learning for Spring Framework](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae.md) 

## Spring Constructor Injection

changes are simply in xml code

1. Why use property ?
    
    If you need to inject values using setter function  then property is the right choice.
    

```xml
<!--below line used to create student object and injecting name in that object -->
    <bean id = "student"  class="DependencyInjectionDemo.studentdetails">
<!-- property is for setter injection -->
        <property name="stuName" value="Mugilan Prabakaran" />
        <property name="id" value="101"/>
    </bean>
<!-- creating constructor injection  -->
    <bean id = "student2"  class="DependencyInjectionDemo.studentdetails">
<!--constructor-arg  is for constructor injection -->
        <constructor-arg name="stuName" value="Shrinithi Kulothungan" />
        <constructor-arg name="id" value="102"/>
    </bean>
```

## Spring Object Injection

For code please visit GitHub 

[SpringCore-/src/Depinjectionobjecttype at master · MugilanPrabakaran/SpringCore-](https://github.com/MugilanPrabakaran/SpringCore-/tree/master/src/Depinjectionobjecttype)

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <!-- Approach 1-->
    <bean id = "stu" class ="Depinjectionobjecttype.Studentdemo" >
        <!-- Here assing value for just sake of creating the object-->
        <property name="id" value="100" > </property>
        <property name="matchcheat">
            <!-- Here we are Notifying spring "Hey Spring it was not a normal value it is Object value"-->
            <bean class ="Depinjectionobjecttype.Mathcheat"></bean>
        </property>
    </bean>
    <!--Example  2 for another student-->
    <bean id = "anstu" class ="Depinjectionobjecttype.AnotherStudent">
        <property name="newcheat">
            <bean class ="Depinjectionobjecttype.Mathcheat"></bean>
        </property>
    </bean>
    <!--Approach 2 -->
    <bean id ="cheatdemo" class = "Depinjectionobjecttype.Mathcheat"></bean>
    <bean id = "stu" class ="Depinjectionobjecttype.Studentdemo" >
        <property name="id" value="100" ></property>
        <property name="matchcheat" ref="cheatdemo"></property>s
    </bean>
    <bean id = "anstu" class ="Depinjectionobjecttype.AnotherStudent">
        <property name="newcheat" ref="cheatdemo"></property>
    </bean>
</beans>
```