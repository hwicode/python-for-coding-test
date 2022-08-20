```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String s = scanner.nextLine();

        int middle = s.length() / 2;
        String frontString = s.substring(0, middle);
        String endString = s.substring(middle);

        int frontSum = 0;
        for (int i = 0; i < frontString.length(); i++) {
            frontSum += frontString.charAt(i) - '0';
        }

        int endSum = 0;
        for (int i = 0; i < endString.length(); i++) {
            endSum += endString.charAt(i) - '0';
        }

        if (frontSum == endSum) {
            System.out.println("LUCKY");
        } else {
            System.out.println("READY");
        }

    }

}

```