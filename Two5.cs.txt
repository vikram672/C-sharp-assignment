using System;

namespace TaxiFareCalculator
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Write("Enter distance traveled (in kilometers): ");
            double distance = Convert.ToDouble(Console.ReadLine());
            bool isRideAtNight = false;

            Console.Write("Is the ride at night (true/false)? ");
            string nightRideInput = Console.ReadLine().ToLower();
            if (nightRideInput == "true")
            {
                isRideAtNight = true;
            }

            double fare = CalculateTaxiFare(distance, isRideAtNight);
            Console.WriteLine($"The fare for the taxi ride is: Rs. {fare}");
        }

        static double CalculateTaxiFare(double distance, bool isRideAtNight)
        {
            const double BASE_FARE = 20;
            const double PER_KILOMETER_RATE = 8;
            const double NIGHT_SURCHARGE = 1.5;

            double fare = BASE_FARE;

            if (distance > 2)
            {
                double additionalDistance = distance - 2;
                fare += additionalDistance * PER_KILOMETER_RATE;
            }

            if (isRideAtNight)
            {
                fare *= NIGHT_SURCHARGE;
            }

            return fare;
        }
    }
}