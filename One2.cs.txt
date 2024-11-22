using System;

namespace AnalyticsTool
{
    class Program
    {
        static void Main(string[] args)
        {
            float[] scores = { 85.5f, 90.3f, 78.4f, 88.9f, 92.1f };
            float sum = 0;

            foreach (float score in scores)
            {
                sum += score;
            }

            float average = sum / scores.Length;
            Console.WriteLine("Average score: " + average);
        }
    }
}