import java.util.Scanner;

// Custom exceptions
class InvalidInputException extends Exception {
    public InvalidInputException(String message) {
        super(message);
    }
}

class DivideByZeroException extends Exception {
    public DivideByZeroException(String message) {
        super(message);
    }
}

class MaxInputException extends Exception {
    public MaxInputException(String message) {
        super(message);
    }
}

class MaxMultiplierException extends Exception {
    public MaxMultiplierException(String message) {
        super(message);
    }
}

public class CustomCalculator {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Custom Calculator");
        System.out.println("Operations: +, -, *, /");
        System.out.println("Enter your expression (e.g., 5 + 3): ");

        try {
            String input = scanner.nextLine();
            double result = calculate(input);
            System.out.println("Result: " + result);
        }
        catch (InvalidInputException e) {
            System.out.println("Error: " + e.getMessage());
        }
        catch (DivideByZeroException e) {
            System.out.println("Error: " + e.getMessage());
        }
        catch (MaxInputException e) {
            System.out.println("Error: " + e.getMessage());
        }
        catch (MaxMultiplierException e) {
            System.out.println("Error: " + e.getMessage());
        }
        finally {
            scanner.close();
        }
    }

    public static double calculate(String input) throws
            InvalidInputException, DivideByZeroException, MaxInputException, MaxMultiplierException {

        // Split the input string into parts
        String[] parts = input.split("\\s+");

        // Check for valid input format (should have exactly 3 parts: num op num)
        if (parts.length != 3) {
            throw new InvalidInputException("Invalid input format. Expected format: number operator number");
        }

        double num1, num2;
        String operator = parts[1];

        try {
            num1 = Double.parseDouble(parts[0]);
            num2 = Double.parseDouble(parts[2]);
        }
        catch (NumberFormatException e) {
            throw new InvalidInputException("Invalid number format in input");
        }

        // Check for max input exception
        if (Math.abs(num1) > 100000 || Math.abs(num2) > 100000) {
            throw new MaxInputException("Input numbers cannot be greater than 100000");
        }

        // Perform the operation based on the operator
        switch (operator) {
            case "+":
                return num1 + num2;
            case "-":
                return num1 - num2;
            case "*":
                // Check for max multiplier exception
                if (num1 > 7000 || num2 > 7000) {
                    throw new MaxMultiplierException("Multiplication input cannot be greater than 7000");
                }
                return num1 * num2;
            case "/":
                if (num2 == 0) {
                    throw new DivideByZeroException("Cannot divide by zero");
                }
                return num1 / num2;
            default:
                throw new InvalidInputException("Invalid operator. Valid operators are +, -, *, /");
        }
    }
}
