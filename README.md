# Assignment-1
using System;
using System.IO;
using System.Collections.Generic;
namespace Student
{
    class Program
    {
     string id, name, department, university, semester;
        double cgpa;
        public static void enterStudentInfo(Program sp)
        {
            Console.WriteLine("Enter number of student for which you want to save infromation: ");
            int num = Convert.ToInt32(Console.ReadLine());
            using (StreamWriter sw = new StreamWriter(@"C:\\Users\\zertashia shafiq\\Desktop\\vp a1.txt"))
            {
                for (int i = 0; i < num; i++)
                {
                    Console.WriteLine("\nEnter student ID: ");
                    sp.id = Console.ReadLine();
                    Console.WriteLine("\nEnter student Name: ");
                    sp.name = Console.ReadLine();
                    Console.WriteLine();
                    Console.WriteLine("\nEnter semester: ");
                    sp.semester = Console.ReadLine();
                    Console.WriteLine("\nEnter student CGPA: ");
                    sp.cgpa = Convert.ToDouble(Console.ReadLine());
                    Console.WriteLine("\nEnter student University: ");
                    sp.university = Console.ReadLine();
                    Console.ReadKey();
                    Console.WriteLine("\nEnter student Department: ");
                    sp.department = Console.ReadLine();
                    Console.WriteLine();
                    sw.WriteLine(sp.id);
                    sw.WriteLine(sp.name);
                    sw.WriteLine(sp.semester);
                    sw.WriteLine(sp.cgpa);
                    sw.WriteLine(sp.university);
                    sw.WriteLine(sp.department);
                    sw.WriteLine();
                }
            }
        }
        static void Main(string[] args)
        {
            Program obj = new Program();
            enterStudentInfo(obj);            
        }
    }   
}
