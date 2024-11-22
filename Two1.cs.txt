using System;

class TemperatureConverter
{
    static void Main()
    {
        Console.Write("Enter temperature in Celsius: ");
        double celsius = Convert.ToDouble(Console.ReadLine());

        if (celsius < 0)
        {
            Console.WriteLine("Warning: Freezing temperature!");
        }

        double fahrenheit = (celsius * 9 / 5) + 32;
        Console.WriteLine("Temperature in Fahrenheit: " + fahrenheit);
    }
}