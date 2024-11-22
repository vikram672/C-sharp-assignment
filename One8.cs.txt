using System;
using System.Linq;

namespace AcademicProject
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] grades = { 56, 78, 89, 45, 67 };
            int[] sortedGrades = (int[])grades.Clone();
            Array.Sort(sortedGrades);

            int secondSmallestGrade = sortedGrades[1];
            Console.WriteLine("Second smallest grade: " + secondSmallestGrade);
        }
    }
}