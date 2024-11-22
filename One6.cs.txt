using System;

namespace SimulationTool
{
    class Program
    {
        static void Main(string[] args)
        {
            int[] measurements = { 2, 4, 6, 8 };
            int factor = 3;
            int[] scaledMeasurements = new int[measurements.Length];

            for (int i = 0; i < measurements.Length; i++)
            {
                scaledMeasurements[i] = measurements[i] * factor;
            }

            Console.WriteLine("Scaled measurements:");
            foreach (int item in scaledMeasurements)
            {
                Console.WriteLine(item);
            }
        }
    }
}