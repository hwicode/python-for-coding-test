```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String s = scanner.nextLine();

        int firstCount = 0;
        int secondCount = 0;

        boolean key = true;

        char x = s.charAt(0);
        secondCount++;

        for (int i = 1; i < s.length(); i++) {
            if (s.charAt(i) != x) {
                x = s.charAt(i);

                if (key) {
                    firstCount++;
                } else {
                    secondCount++;
                }
                key = !key;
            }
        }

        System.out.println(Math.min(firstCount, secondCount));
    }

}

```