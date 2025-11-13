Question 1: Room Class
java
class Room {
    int no;
    String type;
    float area;
    boolean ac;

    void set(int n, String t, float a, boolean c) {
        no = n; type = t; area = a; ac = c;
    }

    void show() {
        System.out.println(no + " " + type + " " + area + " " + ac);
    }

    public static void main(String[] args) {
        Room r = new Room();
        r.set(101, "Deluxe", 250.5f, true);
        r.show();
    }
}
Question 2(i): Static Variables, Methods, and Blocks
java
class StaticEx {
    static int x = 0;

    static void show() {
        x++;
        System.out.println("Count: " + x);
    }

    public static void main(String[] args) {
        show();
        show();
    }
}
Question 2(ii): Greatest Among Three Numbers
java
class Greatest {
    public static void main(String[] args) {
        int a = 10, b = 25, c = 15;
        if (a > b && a > c)
            System.out.println(a + " is greatest");
        else if (b > c)
            System.out.println(b + " is greatest");
        else
            System.out.println(c + " is greatest");
    }
}
Question 3(i): Method Overriding Example
java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}
class Dog extends Animal {
    void sound() {
        System.out.println("Dog barks");
    }
}
class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.sound();
    }
}
Question 3(ii): Super Keyword Example
java
class Parent {
    int a = 10;
}
class Child extends Parent {
    int a = 20;
    void show() {
        System.out.println("Parent a: " + super.a);
        System.out.println("Child a: " + a);
    }
    public static void main(String[] args) {
        Child c = new Child();
        c.show();
    }
}
Question 4: Polymorphism with Shape and Subclasses
java
class Shape {
    void draw() { System.out.println("Drawing Shape"); }
}
class Circle extends Shape {
    void draw() { System.out.println("Drawing Circle"); }
}
class Triangle extends Shape {
    void draw() { System.out.println("Drawing Triangle"); }
}
class Square extends Shape {
    void draw() { System.out.println("Drawing Square"); }
}
class Main {
    public static void main(String[] args) {
        Shape s;
        s = new Circle(); s.draw();
        s = new Triangle(); s.draw();
        s = new Square(); s.draw();
    }
}
Question 5: Outer and Inner Class with Display Functions
java
class Outer {
    void display() {
        System.out.println("Outer class display");
    }
    class Inner {
        void display() {
            System.out.println("Inner class display");
        }
    }
    public static void main(String[] args) {
        Outer o = new Outer();
        o.display();
        Outer.Inner i = o.new Inner();
        i.display();
    }
}
Question 6: Box and Box3D Classes with Constructor, Area, and Volume
java
class Box {
    int l, b;
    Box(int x, int y) {
        l = x; b = y;
    }
    int area() {
        return l * b;
    }
}
class Box3D extends Box {
    int h;
    Box3D(int x, int y, int z) {
        super(x, y);
        h = z;
    }
    int volume() {
        return l * b * h;
    }
    public static void main(String[] args) {
        Box3D obj = new Box3D(2, 3, 4);
        System.out.println("Area: " + obj.area());
        System.out.println("Volume: " + obj.volume());
    }
}
Question 7: Multiple Catch Statements Example
java
class MultiCatch {
    public static void main(String[] args) {
        try {
            int a = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Arithmetic Exception");
        } catch (Exception e) {
            System.out.println("Exception Occurred");
        }
    }
}
Question 8: Try-Catch with Finally Clause
java
class TryFinally {
    public static void main(String[] args) {
        try {
            int a = 10 / 0;
        } catch (ArithmeticException e) {
            System.out.println("Exception caught");
        } finally {
            System.out.println("Finally block executed");
        }
    }
}
Question 9: User Defined Exception
java
class MyException extends Exception {
    MyException(String msg) {
        super(msg);
    }
}
class Test {
    public static void main(String[] args) {
        try {
            throw new MyException("User Defined Exception");
        } catch (MyException e) {
            System.out.println(e.getMessage());
        }
    }
}
Question 10: File Creation and Write using OutputStream
java
import java.io.*;
class FileWrite {
    public static void main(String[] args) {
        try {
            FileOutputStream f = new FileOutputStream("data.txt");
            String s = "Hello Java File";
            f.write(s.getBytes());
            f.close();
            System.out.println("Data written successfully");
        } catch (Exception e) {
            System.out.println(e);
        }
    }
}
Question 11: Input from User and Store into File using Reader and Writer
java
import java.io.*;
class FileInput {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        FileWriter fw = new FileWriter("output.txt");
        System.out.println("Enter text:");
        String data = br.readLine();
        fw.write(data);
        fw.close();
        System.out.println("Data saved in file");
    }
}
Question 13: Employee and Programmer Classes with Payslip Generation
java
class Employee {
    String name, id, address, mail;
    long mobile;

