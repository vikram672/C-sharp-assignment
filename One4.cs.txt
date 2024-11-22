using System;

namespace SurveyReport
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] participantCodes = { 102, 215, 324, 453, 536 };
            int evenCount = 0;
            int oddCount = 0;

            foreach (int code in participantCodes)
            {
                if (code % 2 == 0)
                {
                    evenCount++;
                }
                else
                {
                    oddCount++;
                }
            }

            Console.WriteLine("Number of male participants: " + evenCount);
            Console.WriteLine("Number of female participants: " + oddCount);
        }
    }
}