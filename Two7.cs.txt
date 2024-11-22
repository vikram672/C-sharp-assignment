using System;

namespace ExpenseTracker
{
    class Program
    {
        static void Main(string[] args)
        {
            ExpenseTracker tracker = new ExpenseTracker();

            Console.WriteLine("Enter expenses for 12 months:");
            for (int i = 1; i <= 12; i++)
            {
                Console.Write($"Month {i}: ");
                double expense = Convert.ToDouble(Console.ReadLine());
                tracker.AddExpense(i, expense);
            }

            Console.WriteLine($"Total expenses for the year: {tracker.TotalExpenses}");
            Console.WriteLine($"Month with highest expenses: {tracker.HighestExpenseMonth}");
            Console.WriteLine($"Month with lowest expenses: {tracker.LowestExpenseMonth}");
        }
    }

    public class ExpenseTracker
    {
        private double[] expenses = new double[12];

        public double TotalExpenses { get; private set; }
        public int HighestExpenseMonth { get; private set; }
        public int LowestExpenseMonth { get; private set; }

        public void AddExpense(int month, double expense)
        {
            expenses[month - 1] = expense;
            TotalExpenses += expense;

            if (month == 1 || expense > expenses[HighestExpenseMonth - 1])
            {
                HighestExpenseMonth = month;
            }

            if (month == 1 || expense < expenses[LowestExpenseMonth - 1])
            {
                LowestExpenseMonth = month;
            }
        }
    }
}