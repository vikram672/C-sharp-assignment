using System;

class Program
{
    static void Main()
    {
        bool continueProgram = true;

        while (continueProgram)
        {
            Console.WriteLine("Select a program to run:");
            Console.WriteLine("1. Bank Account Management");
            Console.WriteLine("2. Student Grade Calculation");
            Console.WriteLine("3. Temperature Conversion");
            Console.WriteLine("4. Employee Management");
            Console.WriteLine("5. Simple Calculator");
            Console.WriteLine("6. Library Management System");
            Console.WriteLine("7. Prime Number Checker");
            Console.WriteLine("8. Car Rental System");
            Console.WriteLine("9. E-commerce Order Management System");
            Console.WriteLine("10. Movie Ticket Booking System");
            Console.WriteLine("11. Exit");
            Console.Write("Enter your choice: ");
            int choice = Convert.ToInt32(Console.ReadLine());

            switch (choice)
            {
                case 1:
                    BankAccountDemo();
                    break;
                case 2:
                    StudentGradeDemo();
                    break;
                case 3:
                    TemperatureConverterDemo();
                    break;
                case 4:
                    EmployeeDemo();
                    break;
                case 5:
                    SimpleCalculatorDemo();
                    break;
                case 6:
                    LibraryManagementDemo();
                    break;
                case 7:
                    PrimeNumberCheckerDemo();
                    break;
                case 8:
                    CarRentalDemo();
                    break;
                case 9:
                    EcommerceOrderDemo();
                    break;
                case 10:
                    MovieTicketBookingDemo();
                    break;
                case 11:
                    continueProgram = false;
                    break;
                default:
                    Console.WriteLine("Invalid choice, try again.");
                    break;
            }

            Console.WriteLine();
        }
    }

    // 1. Bank Account Management
    public class BankAccount
    {
        public string AccountHolder { get; private set; }
        private decimal Balance;

        public BankAccount(string accountHolder, decimal initialBalance)
        {
            AccountHolder = accountHolder;
            Balance = initialBalance;
        }

        public void Deposit(decimal amount)
        {
            if (amount > 0)
            {
                Balance += amount;
                Console.WriteLine($"Successfully deposited {amount}. New balance: {Balance}");
            }
            else
            {
                Console.WriteLine("Deposit amount must be positive.");
            }
        }

        public void Withdraw(decimal amount)
        {
            if (amount > Balance)
            {
                Console.WriteLine("Insufficient funds.");
            }
            else if (amount <= 0)
            {
                Console.WriteLine("Withdrawal amount must be positive.");
            }
            else
            {
                Balance -= amount;
                Console.WriteLine($"Successfully withdrew {amount}. New balance: {Balance}");
            }
        }

        public decimal GetBalance()
        {
            return Balance;
        }
    }

    static void BankAccountDemo()
    {
        BankAccount account = new BankAccount("John Doe", 500);
        account.Deposit(200);
        account.Withdraw(100);
        Console.WriteLine($"Final Balance: {account.GetBalance()}");
    }

    // 2. Student Grade Calculation
    static void StudentGradeDemo()
    {
        int[] marks = new int[5];
        for (int i = 0; i < 5; i++)
        {
            Console.Write($"Enter marks for subject {i + 1}: ");
            marks[i] = Convert.ToInt32(Console.ReadLine());

            if (marks[i] < 0 || marks[i] > 100)
            {
                throw new ArgumentOutOfRangeException("Marks must be between 0 and 100.");
            }
        }

        double average = CalculateAverage(marks);
        char grade = GetGrade(average);

        Console.WriteLine($"Average Marks: {average}");
        Console.WriteLine($"Grade: {grade}");
    }

    static double CalculateAverage(int[] marks)
    {
        int sum = 0;
        foreach (int mark in marks)
        {
            sum += mark;
        }
        return (double)sum / marks.Length;
    }

    static char GetGrade(double average)
    {
        if (average >= 90)
            return 'A';
        else if (average >= 80)
            return 'B';
        else if (average >= 70)
            return 'C';
        else if (average >= 60)
            return 'D';
        else
            return 'F';
    }

