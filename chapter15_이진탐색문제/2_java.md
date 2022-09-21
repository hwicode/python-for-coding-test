```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }

        int result = -1;
        int start = 0;
        int end = n - 1;
        int mid;
        while (start <= end) {

            mid = (start + end) / 2;

            if (array[mid] == mid) {
                result = mid;
                break;
            }

            if (array[mid] > mid) {
                end = mid - 1;
                continue;
            }

            if (array[mid] < mid) {
                start = mid + 1;
            }
        }

        System.out.println(result);
    }

}
```