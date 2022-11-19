# Concurrency in Java(Thread)

**What is Multitasking?**
Doing Multiple things together at once is called Multitasking 

### Types of Multitasking:

1. Process Based Multitasking
2. Thread Based Multitasking 

### Process Based Multitasking:

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled.png)

### Thread Based Multitasking:

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%201.png)

### Thread and Multithreading:

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%202.png)

## Lifecycle of Thread:

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%203.png)

### Creating Thread using Thread class:

```java
package FirstPackage;
class Thread1 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("Hello from Thread");
        }
    }
}
public class ThreadDemo {
    public static void main(String[] args) {
        Thread1 t = new Thread1();//creating Thread
        t.run();//Thread Scheduler
        for(int i =0; i<10;i++ )
            System.out.println("Hello from main");
    }
}
-------------
Output:

Hello from Thread
Hello from Thread
Hello from Thread
Hello from Thread
Hello from Thread
Hello from Thread
Hello from Thread
Hello from Thread
Hello from Thread
Hello from Thread
Hello from main
Hello from main
Hello from main
Hello from main
Hello from main
Hello from main
Hello from main
Hello from main
Hello from main
Hello from main

```

## Creating Thread using Runnable Interface:

```java
package FirstPackage;
class Runnableth implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("Hello from Run");
        }
    }
}
public class ThreadDemo {
    public static void main(String[] args) {
        Runnableth runnable = new Runnableth();
        Thread t = new Thread(runnable);
        t.start();//Thread Scheduler
    }
}
------------
Output:
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
```

## Thread Scheduler run() and start()

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%204.png)

- while using start() method new thread is created everytime when you use start() method
- while using run() methods new thread is not creating

```java
package FirstPackage;
class Thread11 extends Thread {
    @Override
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("Hello from Run");
        }
    }
}
public class ThreadDemo {
    public static void main(String[] args) {
        Thread11 t1 = new Thread11();
        Thread11 t2 = new Thread11();
//        t1.start(); 
//        t2.start();
        t1.run();
        t2.run();
        for (int i = 0; i < 10; i++) {
            System.out.println("Hello from Main");
        }
    }
}
----------- 
Output(1): //using start()   output will be diffrent after executing each 
Hello from Main
Hello from Run
Hello from Run
Hello from Run
Hello from Main
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Main
Hello from Main
Hello from Main
Hello from Run

----------------
Output:(2) //using run() output willl be constant for all time
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Main
Hello from Main
Hello from Main
Hello from Main
Hello from Main
```

### Things to remember Multithreading

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%205.png)

### Setting Thread Name:

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%206.png)

```java
package FirstPackage;
class Task implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("Hello from Run");
        }
    }
}
```

```java
package FirstPackage;

public class DemoClass {
    public static void main(String[] args) {
        Thread t = new Thread(new Task());
        System.out.println(t.getName());
        t.setName("Newthread");
        System.out.println(t.getName());
    }
}
----------
Output:
Thread-0
Newthread
```

### Prevention of Execution using yield();

1. yield()
    
    ```java
    package FirstPackage;
    class Task extends Thread {
        @Override
        public void run() {
            //Thread.yield();
            for (int i = 0; i < 5; i++) {
                System.out.println("Hello from Run");
            }
        }
    }
    public class DemoClass {
        public static void main(String[] args) {
            Thread t = new Thread(new Task());
            t.start();
            Thread.yield();//if you use yield it will execute Task after that main wil execute
            for (int i=0; i<5;i++)
                System.out.println("Hello main");
        }
    }
    ------------
    Output:
    
    ```
    
2. sleep()
    1. sleep() is used to pause the function for particular time
    
    ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%207.png)
    
    ```java
    package FirstPackage;
    class Task extends Thread {
        @Override
        public void run() {
            for (int i = 0; i < 5; i++) {
                try {
                    Thread.sleep(2000);//2000 milsec means 2 sec 
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println("Hello from Run");
            }
    
        }
    }
    
        public class DemoClass {
            public static void main(String[] args) {
                Thread t = new Thread(new Task());
                t.start();
            }
        }
    --------------
    Output:
    Hello from Run//it will print each statement after 2 sec 
    Hello from Run
    Hello from Run
    Hello from Run
    Hello from Run
    ```
    
3. join()

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%208.png)

```java
package FirstPackage;
class Task extends Thread {
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            System.out.println("Hello from Run");
        }

    }
}

    public class DemoClass {
        public static void main(String[] args) throws InterruptedException {
            Thread t = new Thread(new Task());
            t.start();
            t.join();//it will exceute after run
            for (int i = 0; i < 5; i++) {
                System.out.println("Hello from Main");
            }
        }
    }
------------------
Output:
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Run
Hello from Main
Hello from Main
Hello from Main
Hello from Main
Hello from Main
```

### Interrupting a Thread:

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%209.png)

```java
package multithreading;

class ThreadClassNormal extends Thread {
    public void run() {
        for (int i = 0; i < 10; i++) {
            System.out.println("Hello from run()");
        }
    }
}

class ThreadClassSleep extends Thread {
    public void run() {
        try {
            for (int i = 0; i < 10; i++) {
                System.out.println("Hello from run() sleep");
                Thread.sleep(1000);
            }
        } catch (InterruptedException e) {
            System.out.println("InterruptedException occur");
        }
    }
}

public class ThreadInterrupt {
    public static void main(String[] args) {
        ThreadClassNormal threadClassNormal = new ThreadClassNormal();
        threadClassNormal.start();
        threadClassNormal.interrupt();

        ThreadClassSleep threadClassSleep = new ThreadClassSleep();
        threadClassSleep.start();
        threadClassSleep.interrupt();
    }
}
```

