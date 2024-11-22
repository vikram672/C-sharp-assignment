using System;

class ATM
{
    static decimal balance = 1000;

    static void Main()
    {
        Console.WriteLine("Welcome to the ATM!");

        while (true)
        {
            Console.WriteLine("1. Check Balance");
            Console.WriteLine("2. Deposit");
            Console.WriteLine("3. Withdraw");
            Console.WriteLine("4. Exit");

            Console.Write("Choose an option: ");
            int option = Convert.ToInt32(Console.ReadLine());

            switch (option)
            {
                case 1:
                    Console.WriteLine("Balance: " + balance);
                    break;
                case 2:
                    Console.Write("Enter amount to deposit: ");
                    decimal deposit = Convert.ToDecimal(Console.ReadLine());
                    balance += deposit;
                    Console.WriteLine("Deposit successful!");
                    break;
                case 3:
                    Console.Write("Enter amount to withdraw: ");
                    decimal withdraw = Convert.ToDecimal(Console.ReadLine());

                    if (withdraw > balance)
                    {
                        Console.WriteLine("Insufficient funds!");
                    }
                    else
                    {
                        balance -= withdraw;
                        Console.WriteLine("Withdrawal successful!");
                    }
                    break;
                case 4:
                    Console.WriteLine("Goodbye!");
                    return;
                default:
                    Console.WriteLine("Invalid option!");
                    break;
            }
        }
    }
}