using System;
using System.IO;
using System.Collections.Generic;
using System.Text;
using System.Threading.Tasks;
using System.Linq;

namespace studentProfile
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
                    sw.Close();
                }
            }
        }

        public static void searchByName(Program sp)
        {

            string[] words = File.ReadAllLines(@"C:\\Users\\zertashia shafiq\\Desktop\\vp a1.txt");
            Console.WriteLine("Enter name: ");
            string search = Console.ReadLine();
            bool condition = false;
            for (int i = 0; i < words.Length; i++)
            {
                if (words[i].Contains(search) == true)
                {
                    Console.WriteLine("\nID: " + words[i - 1] + "\nName: " + words[i] + "\nSemester: " + words[i + 1] + "\nCGPA: " + words[i + 2] + "\nUniversity: " + words[i + 3] + "\nDepartement: " + words[i + 4]);
                    condition = true;
                    break;
                }
                else
                {

                    condition = false;

                }

            }
            if (condition == false)
            {
                Console.WriteLine("\nSorry No record found against this name!");
            }


        }
        public static void searchById(Program sp)
        {

            string[] words = File.ReadAllLines(@"C:\\Users\\zertashia shafiq\\Desktop\\vp a1.txt");
            Console.WriteLine("Enter ID: ");
            string search = Console.ReadLine();
            bool condition = false;
            for (int i = 0; i < words.Length; i++)
            {
                if (words[i].Contains(search) == true)
                {
                    Console.WriteLine("\nID: " + words[i] + "\nName: " + words[i + 1] + "\nSemester: " + words[i + 2] + "\nCGPA: " + words[i + 3] + "\nUniversity: " + words[i + 4] + "\nDepartement: " + words[i + 5]);
                    condition = true;
                    break;
                }
                else
                {

                    condition = false;

                }

            }
            if (condition == false)
            {
                Console.WriteLine("\nSorry No record found against this ID!");
            }


        }





        static void Main(string[] args)
        {
            Program obj = new Program();
            Console.Write("\n1. Create Student Profile\n2 Search student\n3.Delete Student Record\n4.Delete Student Record\n5.Mark student attendence\n6View Attendence\n");
            int choice = Convert.ToInt32(Console.ReadLine());
            switch (choice)
            {
                case 1:
                    enterStudentInfo(obj);
                    break;
                case 2:
                    Console.WriteLine("\n1.Search By Name\n2.Search By ID\n");
                    int ch = Convert.ToInt32(Console.ReadLine());
                    if (ch == 1)
                    {
                        searchByName(obj);
                    }
                    else if (ch == 2)
                    {
                        searchById(obj);
                    }

                    break;


            }
        }
    }
}
