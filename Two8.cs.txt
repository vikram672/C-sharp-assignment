using System;
using System.Collections.Generic;

namespace ShoppingCartSystem
{
    class Program
    {
        static void Main(string[] args)
        {
            ShoppingCart cart = new ShoppingCart();

            while (true)
            {
                Console.WriteLine("1. Add item to cart");
                Console.WriteLine("2. Remove item from cart");
                Console.WriteLine("3. View cart");
                Console.WriteLine("4. Exit");
                Console.Write("Choose an option: ");
                int option = Convert.ToInt32(Console.ReadLine());

                switch (option)
                {
                    case 1:
                        Console.Write("Enter item name: ");
                        string name = Console.ReadLine();
                        Console.Write("Enter item price: ");
                        double price = Convert.ToDouble(Console.ReadLine());
                        cart.AddItem(new Item(name, price));
                        break;
                    case 2:
                        Console.Write("Enter item name to remove: ");
                        string removeName = Console.ReadLine();
                        cart.RemoveItem(removeName);
                        break;
                    case 3:
                        cart.ViewCart();
                        break;
                    case 4:
                        return;
                    default:
                        Console.WriteLine("Invalid option. Please try again.");
                        break;
                }
            }
        }
    }

    public class Item
    {
        public string Name { get; set; }
        public double Price { get; set; }

        public Item(string name, double price)
        {
            Name = name;
            Price = price;
        }
    }

    public class ShoppingCart
    {
        private List<Item> items = new List<Item>();

        public void AddItem(Item item)
        {
            items.Add(item);
        }

        public void RemoveItem(string name)
        {
            items.RemoveAll(i => i.Name == name);
        }

        public void ViewCart()
        {
            double totalPrice = 0;
            Console.WriteLine("Items in cart:");
            foreach (Item item in items)
            {
                Console.WriteLine($"{item.Name} - Rs. {item.Price}");
                totalPrice += item.Price;
            }
            Console.WriteLine($"Total price: Rs. {totalPrice}");
        }
    }
}