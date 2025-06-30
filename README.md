# import java.util.ArrayList;
import java.util.Scanner;

class Student {
    String name;
    double grade;

    public Student(String name, double grade) {
        this.name = name;
        this.grade = grade;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Student> students = new ArrayList<>();

        System.out.print("Enter the number of students: ");
        int numStudents = scanner.nextInt();
        
        for (int i = 0; i < numStudents; i++) {
            System.out.print("Enter student name: ");
            String name = scanner.next(); // Using next() to avoid newline issues
            
            System.out.print("Enter grade: ");
            double grade = scanner.nextDouble();

            students.add(new Student(name, grade));
        }

        double totalGrades = 0;
        double highest = students.get(0).grade; // Initialize with first student's grade
        double lowest = students.get(0).grade;

        for (Student student : students) {
            totalGrades += student.grade;
            if (student.grade > highest) {
                highest = student.grade;
            }
            if (student.grade < lowest) {
                lowest = student.grade;
            }
        }

        double average = totalGrades / students.size();

        System.out.println("\n--- Student Grade Summary ---");
        for (Student student : students) {
            System.out.println(student.name + ": " + student.grade);
        }
        System.out.printf("\nAverage Grade: %.2f\n", average);
        System.out.printf("Highest Grade: %.2f\n", highest);
        System.out.printf("Lowest Grade: %.2f\n", lowest);

        scanner.close();
    }
}
