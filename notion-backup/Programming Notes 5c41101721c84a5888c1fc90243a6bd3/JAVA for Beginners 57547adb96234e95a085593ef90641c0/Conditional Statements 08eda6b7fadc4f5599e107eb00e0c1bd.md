# Conditional Statements

Calculator project for Conditional statements

```java
import java.util.Scanner;

class Helloworld {
    public static void main(String[] args) {
        //Declaring the scanner
        Scanner scanner = new Scanner(System.in);
        System.out.println("***Calculator****" +
                "\nSelect an Option to perform Calculation" +
                "\n 1.Addition" +
                "\n 2.Subtraction" +
                "\n 3.Multiplication" +
                "\n 4.Division");
        String option = scanner.nextLine();
        //scanner.nextLine();
        //System.out.printf("You have selected %s ",option);

        if (option.equals("1")) {
            System.out.println("You have selected Addition operation");
            System.out.println("Please Enter Number1");
            double Number1 = scanner.nextInt();
            System.out.println("Please Enter Number2");
            double Number2 = scanner.nextInt();
            System.out.printf("%f + %f = %f", Number1, Number2, Number1 + Number2);
            }
                    else if (option.equals("2")) {
                        System.out.println("You have selected Subtraction operation");
                        System.out.println("Please Enter Number1");
                        double Number1 = scanner.nextInt();
                        System.out.println("Please Enter Number2");
                        double Number2 = scanner.nextInt();
                        System.out.printf("%f - %f = %f", Number1, Number2, Number1 - Number2);
                    }
                    else if (option.equals("3")) {
                        System.out.println("You have selected Multiplication operation");
                        System.out.println("Please Enter Number1");
                        double Number1 = scanner.nextInt();
                        System.out.println("Please Enter Number2");
                        double Number2 = scanner.nextInt();
                        System.out.printf("%f * %f = %f", Number1, Number2, Number1 * Number2);
                    }
                    else if (option.equals("4")){
                        System.out.println("You have selected Divide operation");
                        System.out.println("Please Enter Number1");
                        double Number1 = scanner.nextInt();
                        System.out.println("Please Enter Number2");
                        double Number2 = scanner.nextInt();
                        System.out.printf("%f / %f = %f", Number1, Number2, Number1 / Number2);
                    }
                    else {
                        System.out.println("You have selected wrong option");
                     }
                    

    }
}
--------------------------
Output:
***Calculator****
Select an Option to perform Calculation
 1.Addition
 2.Subtraction
 3.Multiplication
 4.Division
4
You have selected Divide operation
Please Enter Number1
50
Please Enter Number2
2
50.000000 / 2.000000 = 25.000000
Process finished with exit code 0
```