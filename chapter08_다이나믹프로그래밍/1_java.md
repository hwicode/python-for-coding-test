```java
import java.util.Scanner;

public class algorithm {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] dpTable = new int[30001];

        for (int i = 2; i < n + 1; i++) {

            dpTable[i] = dpTable[i - 1] + 1;

            if (i % 5 == 0) {
                dpTable[i] = Math.min(dpTable[i], dpTable[i / 5] + 1);
            }

            if (i % 3 == 0) {
                dpTable[i] = Math.min(dpTable[i], dpTable[i / 3] + 1);
            }

            if (i % 2 == 0) {
                dpTable[i] = Math.min(dpTable[i], dpTable[i / 2] + 1);
            }
        }

        System.out.println(dpTable[n]);
    }

}

```
