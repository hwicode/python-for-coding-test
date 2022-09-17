```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        int[] array = new int[m + 1];
        for (int i = 0; i < n; i++) {
            int index = scanner.nextInt();
            array[index]++;
        }

        int result = 0;
        int count = n;
        for (int i = 1; i < n; i++) {
            count -= array[i];
            if (count == 0) {
                break;
            }
            result += count * array[i];
        }

        System.out.println(result);
    }

}
```