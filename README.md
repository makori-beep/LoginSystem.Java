import java.util.Scanner;

public class LoginSystem {

    public static void main(String[] args) {
        // Predefined username and password
        final String correctUsername = "admin";
        final String correctPassword = "password123";

        Scanner scanner = new Scanner(System.in);

        int attempts = 3; // Maximum number of attempts
        boolean isAuthenticated = false;

        System.out.println("Welcome to the Login System!");

        // Loop to give the user 3 attempts
        while (attempts > 0) {
            System.out.print("Enter Username: ");
            String inputUsername = scanner.nextLine();

            System.out.print("Enter Password: ");
            StringBuilder passwordInput = new StringBuilder();

            // Mask password input with '*'
            while (true) {
                char input = scanner.next().charAt(0);
                if (input == '\n') break; // End input if Enter key is pressed
                passwordInput.append(input);
                System.out.print("*");
            }

            scanner.nextLine(); // Consume the leftover newline

            // Validate credentials
            if (inputUsername.equals(correctUsername) && passwordInput.toString().equals(correctPassword)) {
                isAuthenticated = true;
                break;
            } else {
                attempts--;
                System.out.println("\nIncorrect username or password. Attempts remaining: " + attempts);
            }
        }

        // Final output based on authentication
        if (isAuthenticated) {
            System.out.println("\nLogin successful! Welcome!");
        } else {
            System.out.println("\nToo many failed attempts. Access denied.");
        }

        scanner.close();
    }
}
