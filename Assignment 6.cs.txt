using System;
using System.IO;

class Program
{
    static void Main()
    {
        // Task 1: Delegate Addition Task
        Task1.Run();
        Console.ReadLine();

        // Task 2: Appliance Task with Power Validation
        Task2.Run();
        Console.ReadLine();

        // Task 3: Multicast Delegate with Display and Log
        Task3.Run();
        Console.ReadLine();

        // Task 4: Person and Employee Validation
        Task4.Run();
        Console.ReadLine();
        // Task 5: Shape Area Calculation
        Task5.Run();
        Console.ReadLine();
    }
}

// Task 1: Delegate for Addition
public static class Task1
{
    public delegate int MathOperation(int a, int b);

    public static void Run()
    {
        MathOperation addition = (a, b) => a + b;
        int result = addition.Invoke(5, 10);
        Console.WriteLine($"Sum of 5 and 10: {result}");
    }
}

// Task 2: Appliance with Abstract Class and Power Validation
public abstract class Appliance
{
    private int power;
    public int Power
    {
        get => power;
        set
        {
            if (value > 1000)
                throw new ArgumentOutOfRangeException("Power cannot exceed 1000 watts.");
            power = value;
        }
    }

    public abstract void TurnOn();
}

public class Fan : Appliance
{
    public override void TurnOn() => Console.WriteLine($"Fan is now on with Power: {Power} watts.");
}

public class AirConditioner : Appliance
{
    public override void TurnOn() => Console.WriteLine($"Air Conditioner is now on with Power: {Power} watts.");
}

public static class Task2
{
    public static void Run()
    {
        try
        {
            Fan fan = new Fan { Power = 900 };
            fan.TurnOn();

            AirConditioner ac = new AirConditioner { Power = 1100 }; // Will throw exception
            ac.TurnOn();
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}

// Task 3: Multicast Delegate
public delegate void ProcessData(string data);

public static class Task3
{
    public static void DisplayData(string data) => Console.WriteLine($"Displaying Data: {data}");

    public static void LogData(string data)
    {
        using (StreamWriter writer = new StreamWriter("log.txt", true))
        {
            writer.WriteLine($"Logged Data: {data}");
        }
        Console.WriteLine("Data logged to file.");
    }

    public static void Run()
    {
        ProcessData processData = DisplayData;
        processData += LogData;
        processData.Invoke("Hello World");
    }
}

// Task 4: Person and Employee with Validation
public class Person
{
    private int age;
    public string Name { get; set; }
    public int Age
    {
        get => age;
        set
        {
            if (value < 0 || value > 10)
                throw new ArgumentOutOfRangeException("Age must be between 0 and 10.");
            age = value;
        }
    }
}

public class Employee : Person
{
    private decimal salary;
    public decimal Salary
    {
        get => salary;
        set
        {
            if (value < 0)
                throw new ArgumentOutOfRangeException("Salary cannot be negative.");
            salary = value;
        }
    }

    public void DisplayDetails() => Console.WriteLine($"Name: {Name}, Age: {Age}, Salary: {Salary}");
}

public static class Task4
{
    public static void Run()
    {
        try
        {
            Employee employee = new Employee { Name = "Alice", Age = 5, Salary = 5000 };
            employee.DisplayDetails();

            employee.Age = -1;  // This will throw an exception
            employee.Salary = -100; // This will throw an exception
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}

// Task 5: Shape Area Calculation
public abstract class Shape
{
    protected double Area { get; private set; }

    public abstract void CalculateArea();

    public double GetArea() => Area;

    protected void SetArea(double area) => Area = area;
}

public class Circle : Shape
{
    private double radius;

    public Circle(double radius)
    {
        this.radius = radius;
    }

    public override void CalculateArea()
    {
        SetArea(Math.PI * Math.Pow(radius, 2));
    }
}

public class Rectangle : Shape
{
    private double length;
    private double width;

    public Rectangle(double length, double width)
    {
        this.length = length;
        this.width = width;
    }

    public override void CalculateArea()
    {
        SetArea(length * width);
    }
}

public static class Task5
{
    public static void Run()
    {
        Circle circle = new Circle(5);
        Rectangle rectangle = new Rectangle(10, 20);

        circle.CalculateArea();
        rectangle.CalculateArea();

        Console.WriteLine($"Circle Area: {circle.GetArea()}");
        Console.WriteLine($"Rectangle Area: {rectangle.GetArea()}");
    }
}
