using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp20
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] testPoints = { -1, 0, 50, 99, 100, 150, 199, 200, 350, 499, 500, 501, 1000 };

            foreach (int points in testPoints)
            {
                try
                {
                    int discount = CalculateDiscount(points);
                    Console.WriteLine($"Баллы: {points} -> Скидка: {discount}%");
                }
                catch (ArgumentException ex)
                {
                    Console.WriteLine($"Баллы: {points} -> Ошибка: {ex.Message}");
                }
            }
        }
        static int CalculateDiscount(int points)
        {
            if (points < 0)
            {
                throw new ArgumentException("Количество баллов не может быть отрицательным");
            }

            if (points >= 500) return 10;
            if (points >= 200) return 5;
            if (points >= 100) return 3;
            return 1;
        }
    }
}