    // 3. Temperature Conversion
    public class TemperatureConverter
    {
        public double Celsius { get; set; }
        public double Fahrenheit
        {
            get { return Celsius * 9 / 5 + 32; }
            set { Celsius = (value - 32) * 5 / 9; }
        }
    }

    static void TemperatureConverterDemo()
    {
        TemperatureConverter converter = new TemperatureConverter();
        string choice;
        do
        {
            Console.WriteLine("Enter 1 to convert from Celsius to Fahrenheit");
            Console.WriteLine("Enter 2 to convert from Fahrenheit to Celsius");
            int option = Convert.ToInt32(Console.ReadLine());

            if (option == 1)
            {
                Console.Write("Enter temperature in Celsius: ");
                converter.Celsius = Convert.ToDouble(Console.ReadLine());
                Console.WriteLine($"Fahrenheit: {converter.Fahrenheit}");
            }
            else if (option == 2)
            {
                Console.Write("Enter temperature in Fahrenheit: ");
                converter.Fahrenheit = Convert.ToDouble(Console.ReadLine());
                Console.WriteLine($"Celsius: {converter.Celsius}");
            }

            Console.WriteLine("Do you want to perform another conversion? (yes/no)");
            choice = Console.ReadLine();
        }
        while (choice.ToLower() == "yes");
    }

    // 4. Employee Management
    public class Employee
    {
        public string Name { get; set; }
        private int age;
        private decimal salary;
        public string Department { get; set; }

        public int Age
        {
            get { return age; }
            set
            {
                if (value <= 0)
                    throw new ArgumentOutOfRangeException("Age must be positive.");
                age = value;
            }
        }

        public decimal Salary
        {
            get { return salary; }
            private set { salary = value; }
        }

        public Employee(string name, int age, decimal salary, string department)
        {
            Name = name;
            Age = age;
            Salary = salary;
            Department = department;
        }

        public void DisplayEmployeeInfo()
        {
            Console.WriteLine($"Name: {Name}, Age: {Age}, Salary: {Salary}, Department: {Department}");
        }
    }

    static void EmployeeDemo()
    {
        Employee employee = new Employee("Alice", 30, 70000, "Engineering");
        employee.DisplayEmployeeInfo();
    }

