```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int x = scanner.nextInt();

        int[] array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }

        int result = countByRange(array, x);

        if (result == 0) {
            System.out.println(-1);
        } else {
            System.out.println(result);
        }

    }

    public static int countByRange(int[] array, int x) {
        int leftIndex = lowerBound(array, x, 0, array.length);
        int rightIndex = upperBound(array, x, 0, array.length);

        return rightIndex - leftIndex;
    }

    public static int lowerBound(int[] array, int x, int start, int end) {
        while (start < end) {
            int mid = (start + end) / 2;
            if (array[mid] < x) {
                start = mid + 1;
            } else {
                end = mid;
            }
        }

        return end;
    }

    public static int upperBound(int[] array, int x, int start, int end) {
        while (start < end) {
            int mid = (start + end) / 2;
            if (array[mid] <= x) {
                start = mid + 1;
            } else {
                end = mid;
            }
        }

        return end;
    }

}
```