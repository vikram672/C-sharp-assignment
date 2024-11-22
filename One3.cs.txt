using System;

namespace InventoryManagementSystem
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] prices = { 1500, 2300, 999, 3200, 1750 };
            int maxPrice = prices[0];

            foreach (int price in prices)
            {
                if (price > maxPrice)
                {
                    maxPrice = price;
                }
            }

            Console.WriteLine("Most expensive item: " + maxPrice);
        }
    }
}