    // 5. Simple Calculator
    static void SimpleCalculatorDemo()
    {
        Console.Write("Enter first number: ");
        double num1 = Convert.ToDouble(Console.ReadLine());

        Console.Write("Enter second number: ");
        double num2 = Convert.ToDouble(Console.ReadLine());

        Console.Write("Enter operation (+, -, *, /): ");
        char operation = Convert.ToChar(Console.ReadLine());

        double result = 0;
        try
        {
            switch (operation)
            {
                case '+':
                    result = num1 + num2;
                    break;
                case '-':
                    result = num1 - num2;
                    break;
                case '*':
                    result = num1 * num2;
                    break;
                case '/':
                    if (num2 == 0)
                        throw new DivideByZeroException("Cannot divide by zero.");
                    result = num1 / num2;
                    break;
                default:
                    Console.WriteLine("Invalid operation.");
                    return;
            }
            Console.WriteLine($"Result: {result}");
        }
        catch (DivideByZeroException ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    // 6. Library Management System
    public class Book
    {
        public string Title { get; set; }
        public string Author { get; set; }
        public string ISBN { get; set; }
        public int CopiesAvailable { get; set; }

        public Book(string title, string author, string isbn, int copies)
        {
            Title = title;
            Author = author;
            ISBN = isbn;
            CopiesAvailable = copies;
        }

        public void IssueBook()
        {
            if (CopiesAvailable > 0)
            {
                CopiesAvailable--;
                Console.WriteLine($"Book issued. Copies available: {CopiesAvailable}");
            }
            else
            {
                Console.WriteLine("No copies available.");
            }
        }

        public void ReturnBook()
        {
            CopiesAvailable++;
            Console.WriteLine($"Book returned. Copies available: {CopiesAvailable}");
        }
    }

    static void LibraryManagementDemo()
    {
        Book book = new Book("C# Programming", "John Smith", "123456", 5);
        book.IssueBook();
        book.ReturnBook();
    }

    // 7. Prime Number Checker
    static void PrimeNumberCheckerDemo()
    {
        Console.Write("Enter an integer to check if it is prime: ");
        int number = Convert.ToInt32(Console.ReadLine());

        if (number <= 1)
        {
            Console.WriteLine("Not a prime number.");
            return;
        }

        bool isPrime = true;
        for (int i = 2; i <= Math.Sqrt(number); i++)
        {
            if (number % i == 0)
            {
                isPrime = false;
                break;
            }
        }

        if (isPrime)
            Console.WriteLine($"{number} is a prime number.");
        else
            Console.WriteLine($"{number} is not a prime number.");
    }

    // 8. Car Rental System
    public class Car
    {
        public string Model { get; set; }
        public decimal DailyRate { get; set; }
        public bool IsAvailable { get; set; } = true;

        public Car(string model, decimal dailyRate)
        {
            Model = model;
            DailyRate = dailyRate;
        }

        public void RentCar(int rentalDays)
        {
            if (!IsAvailable)
                throw new InvalidOperationException("Car is not available for rental.");

            decimal totalCost = rentalDays * DailyRate;
            IsAvailable = false;
            Console.WriteLine($"Car rented for {rentalDays} days. Total cost: ${totalCost}");
        }
    }

    static void CarRentalDemo()
    {
        Car car = new Car("Toyota Camry", 50);
        try
        {
            car.RentCar(3);
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }

    // 9. E-commerce Order Management System
    public class Order
    {
        public int OrderID { get; private set; }
        public string CustomerName { get; set; }
        public decimal Amount { get; private set; }
        public string OrderStatus { get; private set; } = "Placed";

        public Order(int orderId, string customerName, decimal amount)
        {
            OrderID = orderId;
            CustomerName = customerName;
            Amount = amount;
        }

        public void UpdateOrderStatus(string newStatus)
        {
            switch (newStatus.ToLower())
            {
                case "shipped":
                case "delivered":
                    OrderStatus = newStatus;
                    Console.WriteLine($"Order status updated to {OrderStatus}.");
                    break;
                default:
                    Console.WriteLine("Invalid status update.");
                    break;
            }
        }

        public void DisplayOrderDetails()
        {
            Console.WriteLine($"OrderID: {OrderID}, Customer: {CustomerName}, Amount: ${Amount}, Status: {OrderStatus}");
        }
    }

    static void EcommerceOrderDemo()
    {
        Order order = new Order(101, "John Doe", 299.99M);
        order.DisplayOrderDetails();
        order.UpdateOrderStatus("shipped");
        order.DisplayOrderDetails();
    }

    // 10. Movie Ticket Booking System
    public class MovieTicket
    {
        public string MovieName { get; set; }
        public string ShowTime { get; set; }
        public string SeatNumber { get; set; }
        public decimal TicketPrice { get; set; }
        private bool IsBooked { get; set; } = false;

        public MovieTicket(string movieName, string showTime, string seatNumber, decimal ticketPrice)
        {
            MovieName = movieName;
            ShowTime = showTime;
            SeatNumber = seatNumber;
            TicketPrice = ticketPrice;
        }

        public void BookTicket()
        {
            if (IsBooked)
            {
                throw new InvalidOperationException("Seat is already booked.");
            }

            decimal discount = 0;
            if (TicketPrice > 100)
            {
                discount = TicketPrice * 0.10M;
                TicketPrice -= discount;
                Console.WriteLine($"A discount of 10% (${discount}) has been applied. Final price: ${TicketPrice}");
            }

            IsBooked = true;
            Console.WriteLine($"Ticket booked for {MovieName} at {ShowTime}, Seat: {SeatNumber}, Price: ${TicketPrice}");
        }
    }

    static void MovieTicketBookingDemo()
    {
        try
        {
            MovieTicket ticket = new MovieTicket("Avengers", "7:00 PM", "A10", 120);
            ticket.BookTicket();
        }
        catch (Exception ex)
        {
            Console.WriteLine(ex.Message);
        }
    }
}