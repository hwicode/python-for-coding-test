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

        int start = 0;
        int end = (int) 1e9;

        int result = 0;
        while (start <= end) {
            long total = 0;
            int mid = (start + end) / 2;
            
            for (int i = 0; i < n; i++) {
                if (array[i] > mid) {
                    total += array[i] - mid;
                }
            }
            
            if (total < m) {
                end = mid - 1;
            } else {
                result = mid;
                start = mid + 1;
            }
        }

        System.out.println(result);

    }
}

```
