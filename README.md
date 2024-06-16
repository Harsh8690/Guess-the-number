# Guess-the-number
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();
        int numRounds = 3;
        int numAttempts = 5;
        int score = 0;

        for (int i = 0; i < numRounds; i++) {
            int randomNumber = random.nextInt(100) + 1;
            System.out.println("Round " + (i + 1));
            System.out.println("Guess the number between 1 and 100");
            int attemptsLeft = numAttempts;
            boolean guessed = false;
            while (!guessed && attemptsLeft > 0) {
                System.out.println("Attempts left: " + attemptsLeft);
                System.out.print("Enter your guess: ");
                int guess = scanner.nextInt();
                attemptsLeft--;
                if (guess == randomNumber) {
                    guessed = true;
                    System.out.println("Congratulations! You guessed the number.");
                    score += numAttempts - attemptsLeft;
                } else if (guess < randomNumber) {
                    System.out.println("Too low. Try again.");
                } else {
                    System.out.println("Too high. Try again.");
                }
            }
            if (!guessed) {
                System.out.println("Sorry, you didn't guess the number. The correct number was " + randomNumber);
            }
            System.out.println("Your score for this round is: " + (numAttempts - attemptsLeft) * 10);
            System.out.println();
        }

        System.out.println("Your total score is: " + score);
        scanner.close();
    }
}
