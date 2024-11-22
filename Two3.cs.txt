using System;

class GradeCalculator
{
    static void Main()
    {
        Console.Write("Enter marks for 5 subjects (space-separated): ");
        string[] marks = Console.ReadLine().Split(' ');

        decimal total = 0;

        foreach (string mark in marks)
        {
            total += Convert.ToDecimal(mark);
        }

        decimal average = total / 5;

        string grade = "";

        if (average >= 90)
        {
            grade = "A";
        }
        else if (average >= 80)
        {
            grade = "B";
        }
        else if (average >= 70)
        {
            grade = "C";
        }
        else if (average >= 60)
        {
            grade = "D";
        }
        else
        {
            grade = "F";
        }

        Console.WriteLine("Average: " + average);
        Console.WriteLine("Grade: " + grade);
    }
}