using System;
using System.Collections.Generic;

namespace StudentsList
{
    public class Student
    {
        public int Id { get; set; }
        public string? Name { get; set; }
        public int Marks { get; set; }
    }

    class Program
    {
        static List<Student> students = new List<Student>();

        static void Main(string[] args)
        {
            while (true)
            {
                Console.WriteLine("Student's System");
                Console.WriteLine("1- Student's Name");
                Console.WriteLine("2- Update Student");
                Console.WriteLine("3- Delete Student");
                Console.WriteLine("4- Exit");
                Console.Write("Enter number: ");
                int choice = Convert.ToInt32(Console.ReadLine());

                switch (choice)
                {
                    case 1:
                        AddStudent();
                        break;
                    case 2:
                        UpdateStudent();
                        break;
                    case 3:
                        DeleteStudent();
                        break;
                    case 4:
                        Environment.Exit(0);
                        break;
                    default:
                        Console.WriteLine("Invalid Option, Re-Enter Please.");
                        break;
                }
            }
        }

        static void AddStudent()
        {
            Console.Write("Enter student's Name: ");
            int id = Convert.ToInt32(Console.ReadLine());

            Console.Write("Enter student marks: ");
            int marks = Convert.ToInt32(Console.ReadLine());

            Console.WriteLine("Added successfully");
        }

        static void UpdateStudent()
        {
            Console.Write("Enter student's name to update: ");
            int id = Convert.ToInt32(Console.ReadLine());

            Student? student = students.Find(s => s.Id == id);
            if (student == null)
            {
                Console.WriteLine("Not found.");
                return;
            }

            Console.Write("Enter updated student name: ");
            string? name = Console.ReadLine();

            Console.Write("Enter updated student marks: ");
            int marks = Convert.ToInt32(Console.ReadLine());

            student.Name = name;
            student.Marks = marks;

            Console.WriteLine("Updated successfully!");
        }
         static void DeleteStudent()
         {
         Console.Write("Enter Student's Name: ");
         if (int.TryParse(Console.ReadLine(), out int id))
          {
         bool studentExists = students.Any(student => student.Id == id);
           if (studentExists)
         {
            students.RemoveAll(student => student.Id == id);
            Console.WriteLine("Student deleted successfully!");
         }
         else
         {
            Console.WriteLine("Not found.");
         }
         }
         else
         {
          Console.WriteLine("Invalid Option, Re-Enter Please.");
         }
       }
     }
}
