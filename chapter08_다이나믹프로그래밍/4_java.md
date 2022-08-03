```java
import java.util.Scanner;

public class algorithm {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        int[] array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }

        int[] dpTable = new int[m + 1];
        for (int i = 0; i < m + 1; i++) {
            dpTable[i] = 10001;
        }

        dpTable[0] = 0;
        for (int i = 0; i < n; i++) {
            for (int j = array[i]; j < m + 1; j++) {
                dpTable[j] = Math.min(dpTable[j], dpTable[j - array[i]] + 1);
            }
        }

        if (dpTable[m] == 10001) {
            System.out.println(-1);
        } else {
            System.out.println(dpTable[m]);
        }

    }

}

```
