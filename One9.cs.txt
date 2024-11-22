using System;
using System.Collections.Generic;

namespace SystemImprovement
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] ids = { 102, 215, 102, 324, 215 };
            List<int> uniqueIds = new List<int>();

            foreach (int id in ids)
            {
                if (!uniqueIds.Contains(id))
                {
                    uniqueIds.Add(id);
                }
            }

            Console.WriteLine("Unique IDs:");
            foreach (int id in uniqueIds)
            {
                Console.WriteLine(id);
            }
        }
    }
}