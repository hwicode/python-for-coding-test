```java
import java.util.Scanner;

public class algorithm {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] dpTable = new int[n];

        dpTable[0] = 1;
        dpTable[1] = 3;

        for (int i = 2; i < n; i++) {
            dpTable[i] = (dpTable[i - 2] * 2 + dpTable[i - 1]) % 796796;
        }

        System.out.println(dpTable[n - 1]);
    }

}
```
