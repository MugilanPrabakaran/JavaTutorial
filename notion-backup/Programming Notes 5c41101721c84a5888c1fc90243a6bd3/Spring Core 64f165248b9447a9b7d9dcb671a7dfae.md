# Spring Core

**What is Spring?**

- Spring is a Framework to work with java

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