```java
import java.util.Scanner;

public class algorithm {

    public static void main(String[] args) {
        
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] k = new int[n];
        for (int i = 0; i < n; i++) {
            k[i] = scanner.nextInt();
        }

        int[] dpTable = new int[n];

        dpTable[0] = k[0];
        dpTable[1] = Math.max(k[0], k[1]);

        for (int i = 2; i < n; i++) {
            dpTable[i] = Math.max((k[i] + dpTable[i - 2]), dpTable[i - 1]);
        }

        System.out.println(dpTable[n - 1]);
    }

}

```
