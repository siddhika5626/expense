# expense
import java.util.ArrayList;
import java.util.Scanner;

class Expense {
    String category;
    double amount;

    // Constructor
    public Expense(String category, double amount) {
        this.category = category;
        this.amount = amount;
    }

    @Override
    public String toString() {
        return "Category: " + category + ", Amount: $" + String.format("%.2f", amount);
    }
}

public class StudentExpenseChecker {

    private static ArrayList<Expense> expenses = new ArrayList<>();
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {
        while (true) {
            System.out.println("\nStudent Expense Checker");
            System.out.println("1. Add an expense");
            System.out.println("2. View all expenses");
            System.out.println("3. Exit");

            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine();  // Consume the newline character

            switch (choice) {
                case 1:
                    addExpense();
                    break;
                case 2:
                    viewExpenses();
                    break;
                case 3:
                    System.out.println("Exiting the program. Goodbye!");
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
        }
    }

    private static void addExpense() {
        System.out.print("Enter the expense category (e.g., food, transportation, books, etc.): ");
        String category = scanner.nextLine();

        System.out.print("Enter the amount spent: ");
        double amount = scanner.nextDouble();
        scanner.nextLine();  // Consume the newline character

        // Create a new expense object and add it to the list
        expenses.add(new Expense(category, amount));
        System.out.println("Expense added successfully.");
    }

    private static void viewExpenses() {
        if (expenses.isEmpty()) {
            System.out.println("No expenses recorded.");
            return;
        }

        System.out.println("\n--- Expense Report ---");
        double total = 0;
        for (Expense expense : expenses) {
            System.out.println(expense);
            total += expense.amount;
        }

        System.out.println("\nTotal Expenses: $" + String.format("%.2f", total));
    }
}
