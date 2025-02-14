[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/kEz0V4IK)

1. Java Program to Calculate Square Root (with Try-Catch for Error Handling):

import java.util.Scanner;

public class SquareRootCalculator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        try {
            System.out.print("Enter a number to calculate its square root: ");
            String input = scanner.nextLine();
            double number = Double.parseDouble(input);
            
            if (number < 0) {
                throw new IllegalArgumentException("Negative numbers cannot have a real square root.");
            }
            
            double squareRoot = Math.sqrt(number);
            System.out.println("The square root of " + number + " is " + squareRoot);
        } catch (NumberFormatException e) {
            System.out.println("Invalid input! Please enter a numeric value.");
        } catch (IllegalArgumentException e) {
            System.out.println(e.getMessage());
        } catch (Exception e) {
            System.out.println("An unexpected error occurred: " + e.getMessage());
        } finally {
            System.out.println("Program has ended.");
        }
    }
}

2. Java Program to Simulate an ATM Withdrawal System (with Exception Handling):

import java.util.Scanner;

class InvalidPinException extends Exception {
    public InvalidPinException(String message) {
        super(message);
    }
}

class InsufficientBalanceException extends Exception {
    public InsufficientBalanceException(String message) {
        super(message);
    }
}

public class ATMSimulation {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String correctPin = "1234"; // Example PIN
        double balance = 1000.00;  // Example balance
        
        try {
            System.out.print("Enter your PIN: ");
            String enteredPin = scanner.nextLine();
            
            if (!enteredPin.equals(correctPin)) {
                throw new InvalidPinException("Invalid PIN! Please try again.");
            }

            System.out.print("Enter amount to withdraw: ");
            double amount = scanner.nextDouble();
            
            if (amount > balance) {
                throw new InsufficientBalanceException("Insufficient balance for this transaction.");
            }

            balance -= amount;  // Deduct the amount
            System.out.println("Withdrawal successful! You have withdrawn $" + amount);
        } catch (InvalidPinException e) {
            System.out.println(e.getMessage());
        } catch (InsufficientBalanceException e) {
            System.out.println(e.getMessage());
        } catch (Exception e) {
            System.out.println("An unexpected error occurred: " + e.getMessage());
        } finally {
            System.out.println("Your remaining balance is: $" + balance);
            System.out.println("Thank you for using our ATM.");
        }
    }
}


