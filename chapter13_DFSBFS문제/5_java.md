```java
import java.util.Scanner;

public class Main {

    public static int n;
    public static int[] array;

    public static int plusNumber, subtractNumber, multiplyNumber, divideNumber;

    public static int maxValue = (int) -1e9;
    public static int minValue = (int) 1e9;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        n = scanner.nextInt();

        array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }

        plusNumber = scanner.nextInt();
        subtractNumber = scanner.nextInt();
        multiplyNumber = scanner.nextInt();
        divideNumber = scanner.nextInt();

        dfs(1, array[0]);

        System.out.println(maxValue);
        System.out.println(minValue);
    }

    public static void dfs(int i, int now) {
        if (i == n) {
            maxValue = Math.max(maxValue, now);
            minValue = Math.min(minValue, now);
        } else {

            if (plusNumber > 0) {
                plusNumber--;
                dfs(i + 1, now + array[i]);
                plusNumber++;
            }

            if (subtractNumber > 0) {
                subtractNumber--;
                dfs(i + 1, now - array[i]);
                subtractNumber++;
            }

            if (multiplyNumber > 0) {
                multiplyNumber--;
                dfs(i + 1, now * array[i]);
                multiplyNumber++;
            }

            if (divideNumber > 0) {
                divideNumber--;
                dfs(i + 1, now / array[i]);
                divideNumber++;
            }
        }
    }

}
```