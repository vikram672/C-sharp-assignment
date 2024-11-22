using System;
using System.Collections.Generic;

// Generic Storage Class
public class Storage<T>
{
    public T Item { get; set; }
}

// Generic Pair Class
public class Pair<T1, T2>
{
    public T1 First { get; set; }
    public T2 Second { get; set; }

    public Pair(T1 first, T2 second)
    {
        First = first;
        Second = second;
    }

    public void PrintPair()
    {
        Console.WriteLine($"First: {First}, Second: {Second}");
    }
}

// Generic Calculator Class (with numeric constraint)
public class Calculator<T> where T : struct, IComparable, IComparable<T>, IConvertible, IEquatable<T>, IFormattable
{
    public T Add(T a, T b) => (dynamic)a + (dynamic)b;
    public T Subtract(T a, T b) => (dynamic)a - (dynamic)b;
    public T Multiply(T a, T b) => (dynamic)a * (dynamic)b;
    public T Divide(T a, T b)
    {
        if ((dynamic)b == 0) throw new DivideByZeroException("Cannot divide by zero.");
        return (dynamic)a / (dynamic)b;
    }
}

// Generic Stack with Indexer
public class CustomStack<T>
{
    private List<T> _items = new List<T>();

    public void Push(T item)
    {
        _items.Add(item);
    }

    public T Pop()
    {
        if (_items.Count == 0) throw new InvalidOperationException("Stack is empty.");
        T item = _items[_items.Count - 1];
        _items.RemoveAt(_items.Count - 1);
        return item;
    }

    public T this[int index]
    {
        get
        {
            if (index < 0 || index >= _items.Count)
                throw new IndexOutOfRangeException("Invalid index.");
            return _items[index];
        }
    }

    public int Count => _items.Count;
}

// Generic Queue with Indexer
public class CustomQueue<T>
{
    private List<T> _items = new List<T>();

    public void Enqueue(T item)
    {
        _items.Add(item);
    }

    public T Dequeue()
    {
        if (_items.Count == 0) throw new InvalidOperationException("Queue is empty.");
        T item = _items[0];
        _items.RemoveAt(0);
        return item;
    }

    public T this[int index]
    {
        get
        {
            if (index < 0 || index >= _items.Count)
                throw new IndexOutOfRangeException("Invalid index.");
            return _items[index];
        }
    }

    public int Count => _items.Count;
}

// Main class
public class Program
{
    public static void Main(string[] args)
    {
        bool continueProgram = true;

        while (continueProgram)
        {
            Console.WriteLine("Select a program to run:");
            Console.WriteLine("1. Test Storage");
            Console.WriteLine("2. Test Pair");
            Console.WriteLine("3. Test Calculator");
            Console.WriteLine("4. Test Stack");
            Console.WriteLine("5. Test Queue");
            Console.WriteLine("6. Exit");
            Console.Write("Enter your choice: ");
            int choice = Convert.ToInt32(Console.ReadLine());

            switch (choice)
            {
                case 1:
                    TestStorage();
                    break;
                case 2:
                    TestPair();
                    break;
                case 3:
                    TestCalculator();
                    break;
                case 4:
                    TestStack();
                    break;
                case 5:
                    TestQueue();
                    break;
                case 6:
                    continueProgram = false;
                    break;
                default:
                    Console.WriteLine("Invalid choice, please try again.");
                    break;
            }

            Console.WriteLine();
        }
    }

    private static void TestStorage()
    {
        Console.WriteLine("Testing Storage:");
        Storage<int> intStorage = new Storage<int> { Item = 123 };
        Storage<string> stringStorage = new Storage<string> { Item = "Hello" };
        Storage<double> doubleStorage = new Storage<double> { Item = 45.67 };
        Console.WriteLine($"Integer stored: {intStorage.Item}");
        Console.WriteLine($"String stored: {stringStorage.Item}");
        Console.WriteLine($"Double stored: {doubleStorage.Item}\n");
    }

    private static void TestPair()
    {
        Console.WriteLine("Testing Pair:");
        Pair<int, string> intStringPair = new Pair<int, string>(1, "One");
        Pair<string, double> stringDoublePair = new Pair<string, double>("Pi", 3.14);
        intStringPair.PrintPair();
        stringDoublePair.PrintPair();
        Console.WriteLine();
    }

    private static void TestCalculator()
    {
        Console.WriteLine("Testing Calculator:");
        Calculator<int> intCalculator = new Calculator<int>();
        Calculator<double> doubleCalculator = new Calculator<double>();
        Console.WriteLine($"Addition (int): {intCalculator.Add(5, 3)}");
        Console.WriteLine($"Subtraction (double): {doubleCalculator.Subtract(10.5, 2.3)}");
        Console.WriteLine($"Multiplication (int): {intCalculator.Multiply(7, 8)}");
        Console.WriteLine($"Division (double): {doubleCalculator.Divide(25.0, 5.0)}\n");
    }

    private static void TestStack()
    {
        Console.WriteLine("Testing Stack:");
        CustomStack<string> stack = new CustomStack<string>();
        stack.Push("First");
        stack.Push("Second");
        stack.Push("Third");
        Console.WriteLine($"Popped from stack: {stack.Pop()}");
        Console.WriteLine($"Element at index 0: {stack[0]}");
        Console.WriteLine($"Element at index 1: {stack[1]}\n");
    }

    private static void TestQueue()
    {
        Console.WriteLine("Testing Queue:");
        CustomQueue<int> queue = new CustomQueue<int>();
        queue.Enqueue(10);
        queue.Enqueue(20);
        queue.Enqueue(30);
        Console.WriteLine($"Dequeued from queue: {queue.Dequeue()}");
        Console.WriteLine($"Element at index 0: {queue[0]}");
        Console.WriteLine($"Element at index 1: {queue[1]}\n");
    }
}
