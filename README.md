 # علي باوزير
using System;

class Vehicle
{
    public string Brand;
    public int Year;

    public Vehicle(string brand, int year)
    {
        Brand = brand;
        Year = year;
    }

    public virtual void Start()
    {
        Console.WriteLine(Brand + " is starting.");
    }
}

class Car : Vehicle
{
    public int NumberOfDoors;

    public Car(string brand, int year, int numberOfDoors)
        : base(brand, year)
    {
        NumberOfDoors = numberOfDoors;
    }
}

class Bus : Vehicle
{
    public int Capacity;

    public Bus(string brand, int year, int capacity)
        : base(brand, year)
    {
        Capacity = capacity;
    }
}

class Motorcycle : Vehicle
{
    public bool HasSidecar;

    public Motorcycle(string brand, int year, bool hasSidecar)
        : base(brand, year)
    {
        HasSidecar = hasSidecar;
    }
}

class Program
{
    static void Main()
    {
        Car car = new Car("Toyota", 2022, 4);
        Bus bus = new Bus("Mercedes", 2020, 50);
        Motorcycle motorcycle = new Motorcycle("Honda", 2023, false);

        car.Start();
        bus.Start();
        motorcycle.Start();

        Console.WriteLine("Car Doors: " + car.NumberOfDoors);
        Console.WriteLine("Bus Capacity: " + bus.Capacity);
        Console.WriteLine("Motorcycle Has Sidecar: " + motorcycle.HasSidecar);
    }
}


using System;
using System.Collections.Generic;

class Shape
{
    public virtual double CalculateArea()
    {
        return 0;
    }
}

class Circle : Shape
{
    public double Radius;

    public Circle(double radius)
    {
        Radius = radius;
    }

    public override double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }
}

class Rectangle : Shape
{
    public double Width;
    public double Height;

    public Rectangle(double width, double height)
    {
        Width = width;
        Height = height;
    }

    public override double CalculateArea()
    {
        return Width * Height;
    }
}

class Program
{
    static void Main()
    {
        List<Shape> shapes = new List<Shape>();

        shapes.Add(new Circle(5));
        shapes.Add(new Rectangle(10, 4));

        foreach (Shape shape in shapes)
        {
            Console.WriteLine("Type: " + shape.GetType().Name);
            Console.WriteLine("Area: " + shape.CalculateArea());
            Console.WriteLine();
        }
    }
}


using System;

class Person
{
    public string Name;
    public string Email;

    public Person(string name, string email)
    {
        Console.WriteLine("Person constructor");
        
        Name = name;
        Email = email;
    }

    public void DisplayBasicInfo()
    {
        Console.WriteLine("Name: " + Name);
        Console.WriteLine("Email: " + Email);
    }
}

class Student : Person
{
    public int StudentId;
    public double GPA;

    public Student(string name, string email, int studentId, double gpa)
        : base(name, email)
    {
        Console.WriteLine("Student constructor");

        StudentId = studentId;
        GPA = gpa;
    }

    public void DisplayStudentInfo()
    {
        Console.WriteLine("Student ID: " + StudentId);
        Console.WriteLine("GPA: " + GPA);
    }
}

class Employee : Person
{
    public int EmployeeId;
    public double Salary;

    public Employee(string name, string email, int employeeId, double salary)
        : base(name, email)
    {
        Console.WriteLine("Employee constructor");

        EmployeeId = employeeId;
        Salary = salary;
    }
}

class Teacher : Employee
{
    public string CourseName;

    public Teacher(
        string name,
        string email,
        int employeeId,
        double salary,
        string courseName)
        : base(name, email, employeeId, salary)
    {
        Console.WriteLine("Teacher constructor");

        CourseName = courseName;
    }

    public void Teach()
    {
        Console.WriteLine("Teacher is teaching: " + CourseName);
    }
}

class Program
{
    static void Main()
    {
        Console.WriteLine("Creating Student:");
        
        Student student = new Student(
            "Ahmed",
            "ahmed@gmail.com",
            101,
            3.5
        );

        Console.WriteLine();

        Console.WriteLine("Creating Teacher:");

        Teacher teacher = new Teacher(
            "Mohammed",
            "mohammed@gmail.com",
            501,
            5000,
            "C# Programming"
        );

        Console.WriteLine();

        Console.WriteLine("Student Information:");
        student.DisplayBasicInfo();
        student.DisplayStudentInfo();

        Console.WriteLine();

        Console.WriteLine("Teacher Information:");
        teacher.DisplayBasicInfo();
        teacher.Teach();
    }
}


using System;
using System.Collections.Generic;

class Person
{
    public string Name;

    public Person(string name)
    {
        Name = name;
    }

    public virtual void DisplayInfo()
    {
        Console.WriteLine("Person Name: " + Name);
    }
}

class Student : Person
{
    public int StudentId;

    public Student(string name, int studentId)
        : base(name)
    {
        StudentId = studentId;
    }

    public override void DisplayInfo()
    {
        Console.WriteLine("Student Name: " + Name);
        Console.WriteLine("Student ID: " + StudentId);
    }
}

class Employee : Person
{
    public double Salary;

    public Employee(string name, double salary)
        : base(name)
    {
        Salary = salary;
    }

    public override void DisplayInfo()
    {
        Console.WriteLine("Employee Name: " + Name);
        Console.WriteLine("Salary: " + Salary);
    }
}

class Teacher : Person
{
    public string CourseName;

    public Teacher(string name, string courseName)
        : base(name)
    {
        CourseName = courseName;
    }

    public override void DisplayInfo()
    {
        Console.WriteLine("Teacher Name: " + Name);
        Console.WriteLine("Course: " + CourseName);
    }
}

class Program
{
    static void ShowPersonInfo(Person person)
    {
        person.DisplayInfo();
    }

    static void Main()
    {
        List<Person> people = new List<Person>();

        people.Add(new Student("Ahmed", 101));
        people.Add(new Employee("Ali", 5000));
        people.Add(new Teacher("Mohammed", "C# Programming"));

        foreach (Person person in people)
        {
            Console.WriteLine("Runtime Type: " + person.GetType().Name);

            person.DisplayInfo();

            Console.WriteLine();
        }

        Console.WriteLine("Calling method that accepts Person:");
        ShowPersonInfo(people[0]);
    }
}