    Employee(String name, String id, String address, String mail, long mobile) {
        this.name = name;
        this.id = id;
        this.address = address;
        this.mail = mail;
        this.mobile = mobile;
    }
}

class Programmer extends Employee {
    double bp;
    Programmer(String name, String id, String address, String mail, long mobile, double bp) {
        super(name, id, address, mail, mobile);
        this.bp = bp;
    }

    void generatePayslip() {
        double da = 0.97 * bp;
        double hra = 0.10 * bp;
        double pf = 0.12 * bp;
        double sf = 0.001 * bp;

        double gross = bp + da + hra;
        double net = gross - (pf + sf);

        System.out.println("\n--- PAY SLIP ---");
        System.out.println("Name: " + name);
        System.out.println("Emp ID: " + id);
        System.out.println("Mail: " + mail);
        System.out.println("Mobile: " + mobile);
        System.out.println("Basic Pay: " + bp);
        System.out.println("Gross Salary: " + gross);
        System.out.println("Net Salary: " + net);
    }
}

class AssistantProfessor extends Programmer {
    AssistantProfessor(String n, String i, String a, String m, long mob, double b) {
        super(n, i, a, m, mob, b);
    }
}

class AssociateProfessor extends Programmer {
    AssociateProfessor(String n, String i, String a, String m, long mob, double b) {
        super(n, i, a, m, mob, b);
    }
}

class Professor extends Programmer {
    Professor(String n, String i, String a, String m, long mob, double b) {
        super(n, i, a, m, mob, b);
    }
}

public class Main {
    public static void main(String[] args) {
        Programmer p = new Programmer("Kavi", "E101", "Chennai", "kavi@mail.com", 9876543210L, 20000);
        p.generatePayslip();

        AssistantProfessor ap = new AssistantProfessor("Ravi", "E102", "Madurai", "ravi@mail.com", 9876500000L, 30000);
        ap.generatePayslip();
    }
}
Question 13 (Interface): Prime Number Check
java
interface Check {
    void isPrime(int n);
}
class Prime implements Check {
    public void isPrime(int n) {
        int c = 0;
        for (int i = 2; i < n; i++)
            if (n % i == 0) c++;
        if (c == 0)
            System.out.println(n + " is Prime");
        else
            System.out.println(n + " is Not Prime");
    }
    public static void main(String[] args) {
        Prime p = new Prime();
        p.isPrime(7);
    }
}
Question 14: Simple, Multilevel, Hybrid Inheritance
java
class A {
    void showA() { System.out.println("Class A"); }
}
class B extends A {
    void showB() { System.out.println("Class B"); }
}
class C extends B {
    void showC() { System.out.println("Class C"); }
}
class D extends A {
    void showD() { System.out.println("Class D"); }
}
class Main {
    public static void main(String[] args) {
        C obj1 = new C();
        obj1.showA(); obj1.showB(); obj1.showC();

        D obj2 = new D();
        obj2.showA(); obj2.showD();
    }
}
Question 15: Outer and Inner Class Display
java
class Outer {
    void display() {
        System.out.println("Outer display");
    }

    class Inner {
        void display() {
            System.out.println("Inner display");
        }
    }

