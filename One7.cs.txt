using System;

namespace LibrarySystem
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] bookCodes = { 101, 203, 304, 405, 506 };
            int searchCode = 304;
            int index = -1;

            for (int i = 0; i < bookCodes.Length; i++)
            {
                if (bookCodes[i] == searchCode)
                {
                    index = i;
                    break;
                }
            }

            if (index != -1)
            {
                Console.WriteLine("Book code found at index " + index);
            }
            else
            {
                Console.WriteLine("Book code not found");
            }
        }
    }
}