using System;
using System.Collections.Generic;

namespace AnalyticsApplication
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] dataset1 = { 1, 2, 3, 4, 5 };
            int[] dataset2 = { 3, 4, 5, 6, 7 };
            List<int> commonElements = new List<int>();

            foreach (int element in dataset1)
            {
                if (dataset2.Contains(element) && !commonElements.Contains(element))
                {
                    commonElements.Add(element);
                }
            }

            Console.WriteLine("Common elements:");
            foreach (int element in commonElements)
            {
                Console.WriteLine(element);
            }
        }
    }
}