    public static void main(String[] args) {
        Outer o = new Outer();
        o.display();
        Outer.Inner i = o.new Inner();
        i.display();
    }
}
Question 16: MenuBar, Menus, and MenuItems (Simplest)
java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class MenuBarEx extends Application {
    public void start(Stage s) {
        MenuBar mb = new MenuBar();
        Menu m1 = new Menu("File");
        MenuItem i1 = new MenuItem("New");
        MenuItem i2 = new MenuItem("Open");
        m1.getItems().addAll(i1, i2);
        mb.getMenus().add(m1);

        VBox v = new VBox(mb);
        Scene sc = new Scene(v, 200, 100);
        s.setScene(sc);
        s.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
Question 17: MenuBar with Submenu (Simplest)
java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class SubMenuEx extends Application {
    public void start(Stage s) {
        MenuBar mb = new MenuBar();
        Menu m1 = new Menu("File");
        MenuItem i1 = new MenuItem("New");
        MenuItem i2 = new MenuItem("Open");

        Menu recent = new Menu("Recent"); // Submenu
        MenuItem f1 = new MenuItem("File1");
        MenuItem f2 = new MenuItem("File2");
        recent.getItems().addAll(f1, f2);

        m1.getItems().addAll(i1, i2, recent);
        mb.getMenus().add(m1);

        VBox v = new VBox(mb);
        Scene sc = new Scene(v, 200, 100);
        s.setScene(sc);
        s.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
Question 18(i): Grid Layout (Simplest)
java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.GridPane;
import javafx.stage.Stage;

public class GridEx extends Application {
    public void start(Stage s) {
        GridPane grid = new GridPane();

        grid.add(new Button("1"), 0, 0);
        grid.add(new Button("2"), 1, 0);
        grid.add(new Button("3"), 0, 1);
        grid.add(new Button("4"), 1, 1);

        Scene sc = new Scene(grid, 200, 100);
        s.setScene(sc);
        s.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
Question 18(ii): Border Layout (Simplest)
java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.BorderPane;
import javafx.stage.Stage;

public class BorderEx extends Application {
    public void start(Stage s) {
        BorderPane border = new BorderPane();

        border.setTop(new Button("Top"));
        border.setBottom(new Button("Bottom"));
        border.setLeft(new Button("Left"));
        border.setRight(new Button("Right"));
        border.setCenter(new Button("Center"));

        Scene sc = new Scene(border, 200, 100);
        s.setScene(sc);
        s.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}
Question 19(i): Total & Average for Students
java
import java.util.*;

class Student {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        System.out.print("Enter Name: ");
        String name = s.next();
        System.out.print("Enter Roll No: ");
        int roll = s.nextInt();
        int total = 0;
        System.out.println("Enter 5 Marks:");
        for (int i = 0; i < 5; i++)
            total += s.nextInt();
        float avg = total / 5f;
        System.out.println("Name: " + name);
        System.out.println("Roll: " + roll);
        System.out.println("Total: " + total);
        System.out.println("Average: " + avg);
    }
}
Question 19(ii): Palindrome Check
java
import java.util.*;

class Palindrome {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        System.out.print("Enter number: ");
        int n = s.nextInt(), rev = 0, t = n;
        while (n > 0) {
            rev = rev * 10 + n % 10;
            n /= 10;
        }
        if (t == rev)
            System.out.println("Palindrome");
        else
            System.out.println("Not Palindrome");
    }
}
Question 20: Abstract Class Shape
java
abstract class Shape {
    int a, b;
    abstract void printArea();
}

class Rectangle extends Shape {
    Rectangle(int x, int y) { a = x; b = y; }
    void printArea() {
        System.out.println("Area of Rectangle: " + (a * b));
    }
}

class Triangle extends Shape {
    Triangle(int x, int y) { a = x; b = y; }
    void printArea() {
        System.out.println("Area of Triangle: " + (0.5 * a * b));
    }
}

class Circle extends Shape {
    Circle(int r) { a = r; }
    void printArea() {
        System.out.println("Area of Circle: " + (3.14 * a * a));
    }
}

class ShapeMain {
    public static void main(String[] args) {
        new Rectangle(5, 10).printArea();
        new Triangle(5, 10).printArea();
        new Circle(5).printArea();
    }
}
Question 21(a): Fibonacci Series
java
import java.util.*;

class Fibonacci {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        System.out.print("Enter limit: ");
        int n = s.nextInt(), a = 0, b = 1;
        System.out.print("Fibonacci: " + a + " " + b);
        for (int i = 2; i < n; i++) {
            int c = a + b;
            System.out.print(" " + c);
            a = b;
            b = c;
        }
    }
}
Question 21(b): Factorial
java
import java.util.*;

class Factorial {
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        System.out.print("Enter number: ");
        int n = s.nextInt(), fact = 1;
        for (int i = 1; i <= n; i++)
            fact *= i;
        System.out.println("Factorial: " + fact);
    }
}
Question 22: Inter-thread Communication (Wait and Notify)
java
class Customer {
    int amount = 10000;

    synchronized void withdraw(int amt) {
        while (amount < amt) {
            try { wait(); } catch (InterruptedException e) {}
        }
        amount -= amt;
        System.out.println("Withdrawn: " + amt + ", Balance: " + amount);
    }

    synchronized void deposit(int amt) {
        amount += amt;
        System.out.println("Deposited: " + amt + ", Balance: " + amount);
        notify();
    }

    public static void main(String[] args) {
        Customer c = new Customer();
        new Thread(() -> c.withdraw(15000)).start();
        new Thread(() -> c.deposit(10000)).start();
    }
}
