```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] timeTable = new int[n];
        int[] payTable = new int[n];
        int[] dpTable = new int[n + 1];
        int maxValue = 0;

        for (int i = 0; i < n; i++) {
            int time = scanner.nextInt();
            int pay = scanner.nextInt();
            timeTable[i] = time;
            payTable[i] = pay;
        }

        for (int i = n - 1; i >= 0; i--) {
            int time = i + timeTable[i];
            if (time <= n) {
                dpTable[i] = Math.max(payTable[i] + dpTable[time], maxValue);
                maxValue = dpTable[i];
            } else {
                dpTable[i] = maxValue;
            }
        }

        System.out.println(dpTable[0]);
    }
}
```