### Executive Service

1. It is mainly used for limit the usage of multiple threads 
2. if we execute loops for 10 , 10 threads will create 
3. Now we use Executive service like *`ExecutorService* executorService = Executors.*newFixedThreadPool*(4);`
4. Above line we declare threadpool to 4 it means we declare 4 slots to run 
5. so our code will first execute 4 slots after execution the executed slots are free , so waiting threads are able to use free slots to execute 

![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2010.png)

```java
package FiirstPackage;

import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

class Task implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 5; i++) {
            System.out.println("Hello from Run");
        }
    }
}

public class ExecutorServiceExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(4);
        for (int i = 0; i < 10; i++) {
            executorService.execute(new Task());
        }
    }
}
```

### Types of pool in Executive service

1. Single Thread Pool
    1. pic
    
    ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2011.png)
    
    ```java
    package multithreading;
    
    import java.util.concurrent.ExecutorService;
    import java.util.concurrent.Executors;
    
    public class SingleThreadPoolExample {
        public static void main(String[] args) {
            ExecutorService executorService = Executors.newSingleThreadExecutor();
            for (int i = 0; i < 10; i++) {
                executorService.execute(new Task());
            }
        }
    }
    ```
    
2. Fixed Thread Pool
    1. Pic
        
        ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2012.png)
        
        ```java
        public class ExecutorServiceExample {
            public static void main(String[] args) {
                ExecutorService executorService = Executors.newFixedThreadPool(4);
                for (int i = 0; i < 10; i++) {
                    executorService.execute(new Task());
                }
            }
        }
        ```
        
3. Cache  Thread Pool
    1. PIC
        
        ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2013.png)
        
        ```java
        package multithreading;
        
        import java.util.concurrent.ExecutorService;
        import java.util.concurrent.Executors;
        
        public class CachedThreadPoolExample {
            public static void main(String[] args) {
                ExecutorService executorService = Executors.newCachedThreadPool();
                for (int i = 0; i < 10; i++) {
                    executorService.execute(new Task());
                }
            }
        }
        ```
        
4. Schdeule Thread Pool
    1. Pic
        
        ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2014.png)
        
        ```java
        package multithreading;
        
        import java.util.concurrent.Executors;
        import java.util.concurrent.ScheduledExecutorService;
        import java.util.concurrent.TimeUnit;
        
        public class ScheduledThreadPoolExample {
            public static void main(String[] args) {
                ScheduledExecutorService executorService = Executors.newScheduledThreadPool(10);
        
                // Schedules task after delay 10 seconds
                executorService.schedule(new Task(), 10, TimeUnit.SECONDS);
        
                // Schedules task after initial delay of 3 seconds. It will run repeatedly after every 2 seconds
                executorService.scheduleAtFixedRate(new Task(), 3, 2, TimeUnit.SECONDS);
        
                // Schedules task after initial delay of 3 seconds.
                // It will run repeatedly after previous task is completed at delay of every 2 seconds
                executorService.scheduleWithFixedDelay(new Task(), 3, 2, TimeUnit.SECONDS);
            }
        }
        ```
        
        ### Thread Safety
        
        ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2015.png)
        
        Disadvantages of Thread safety:
        
        1.  Thread safety is very slow 
        2. Only one thread is able to execute 
        
        ### Thread Priority
        
        ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2016.png)
        
        ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2017.png)
        
        ```java
        package FiirstPackage;
        class Threadpriority extends Thread {
        
        }
        public class Threadnew {
            public static void main(String[] args) {
            Threadpriority t = new Threadpriority();
                System.out.println(t.getPriority());
                t.setPriority(9);//if you give morethan 10 it will throw error
                System.out.println(t.getPriority());
        
            }
        }
        -----------
        Output:
        5
        9
        ```
        
    
    ## DeadLock:
    
    What is Deadlock?
    
    Deadlock is situation where two process are waiting for each other to finish.
    
    eg: A is waiting for B to finish simultenously B is waiting for A to finish.
    
     
    
    ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2018.png)
    
    ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2019.png)
    
    ```java
    package multithreading;
    
    public class DeadlockDemo {
        public static Object l1 = new Object();
        public static Object l2 = new Object();
    
        public static void main(String[] a) {
            Thread t1 = new Thread1();
            Thread t2 = new Thread2();
            t1.start();
            t2.start();
        }
    
        private static class Thread1 extends Thread {
            public void run() {
                synchronized (l1) {
                    System.out.println("Thread 1: Holding lock 1...");
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                    }
                    System.out.println("Thread 1: Waiting for lock 2...");
                    synchronized (l2) {
                        System.out.println("Thread 2: Holding lock 1 & 2...");
                    }
                }
            }
        }
    
        private static class Thread2 extends Thread {
            public void run() {
                synchronized (l2) {
                    System.out.println("Thread 2: Holding lock 2...");
                    try {
                        Thread.sleep(10);
                    } catch (InterruptedException e) {
                    }
                    System.out.println("Thread 2: Waiting for lock 1...");
                    synchronized (l1) {
                        System.out.println("Thread 2: Holding lock 2 & 1...");
                    }
                }
            }
        }
    }
    ----------------
    Output:
    Thread 1 : Started in Place 1
    Thread 2 : Started in Place 2
    Thread 2 : Waiting to Release Thread 1
    Thread 1 : Waiting to Release Thread 2 ///Output will go infinite until push stop button
    ```
    
    ## Inter Thread Communication:
    
    ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2020.png)
    
    ### Example of consumer and procedure
    
    ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2021.png)
    
    ![Untitled](Concurrency%20in%20Java(Thread)%206f00a8f4c02a4d50aa47ee95a9edb777/Untitled%2022.png)