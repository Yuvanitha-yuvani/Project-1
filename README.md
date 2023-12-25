# Project-1
import java.security.SecureRandom;

public class RandomPasswordGenerator {

    private static final String UPPERCASE = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    private static final String LOWERCASE = "abcdefghijklmnopqrstuvwxyz";
    private static final String DIGITS = "0123456789";
    private static final String SPECIAL_CHARACTERS = "!@#$%^&*()-_=+[]{}|;:'\",.<>/?";

    public static void main(String[] args) {
        int passwordLength = getPasswordLength();
        String password = generateRandomPassword(passwordLength);
        System.out.println("Generated Password: " + password);
    }

    private static int getPasswordLength() {
        System.out.print("Enter the desired password length: ");
        try {
            return Integer.parseInt(System.console().readLine());
        } catch (NumberFormatException e) {
            System.out.println("Invalid input. Using default password length (12).");
            return 12;
        }
    }

    private static String generateRandomPassword(int length) {
        SecureRandom random = new SecureRandom();
        StringBuilder password = new StringBuilder();

        String allCharacters = UPPERCASE + LOWERCASE + DIGITS + SPECIAL_CHARACTERS;

        for (int i = 0; i < length; i++) {
            int randomIndex = random.nextInt(allCharacters.length());
            password.append(allCharacters.charAt(randomIndex));
        }

        return password.toString();
    }
}
