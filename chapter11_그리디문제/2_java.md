```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String s = scanner.nextLine();

        int result = 0;
        for (int i = 0; i < s.length(); i++) {
            int number = s.charAt(i) - '0';
            if (number <= 1 || result <= 1) {
                result += number;
            } else {
                result *= number;
            }
        }

        System.out.println(result);
    }

}
```