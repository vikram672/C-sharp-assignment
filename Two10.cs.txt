using System;

class ShoppingCart
{
    static void Main()
    {
        decimal[] prices = { 100, 200, 300, 400, 500 };
        decimal totalPrice = 0;

        foreach (decimal price in prices)
        {
            totalPrice += price;
        }

        if (totalPrice > 3000)
        {
            totalPrice *= 0.9m; // 10% discount
        }

        Console.WriteLine("Total Price: " + totalPrice);
    }
}