```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();

        int[] array = new int[n];
        for (int i = 0; i < n; i++) {
            array[i] = scanner.nextInt();
        }

        Arrays.sort(array);

        int result = 0;
        int count = 0;

        for (int i = 0; i < n; i++) {
            count += 1;
            if (count >= array[i]) {
                result += 1;
                count = 0;
            }
        }

        System.out.println(result);
    }

}

```