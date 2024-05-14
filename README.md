# CVIP-Internship-2
Student Information System
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Student {
    private String name;
    private int id;
    private String department;
    private List<String> courses;

    public Student(String name, int id, String department) {
        this.name = name;
        this.id = id;
        this.department = department;
        this.courses = new ArrayList<>();
    }

    public String getName() {
        return name;
    }

    public int getId() {
        return id;
    }

    public String getDepartment() {
        return department;
    }

    public List<String> getCourses() {
        return courses;
    }

    public void addCourse(String course) {
        courses.add(course);
    }

    @Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", id=" + id +
                ", department='" + department + '\'' +
                ", courses=" + courses +
                '}';
    }
}

class StudentDatabase {
    private List<Student> students;

    public StudentDatabase() {
        this.students = new ArrayList<>();
    }

    public void addStudent(Student student) {
        students.add(student);
    }

    public Student findStudentById(int id) {
        for (Student student : students) {
            if (student.getId() == id) {
                return student;
            }
        }
        return null;
    }

    public List<Student> getStudents() {
        return students;
    }
}

public class Main {
    public static void main(String[] args) {
        StudentDatabase database = new StudentDatabase();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nStudent Information System");
            System.out.println("1. Add Student");
            System.out.println("2. Find Student by ID");
            System.out.println("3. Display All Students");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter student name: ");
                    String name = scanner.next();
                    System.out.print("Enter student ID: ");
                    int id = scanner.nextInt();
                    scanner.nextLine(); // Consume newline
                    System.out.print("Enter student department: ");
                    String department = scanner.nextLine();
                    Student student = new Student(name, id, department);
                    database.addStudent(student);
                    System.out.println("Student added successfully!");
                    break;
                case 2:
                    System.out.print("Enter student ID to find: ");
                    int searchId = scanner.nextInt();
                    Student foundStudent = database.findStudentById(searchId);
                    if (foundStudent != null) {
                        System.out.println("Student found:");
                        System.out.println(foundStudent);
                    } else {
                        System.out.println("Student not found!");
                    }
                    break;
                case 3:
                    System.out.println("All Students:");
                    for (Student s : database.getStudents()) {
                        System.out.println(s);
                    }
                    break;
                case 4:
                    System.out.println("Exiting...");
                    System.exit(0);
                default:
                    System.out.println("Invalid choice! Please try again.");
            }
        }
    }
}


/* output for this program
Student Information System
1. Add Student
2. Find Student by ID
3. Display All Students
4. Exit
Enter your choice: 1
Enter student name: vaishnavi
Enter student ID: 777
Enter student department: computer engineering            
Student added successfully!

Student Information System
1. Add Student
2. Find Student by ID
3. Display All Students
4. Exit
Enter your choice: 1
Enter student name: siranjeevi
Enter student ID: 191 
Enter student department: electronic enginerring
Student added successfully!

Student Information System
1. Add Student
2. Find Student by ID
3. Display All Students
4. Exit
Enter your choice: 1        
Enter student name: venkatesh
Enter student ID: 121
Enter student department: information technology
Student added successfully!

Student Information System
1. Add Student
2. Find Student by ID
3. Display All Students
4. Exit
Enter your choice: 2
Enter student ID to find: 121
Student found:
Student{name='venkatesh', id=121, department='information technology', courses=[]}

Student Information System
1. Add Student
2. Find Student by ID
3. Display All Students
4. Exit
Enter your choice: 3 
All Students:
Student{name='vaishnavi', id=777, department='computer engineering', courses=[]}
Student{name='siranjeevi', id=191, department='electronic enginerring', courses=[]}
Student{name='venkatesh', id=121, department='information technology', courses=[]}

Student Information System
1. Add Student
2. Find Student by ID
3. Display All Students
4. Exit
Enter your choice: 4
Exiting...  */
