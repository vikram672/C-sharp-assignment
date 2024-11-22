using System;

namespace StudentAttendanceTracker
{
    class Program
    {
        static void Main(string[] args)
        {
            Student student = new Student("John Doe");

            Console.WriteLine("Enter attendance for 5 days (Y/N):");
            for (int i = 1; i <= 5; i++)
            {
                Console.Write($"Day {i}: ");
                string attendance = Console.ReadLine().ToUpper();
                student.RecordAttendance(attendance == "Y");
            }

            Console.WriteLine($"Total days attended: {student.TotalDaysAttended}");
            Console.WriteLine($"Has perfect attendance: {student.HasPerfectAttendance}");
        }
    }

    public class Student
    {
        public string Name { get; set; }
        public int TotalDaysAttended { get; private set; }
        public bool HasPerfectAttendance { get; private set; }

        public Student(string name)
        {
            Name = name;
            TotalDaysAttended = 0;
            HasPerfectAttendance = true;
        }

        public void RecordAttendance(bool isPresent)
        {
            if (isPresent)
            {
                TotalDaysAttended++;
            }
            else
            {
                HasPerfectAttendance = false;
            }
        }
    }
}