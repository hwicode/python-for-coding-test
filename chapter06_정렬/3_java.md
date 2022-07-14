```java
import java.util.Arrays;
import java.util.Collections;
import java.util.Scanner;

public class algorithm {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int k = scanner.nextInt();

        Integer[] arrayA = new Integer[n];
        Integer[] arrayB = new Integer[n];

        for (int i = 0; i < n; i++) {
            arrayA[i] = scanner.nextInt();
        }

        for (int i = 0; i < n; i++) {
            arrayB[i] = scanner.nextInt();
        }

        Arrays.sort(arrayA);
        Arrays.sort(arrayB, Collections.reverseOrder());

        for (int i = 0; i < k; i++) {
            if (arrayA[i] < arrayB[i]) {
                int temp = arrayA[i];
                arrayA[i] = arrayB[i];
                arrayB[i] = temp;
            } else {
                break;
            }
        }

        int sum = 0;
        for (int i = 0; i < n; i++) {
            sum += arrayA[i];
        }

        System.out.println(sum);
        
    }
}
```
