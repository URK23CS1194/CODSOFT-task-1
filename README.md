````
# CODSOFT-task-1
package codsoft.task1;
import java.util.Scanner;
import java.util.Random;
public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int totalRounds = 0;
        int totalWins = 0;
        boolean playAgain;
        System.out.println("Welcome to the Number Guessing Game");
        do {
            int targetNumber = random.nextInt(100) + 1;
            int maxAttempts = 7;
            int attempts = 0;
            boolean guessedCorrectly = false;
            System.out.println("\nRound " + (totalRounds + 1));
            System.out.println("You have " + maxAttempts + " chances to guess the number between 1 and 100.");
            while (attempts < maxAttempts) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();
                attempts++;
                if (userGuess == targetNumber) {
                    System.out.println("Correct! You guessed the number in " + attempts + " attempt(s).");
                    guessedCorrectly = true;
                    totalWins++;
                    break;
                } else if (userGuess < targetNumber) {
                    System.out.println("Your guess is too low.");
                } else {
                    System.out.println("Your guess is too high.");
                }
            }

            if (!guessedCorrectly) {
                System.out.println("You have used all attempts. The correct number was: " + targetNumber);
            }
            totalRounds++;
            System.out.print("Do you want to play another round? Type 'yes' or 'no': ");
            String response = scanner.next();
            playAgain = response.equalsIgnoreCase("yes");
        } while (playAgain);
        System.out.println("\nGame Summary");
        System.out.println("Total Rounds Played: " + totalRounds);
        System.out.println("Total Rounds Won: " + totalWins);
        scanner.close();
    }
}
