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


        public static void deleteRecord()
        {
            List<string> line = File.ReadAllLines(@"C:\\Users\\zertashia shafiq\\Desktop\\vp a1.txt").ToList();
            Console.WriteLine("Enter ID: ");
            string id = Console.ReadLine();
            for (int i=0;i<line.Count;i++)
            {
                if(line[i]==id)
                {
                    line.RemoveAt(0);
                   for(int j=0;j<6;j++)

                    {
                        line.RemoveAt(0);

                       
                    }
                }
            }
            File.WriteAllLines(@"C:\\Users\\zertashia shafiq\\Desktop\\vp a1.txt", line.ToArray());
        }

        public static void markAttendence()
        {

            string[] words = File.ReadAllLines(@"C:\\Users\\zertashia shafiq\\Desktop\\vp a1.txt");
            string[] attend = new string[words.Length];
            string[] id = new string[words.Length];
            Console.WriteLine("press 'a' to mark absent\tpress 'p' to mark present against each ID\n\n");
            string mark;
            for(int i = 0;i < words.Length;i=i+7)
            {
                id[i] = words[i];
                Console.Write("Student ID: "+id[i]+"\t\ta/p: ");
                mark = Console.ReadLine();
                if(mark=="p")
                {
                    attend[i] = "present";
                }
                else if(mark=="a")
                {
                    attend[i] = "absent";
                }

            }
            int j = 0;
           
            using(StreamWriter sw=new StreamWriter(@"C:\\Users\\zertashia shafiq\\Desktop\\vp a1.txt"))
            {
                for(int i=0; i<words.Length; i=i+7)
                {
                    sw.WriteLine(words[i]);
                    sw.WriteLine(words[i+1]);
                    sw.WriteLine(words[i+2]);
                    sw.WriteLine(words[i+3]);
                    sw.WriteLine(words[i+4]);
                    sw.WriteLine(words[i+5]);
                    sw.WriteLine(attend[j]);
                    j = j + 7;
                }
            }


                }

        static void Main(string[] args)
        {
            Program obj = new Program();
            Console.Write("\n1.Create Student Profile\n2 Search student\n3.Delete Student Record\n4.List top 3 of class\n5.Mark student attendence\n6.View Attendence\n");
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
                case 3:
                    deleteRecord();
                    break;
                case 4:
                    break;
                case 5:
                    markAttendence();
                    break;


            }
        }
    }
}
