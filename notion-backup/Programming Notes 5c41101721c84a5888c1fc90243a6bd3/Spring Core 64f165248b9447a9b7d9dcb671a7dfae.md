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

## Spring LooseCoupling:

[SpringCore-/src/SpringlooseCoupling at master · MugilanPrabakaran/SpringCore-](https://github.com/MugilanPrabakaran/SpringCore-/tree/master/src/SpringlooseCoupling)

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id ="Dataserviceobject" class = "SimpleProject.Dataservice"></bean>
    <bean id = "HellotunesObject" class="SimpleProject.HelloTunes"></bean>
    <bean id = "SMSserviceObject" class="SimpleProject.SMSservice"></bean>
    <bean id = "ser" class ="SimpleProject.Airtel" >
        <!-- Airtel ser = new Airtel();-->
        <property name="services" ref="Dataserviceobject"></property>
        <!-- ser.setServices(Dataserviceobject);-->
    </bean>
    <bean id = "vod" class ="SimpleProject.Vodafone" >
        <property name="services" ref="HellotunesObject"></property>
    </bean>
</beans>
```

## Spring Auto wire:

Auto wiring is feature in spring which allows us to run  our program without property deceleration.

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean id="heartObject" class="AutowiredinSpring.Heart"/>
    <!-- Heart heartObject = new Heart();-->
    <bean id = "human" class = "AutowiredinSpring.Human">
        <!-- Human human = new Human();-->
        <property name="heart" ref ="heartObject"/><!--Here we don't property in Autowire-->
        <!-- human.setHeart(heartObject);-->
    </bean>
```

While declaring autowire you can use option like below 

![Untitled](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled%202.png)

1. byName 
    - It means autowire inject the  variable of the Object by  name(heart).
    
    ```xml
    <bean id = "heart" class="AutowiredinSpring.Heart"/>
        <!-- Heart heart = new Heart();-->
        <bean id = "human" class = "AutowiredinSpring.Human" autowire="byName"/>
        <!--Human human = new Human();
            human.setHeart(new Heart()):-->
    ```
    
    - Reference variable name and bean id name should be match.
        
        ![Untitled](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled%203.png)
        
    1. byType
        - It defines inject the class which is same type
            
            ```xml
            <bean id = "heartObject" class="AutowiredinSpring.Heart"/>
                <!-- Heart heartObject = new Heart();-->
                <bean id = "human" class = "AutowiredinSpring.Human" autowire="byType"/>
                <!--Human human = new Human();
                    human.setHeart(heartObject):-->
            ```
            
            ![Untitled](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled%204.png)
            
    2. Constructor
        
         It means do the injection when the constructor is there.
        
        ```xml
        <bean id = "heartObject" class="AutowiredinSpring.Heart"/>
            <!-- Heart heart = new Heart();-->
            <bean id = "human" class = "AutowiredinSpring.Human" autowire="constructor"/>
            <!--Human human = new Human();
                human.setHeart(new Heart()):-->
        ```
        
        ## What happen if @Autowired in java program itself?
        
        we need to mention @Autowired in constructer side  and it wiil work if you move @Autowired  to setter method
        
        ```java
        package AutowiredinSpring;
        
        import org.springframework.beans.factory.annotation.Autowired;
        
        public class Human {
            private  Heart heart;
        
            public void setHeart(Heart heart) {
                this.heart = heart;
            }
        @Autowired
            public Human(Heart heart) {
                this.heart = heart;
            }
        public Human(){
        
        }
            public void startPumping(){
                if (heart != null) {
                    heart.pump();
                }
                else {
                    System.out.println("Heart stop beating");
                }
            }
        }
        //Initially autowire is OFF condtion we need turn it ON 
        ```
        
        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <beans xmlns="http://www.springframework.org/schema/beans"
               xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xmlns:context="http://www.springframework.org/schema/context"
               xsi:schemaLocation="http://www.springframework.org/schema/beans
                   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
                   http://www.springframework.org/schema/context
                   http://www.springframework.org/schema/context/spring-context-3.0.xsd">
            
            <!-- Below context code used to TurnON @Autowired in java-->
            <context:annotation-config/>
            <bean id = "heartObject" class="AutowiredinSpring.Heart"/>
            <!-- Heart heart = new Heart();-->
            <bean id = "human" class = "AutowiredinSpring.Human"/>
            <!--Human human = new Human();
                human.setHeart(new Heart()):-->
        ```
        
        ![Untitled](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled%205.png)
        
        ## Spring Qualifier Annotation
        
        why we using spring qualifier annotation?
        
        Autowire search based on above pic , if it  get error, in that case we use “@Qualifier” 
        
        ![Untitled](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled%206.png)
        
        If we are you using Annotation before class then no need for setters and constructors
        
        ```java
        public class Human {
            private Heart heart;
            @Autowired
            @Qualifier("OctopusHeart") //if you are using annotation before  class name setter and getter are no need if any doubt refer Noti 
            public void setHeart(Heart heart) {
                this.heart = heart;
            }
            public Human(Heart heart) {
                this.heart = heart;
            }
        public Human(){
        
        }
            public void startPumping(){
                if (heart != null) {
                    heart.pump();
                    System.out.println("Name of the Animal is : "+ heart.getNameoftheAnimal()+
                            ", No of heart : "+heart.getNoofHeart());
                }
                else {
                    System.out.println("Heart stop beating");
                }
            }
        }
        ```
        
        ![After](Spring%20Core%2064f165248b9447a9b7d9dcb671a7dfae/Untitled%207.png)
        
        After
        
        ## Propertyfiles Injection of “@Value and @Required” Annotation
        
        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <beans xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
               xmlns:context="http://www.springframework.org/schema/context"
               xmlns="http://www.springframework.org/schema/beans"
               xsi:schemaLocation="http://www.springframework.org/schema/beans
                   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
                   http://www.springframework.org/schema/context
                   http://www.springframework.org/schema/context/spring-context-3.0.xsd">
            <!-- it is used to connecting the property files to XML-->
            <context:property-placeholder location="classpath:PropertyfilesInjectuingDemo/injectting-files.properties"/>
            <bean id = "student" class="PropertyfilesInjectuingDemo.Student">
                <!-- we are loading Dynamic values by using ${}-->
               <property name="name" value="${student.name}" />
                <property name="hobby" value="${student.hobby}"  />
                <property  name="Address" value="${student.Address}"/>
            </bean>
        ```
        
        Property files
        
        ```
        student.name = Shrinithi
        student.hobby = Reading
        student.Address = Karaikudi
        ```
        
        ## “@Value” and “@Required”
        
        We can directly inject values using “@Value” Annotation and setting condtion using “@Required”
        
        1. Below we can see the  annotation of direct injecting and Dynamic value injection using property files like above.
        2.  @Required in deprecated in latest  java but if you need hobby value you can set required.
        
        ```java
        package PropertyfilesInjectuingDemo;
        
        import org.springframework.beans.factory.annotation.Required;
        import org.springframework.beans.factory.annotation.Value;
        
        public class Student {
        
            private String name;
            private String hobby;
            private String Address;
            @Value("${student.name}") // Dynamic Value Initilization
            //@Value("Mugilan") //While using @Value annotation  there no need of properties file
            public void setName(String name) {
                this.name = name;
            }
            @Required
            @Value("${student.hobby}")
        //    @Value("Cricket")
            public void setHobby(String hobby) {
                this.hobby = hobby;
            }
        //    @Value("Salem")
            @Value("${student.Address}")
            public void setAddress(String address) {
                Address = address;
            }
        
            public void displayinfo(){
                System.out.println("Student name is : "+ name );
                System.out.println("Student hobby : " + hobby);
                System.out.println("Student Address : " + Address);
            }
        }
        ```
        
        ## “@Component” Annotation
        
        - “@Component” annotation is use to create a bean for class in new way
        - Usually how we declare bean in XML  file like below right?
            
            <aside>
            💡 `<bean id = "collegebean" class = "Annotation_All_in_1.College"/>`
            
            </aside>
            
        - now we are creating Object in java file itself using “@Component”.
            
            <aside>
            💡
            
            </aside>