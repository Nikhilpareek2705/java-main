import java.util.Scanner;

public class SimpleNumberToWords {

    
    private static final String[] BELOW_TWENTY = {
        "", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine", "ten",
        "eleven", "twelve", "thirteen", "fourteen", "fifteen", "sixteen", "seventeen", "eighteen", "nineteen"
    };

    private static final String[] TENS = {
        "", "", "twenty", "thirty", "forty", "fifty", "sixty", "seventy", "eighty", "ninety"
    };

    private static String numberToWords(int num) {
        if (num == 0) {
            return "zero";
        }

     
        return helper(num);
    }

    
    private static String helper(int num) {
        if (num < 20) {
            return BELOW_TWENTY[num];  
        } else if (num < 100) {
            return TENS[num / 10] + (num % 10 != 0 ? " " + BELOW_TWENTY[num % 10] : "");
        } else if (num < 1000) {
            return BELOW_TWENTY[num / 100] + " hundred" + (num % 100 != 0 ? " " + helper(num % 100) : "");
        } else if (num < 1000000) {
            return helper(num / 1000) + " thousand" + (num % 1000 != 0 ? " " + helper(num % 1000) : "");
        } else {
            return helper(num / 1000000) + " million" + (num % 1000000 != 0 ? " " + helper(num % 1000000) : "");
        }
    }

    public static void main(String[] args) {
       
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a number: ");
        int num = scanner.nextInt();

      
        System.out.println("In words: " + numberToWords(num));
    }
}
