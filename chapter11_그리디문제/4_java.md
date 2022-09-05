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

        int target = 1;
        for (int i = 0; i < n; i++) {
            if (target < array[i]) {
                break;
            }
            target += array[i];
        }

        System.out.println(target);
    }
    
}
```