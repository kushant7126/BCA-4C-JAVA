# BCA-4C-JAVA
Dear Students, Java first assignment need to complete on time

Encapsulation in Java is the process by which data (variables) and the code that acts upon them (methods) are integrated as a single unit. By encapsulating a class's variables, other classes cannot access them, and only the methods of the class can access them. 
Create a class EMPLOYEE having data members as NameOfEmp, Emp-Id, BasicSalary and GrossSalary. NameOfEmp, Emp-Id, BasicSalary should be entered as user input. Calculate HRA (HRA is 25% of BasicSalary).Also, calculate DA (DA is 40% of BasicSalary). Then, calculate GrossSalary (GrossSalary=BasicSalary+HRA+DA). 
Implement the following queries: 
a) Display the NameOfEmp and GrossSalary of employees whose name starts With a consonent.
b) Display the Emp-Id and GrossSalary of Employees whose Emp-Id is between 101 and 150.
c) Count the total number of Employees whose GrossSalary is less than 35000/-

a) import java.util.Scanner;
class Employee {
    private String nameOfEmp;
    private int empId;
    private double basicSalary;
    private double grossSalary;

    // Constructor
    public Employee(String nameOfEmp, int empId, double basicSalary) {
        this.nameOfEmp = nameOfEmp;
        this.empId = empId;
        this.basicSalary = basicSalary;
        calculateGrossSalary();
    }

    // Method to calculate Gross Salary
    private void calculateGrossSalary() {
        double hra = 0.25 * basicSalary; // HRA is 25% of Basic Salary
        double da = 0.4 * basicSalary;   // DA is 40% of Basic Salary
        grossSalary = basicSalary + hra + da;
    }

    // Getter methods
    public String getNameOfEmp() {
        return nameOfEmp;
    }

    public double getGrossSalary() {
        return grossSalary;
    }

    // Method to check if a character is a consonant
    private static boolean isConsonant(char c) {
        c = Character.toUpperCase(c);
        return !(c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U');
    }

    // Method to check if the name starts with a consonant
    public boolean startsWithConsonant() {
        return isConsonant(nameOfEmp.charAt(0));
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter the number of employees: ");
        int numEmployees = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        Employee[] employees = new Employee[numEmployees];

        // Input employee details
        for (int i = 0; i < numEmployees; i++) {
            System.out.println("\nEnter details for employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.nextLine();
            System.out.print("Employee ID: ");
            int empId = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume newline

            employees[i] = new Employee(name, empId, basicSalary);
        }

        // Display employees whose name starts with a consonant along with their gross salary
        System.out.println("\nEmployees whose name starts with a consonant:");
        for (Employee employee : employees) {
            if (employee.startsWithConsonant()) {
                System.out.println("Name: " + employee.getNameOfEmp() + ", Gross Salary: " + employee.getGrossSalary());
            }
        }

        scanner.close();
    }
}
b)  import java.util.Scanner;

class EMPLOYEE {
    private String NameOfEmp;
    private int EmpId;
    private double BasicSalary;
    private double GrossSalary;

    // Constructor
    public EMPLOYEE(String nameOfEmp, int empId, double basicSalary) {
        this.NameOfEmp = nameOfEmp;
        this.EmpId = empId;
        this.BasicSalary = basicSalary;
        calculateGrossSalary();
    }

    // Method to calculate GrossSalary
    private void calculateGrossSalary() {
        double HRA = 0.25 * BasicSalary;
        double DA = 0.4 * BasicSalary;
        GrossSalary = BasicSalary + HRA + DA;
    }

    // Getter methods
    public int getEmpId() {
        return EmpId;
    }

    public double getGrossSalary() {
        return GrossSalary;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Taking input for number of employees
        System.out.print("Enter the number of employees: ");
        int numEmployees = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        // Creating an array to store employees
        EMPLOYEE[] employees = new EMPLOYEE[numEmployees];

        // Input employee details
        for (int i = 0; i < numEmployees; i++) {
            System.out.println("\nEnter details for employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.nextLine();
            System.out.print("Emp Id: ");
            int empId = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume newline

            employees[i] = new EMPLOYEE(name, empId, basicSalary);
        }

        // Query b) Display Emp-Id and GrossSalary for employees with Emp-Id between 101 and 150
        System.out.println("\nEmployees with Emp-Id between 101 and 150:");
        System.out.println("Emp-Id\tGross Salary");
        for (EMPLOYEE employee : employees) {
            if (employee.getEmpId() >= 101 && employee.getEmpId() <= 150) {
                System.out.println(employee.getEmpId() + "\t\t" + employee.getGrossSalary());
            }
        }
    }
}
c)  import java.util.Scanner;
class Employee {
    private String nameOfEmp;
    private int empId;
    private double basicSalary;
    private double grossSalary;

    // Constructor to initialize the data members
    public Employee(String nameOfEmp, int empId, double basicSalary) {
        this.nameOfEmp = nameOfEmp;
        this.empId = empId;
        this.basicSalary = basicSalary;
        calculateGrossSalary();
    }

    // Method to calculate HRA
    private double calculateHRA() {
        return 0.25 * basicSalary;
    }

    // Method to calculate DA
    private double calculateDA() {
        return 0.40 * basicSalary;
    }

    // Method to calculate Gross Salary
    private void calculateGrossSalary() {
        double hra = calculateHRA();
        double da = calculateDA();
        this.grossSalary = basicSalary + hra + da;
    }

    // Method to get Gross Salary
    public double getGrossSalary() {
        return grossSalary;
    }

    // Method to count employees with Gross Salary less than 35000
    public static int countEmployeesWithLowGrossSalary(Employee[] employees) {
        int count = 0;
        for (Employee emp : employees) {
            if (emp.getGrossSalary() < 35000) {
                count++;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Enter the number of employees:");
        int numberOfEmployees = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        Employee[] employees = new Employee[numberOfEmployees];

        // Input employee details
        for (int i = 0; i < numberOfEmployees; i++) {
            System.out.println("Enter details for employee " + (i + 1) + ":");
            System.out.print("Name: ");
            String name = scanner.nextLine();
            System.out.print("Employee ID: ");
            int id = scanner.nextInt();
            System.out.print("Basic Salary: ");
            double basicSalary = scanner.nextDouble();
            scanner.nextLine(); // Consume newline

            employees[i] = new Employee(name, id, basicSalary);
        }

        // Output count of employees with low Gross Salary
        int count = Employee.countEmployeesWithLowGrossSalary(employees);
        System.out.println("Total number of employees with Gross Salary less than 35000: " + count);

        scanner.close();
    }
}

