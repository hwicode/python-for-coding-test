```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

    public static int[] array;
    public static int[] dp;

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();

        array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }

        dp = new int[n];
        Arrays.fill(dp, 1);

        for (int now = 0; now < n; now++) {
            for (int i = 0; i < now; i++) {
                if (array[i] > array[now]) {
                    dp[now] = Math.max(dp[i] + 1, dp[now]);
                }
            }
        }

        int max = 0;
        for (int i = 0; i < n; i++) {
            max = Math.max(max, dp[i]);
        }

        System.out.println(n - max);
    }

}

```
