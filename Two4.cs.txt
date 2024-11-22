using System;
using System.Text.RegularExpressions;

class PasswordValidator
{
    static void Main()
    {
        Console.Write("Enter password: ");
        string password = Console.ReadLine();

        if (password.Length < 8)
        {
            Console.WriteLine("Password must be at least 8 characters long!");
        }
        else if (!Regex.IsMatch(password, "[A-Z]"))
        {
            Console.WriteLine("Password must contain at least one uppercase letter!");
        }
        else if (!Regex.IsMatch(password, "[a-z]"))
        {
            Console.WriteLine("Password must contain at least one lowercase letter!");
        }
        else if (!Regex.IsMatch(password, "[0-9]"))
        {
            Console.WriteLine("Password must contain at least one number!");
        }
        else
        {
            Console.WriteLine("Password is valid!");
        }
    }
}