```java
import java.util.Arrays;
import java.util.Scanner;

public class algorithm {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int m = scanner.nextInt();
        int k = scanner.nextInt();

        int[] numbers = new int[n];
        for(int i = 0; i < n; i++) {
            numbers[i] = scanner.nextInt();
        }
        Arrays.sort(numbers);
        int sum = numbers[n - 1] * k + numbers[n - 2];
        int answer = sum * (m / (k + 1)) + numbers[n - 1] * (m % (k + 1));
        System.out.println(answer);
    }
}
```
