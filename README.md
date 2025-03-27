# Convert-number-system-
import java.util.Scanner;

public class NumberSystemConverter {

    public static String convertBase(String number, int fromBase, int toBase) {
        int decimalValue = Integer.parseInt(number, fromBase);
        return Integer.toString(decimalValue, toBase).toUpperCase();
    }

    public static String addNumbers(String num1, int base1, String num2, int base2, int resultBase) {
        int value1 = Integer.parseInt(num1, base1);
        int value2 = Integer.parseInt(num2, base2);
        int sum = value1 + value2;
        return Integer.toString(sum, resultBase).toUpperCase();
    }

    public static String subtractNumbers(String num1, int base1, String num2, int base2, int resultBase) {
        int value1 = Integer.parseInt(num1, base1);
        int value2 = Integer.parseInt(num2, base2);
        int difference = value1 - value2;
        return Integer.toString(difference, resultBase).toUpperCase();
    }

    public static String onesComplement(String binary) {
        StringBuilder complement = new StringBuilder();
        for (char bit : binary.toCharArray()) {
            complement.append(bit == '0' ? '1' : '0');
        }
        return complement.toString();
    }

    public static String twosComplement(String binary) {
        String onesComp = onesComplement(binary);
        int decimalValue = Integer.parseInt(onesComp, 2) + 1;
        return Integer.toBinaryString(decimalValue);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("\nChoose an operation:");
            System.out.println("1. Convert number");
            System.out.println("2. Add numbers");
            System.out.println("3. Subtract numbers");
            System.out.println("4. One's Complement");
            System.out.println("5. Two's Complement");
            System.out.println("6. Exit");
            System.out.print("Enter choice: ");
            int choice = scanner.nextInt();

            if (choice == 6) break;

            switch (choice) {
                case 1:
                    System.out.print("Enter number: ");
                    String number = scanner.next();
                    System.out.print("Enter from base (2, 8, 10, 16): ");
                    int fromBase = scanner.nextInt();
                    System.out.print("Enter to base (2, 8, 10, 16): ");
                    int toBase = scanner.nextInt();
                    System.out.println("Converted: " + convertBase(number, fromBase, toBase));
                    break;

                case 2:
                    System.out.print("Enter first number: ");
                    String num1 = scanner.next();
                    System.out.print("Enter its base: ");
                    int base1 = scanner.nextInt();
                    System.out.print("Enter second number: ");
                    String num2 = scanner.next();
                    System.out.print("Enter its base: ");
                    int base2 = scanner.nextInt();
                    System.out.print("Enter result base: ");
                    int resultBase = scanner.nextInt();
                    System.out.println("Sum: " + addNumbers(num1, base1, num2, base2, resultBase));
                    break;

                case 3:
                    System.out.print("Enter first number: ");
                    String subNum1 = scanner.next();
                    System.out.print("Enter its base: ");
                    int subBase1 = scanner.nextInt();
                    System.out.print("Enter second number: ");
                    String subNum2 = scanner.next();
                    System.out.print("Enter its base: ");
                    int subBase2 = scanner.nextInt();
                    System.out.print("Enter result base: ");
                    int subResultBase = scanner.nextInt();
                    System.out.println("Difference: " + subtractNumbers(subNum1, subBase1, subNum2, subBase2, subResultBase));
                    break;

                case 4:
                    System.out.print("Enter binary number: ");
                    String binary = scanner.next();
                    System.out.println("One's Complement: " + onesComplement(binary));
                    break;

                case 5:
                    System.out.print("Enter binary number: ");
                    String bin = scanner.next();
                    System.out.println("Two's Complement: " + twosComplement(bin));
                    break;

                default:
                    System.out.println("Invalid choice! Try again.");
            }
        }
        scanner.close();
    }
}
