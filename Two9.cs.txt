using System;

namespace EmployeeMonthlySalaryCalculator
{
    class Employee
    {
        public decimal HourlyWage { get; set; }
        public decimal HoursWorkedPerWeek { get; set; }

        public Employee(decimal hourlyWage, decimal hoursWorkedPerWeek)
        {
            HourlyWage = hourlyWage;
            HoursWorkedPerWeek = hoursWorkedPerWeek;
        }

        public decimal CalculateMonthlySalary()
        {
            const int WEEKS_IN_MONTH = 4;
            decimal weeklySalary = HourlyWage * HoursWorkedPerWeek;
            decimal monthlySalary = weeklySalary * WEEKS_IN_MONTH;
            return monthlySalary;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Enter hourly wage: ");
            decimal hourlyWage = Convert.ToDecimal(Console.ReadLine());

            Console.Write("Enter hours worked per week: ");
            decimal hoursWorkedPerWeek = Convert.ToDecimal(Console.ReadLine());

            Employee employee = new Employee(hourlyWage, hoursWorkedPerWeek);

            decimal monthlySalary = employee.CalculateMonthlySalary();
            Console.WriteLine($"Monthly salary: {monthlySalary:C}");
        }
    }
}