```java
import java.util.Arrays;
import java.util.Scanner;

public class algorithm {

    public static int binarySearch(int[] array, int target, int start, int end) {

        if (start > end) {
            return -1;
        }

        int mid = (start + end) / 2;
        if (array[mid] == target) {
            return target;
        } else if (array[mid] > target) {
            return binarySearch(array, target, start, mid - 1);
        } else {
            return binarySearch(array, target, mid + 1, end);
        }

    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int[] array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }

        Arrays.sort(array);

        int m = scanner.nextInt();
        int[] targets = new int[m];
        for (int i = 0; i < m; i++) {
            targets[i] = scanner.nextInt();
        }

        for (int i = 0; i < m; i++) {
            int result = binarySearch(array, targets[i], 0, n - 1);
            if (result == -1) {
                System.out.printf("no ");
            } else {
                System.out.printf("yes ");
            }
        }

    }
}
```
