# C# Object-Oriented Programming Assignments

using System;

class Person
{
    public string Name { get; set; }
    public string Email { get; set; }

    public Person(string name, string email)
    {
        Name = name;
        Email = email;
        Console.WriteLine("Person Constructor Executed.");
    }

    public virtual void DisplayBasicInfo()
    {
        Console.WriteLine($"Name: {Name}, Email: {Email}");
    }
}

class Student : Person
{
    public int StudentId { get; set; }
    public double Gpa { get; set; }

    public Student(string name, string email, int studentId, double gpa) : base(name, email)
    {
        StudentId = studentId;
        Gpa = gpa;
        Console.WriteLine("Student Constructor Executed.");
    }
}

class Teacher : Person
{
    public string CourseName { get; set; }

    public Teacher(string name, string email, string courseName) : base(name, email)
    {
        CourseName = courseName;
        Console.WriteLine("Teacher Constructor Executed.");
    }

    public void Teach()
    {
        Console.WriteLine($"{Name} is teaching {CourseName}.");
    }
}

class Program
{
    static void Main()
    {
        Console.WriteLine("--- Creating Student ---");
        Student student = new Student("Ali", "ali@uni.com", 101, 3.8);

        Console.WriteLine("--- Creating Teacher ---");
        Teacher teacher = new Teacher("Dr. Waleed", "waleed@uni.com", "Anatomy");

        Console.WriteLine("--- Calling Methods ---");
        student.DisplayBasicInfo();
        teacher.DisplayBasicInfo();
        teacher.Teach();
    }
}


class Person
{
    public string Name { get; set; }

    public Person(string name) { Name = name; }

    public virtual void DisplayInfo()
    {
        Console.WriteLine($"Person Name: {Name}");
    }
}

class Student : Person
{
    public int StudentId { get; set; }
    public Student(string name, int studentId) : base(name) { StudentId = studentId; }

    public override void DisplayInfo()
    {
        Console.WriteLine($"Student: {Name}, ID: {StudentId}");
    }
}

class Employee : Person
{
    public double Salary { get; set; }
    public Employee(string name, double salary) : base(name) { Salary = salary; }

    public override void DisplayInfo()
    {
        Console.WriteLine($"Employee: {Name}, Salary: {Salary}");
    }
}

class Teacher : Person
{
    public string CourseName { get; set; }
    public Teacher(string name, string courseName) : base(name) { CourseName = courseName; }

    public override void DisplayInfo()
    {
        Console.WriteLine($"Teacher: {Name}, Course: {CourseName}");
    }
}

class Program
{
    static void PrintPersonInfo(Person p)
    {
        p.DisplayInfo();
    }

    static void Main()
    {
        List<Person> people = new List<Person>
        {
            new Student("Ahmed", 202301),
            new Employee("Mohammed", 1200.0),
            new Teacher("Dr. Salem", "Physical Therapy")
        };

        foreach (var person in people)
        {
            Console.WriteLine($"Runtime Type: {person.GetType().Name}");
            person.DisplayInfo();
            Console.WriteLine("-------------------");
        }

        Console.WriteLine("Testing Method accepting Person:");
        PrintPersonInfo(new Student("Khaled", 202302));
    }
}


class Vehicle
{
    public string Brand { get; set; }
    public int Year { get; set; }

    public Vehicle(string brand, int year)
    {
        Brand = brand;
        Year = year;
    }

    public void Start()
    {
        Console.WriteLine($"{Brand} vehicle is starting.");
    }
}

class Car : Vehicle
{
    public int NumberOfDoors { get; set; }
    public Car(string brand, int year, int numberOfDoors) : base(brand, year)
    {
        NumberOfDoors = numberOfDoors;
    }
}

class Bus : Vehicle
{
    public int Capacity { get; set; }
    public Bus(string brand, int year, int capacity) : base(brand, year)
    {
        Capacity = capacity;
    }
}

class Motorcycle : Vehicle
{
    public bool HasSidecar { get; set; }
    public Motorcycle(string brand, int year, bool hasSidecar) : base(brand, year)
    {
        HasSidecar = hasSidecar;
    }
}

class Program
{
    static void Main()
    {
        Car car = new Car("Toyota", 2024, 4);
        Bus bus = new Bus("Mercedes", 2022, 50);
        Motorcycle moto = new Motorcycle("Yamaha", 2023, false);

        car.Start();
        bus.Start();
        moto.Start();
    }
}



class Shape
{
    public virtual double CalculateArea()
    {
        return 0.0;
    }
}

class Circle : Shape
{
    public double Radius { get; set; }

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
    public double Width { get; set; }
    public double Height { get; set; }

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
        List<Shape> shapes = new List<Shape>
        {
            new Circle(5.0),
            new Rectangle(4.0, 6.0)
        };

        foreach (var shape in shapes)
        {
            Console.WriteLine($"Type: {shape.GetType().Name}, Area: {shape.CalculateArea():F2}");
        }
    }
}
