```java
import java.util.Scanner;

public class Main {

    public static int[][] dpTable = new int[500][500];

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < i + 1; j++) {
                dpTable[i][j] = scanner.nextInt();
            }
        }

        for (int i = 1; i < n; i++) {
            for (int j = 0; j < i + 1; j++) {
                int up, upLeft;

                if (j == 0) {
                    upLeft = 0;
                } else {
                    upLeft = dpTable[i - 1][j - 1];
                }

                if (j == i) {
                    up = 0;
                } else {
                    up = dpTable[i - 1][j];
                }

                dpTable[i][j] = dpTable[i][j] + Math.max(upLeft, up);
            }
        }

        int result = 0;
        for (int i = 0; i < n; i++) {
            result = Math.max(result, dpTable[n - 1][i]);
        }

        System.out.println(result);
    }

}

```