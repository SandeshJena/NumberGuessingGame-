# NumberGuessingGame-
import java.util.Random;
import java.util.Scanner;

public class GuessingGame {

    // Method to play a single round of the game
    public static boolean playRound() {
        Random random = new Random();
        int secretNumber = random.nextInt(100) + 1;  // Generate a number between 1 and 100
        int attemptsLeft = 10;

        Scanner scanner = new Scanner(System.in);

        System.out.println("Welcome to the Guessing Game!");
        System.out.println("I have selected a number between 1 and 100.");
        System.out.println("You have 10 attempts to guess it correctly.");

        while (attemptsLeft > 0) {
            // Prompt the user for their guess
            System.out.print("You have " + attemptsLeft + " attempts left. Enter your guess: ");
            int guess = scanner.nextInt();

            // Compare the guess with the secret number and provide feedback
            if (guess < secretNumber) {
                System.out.println("Too low!");
            } else if (guess > secretNumber) {
                System.out.println("Too high!");
            } else {
                System.out.println("Congratulations! You guessed the correct number " + secretNumber + "!");
                return true;  // User guessed correctly
            }

            attemptsLeft--;
        }

        System.out.println("Sorry! You've run out of attempts. The correct number was " + secretNumber + ".");
        return false;  // User failed to guess correctly
    }

    public static void main(String[] args) {
        int totalRounds = 0;
        int totalWins = 0;

        Scanner scanner = new Scanner(System.in);

        while (true) {
            // Play a round
            if (playRound()) {
                totalWins++;
            }
            totalRounds++;

            // Ask the user if they want to play again
            System.out.print("Do you want to play another round? (yes/no): ");
            String playAgain = scanner.next().toLowerCase();

            if (!playAgain.equals("yes")) {
                break;
            }
        }

        // Display the user's score
        System.out.println("\nGame Over! You played " + totalRounds + " round(s) and won " + totalWins + " time(s).");
        System.out.println("Thanks for playing!");
    }
}
