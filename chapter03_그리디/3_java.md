```java

import java.util.Scanner;

public class algorithm {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int m = scanner.nextInt();
        scanner.nextLine();

        int answer = 0;
        for (int i = 0; i < n; i++) {
            int minValue = 2_147_483_647;
            for(int j = 0; j < m; j++) {
                int inputValue = scanner.nextInt();
                minValue = Math.min(minValue, inputValue);
            }
            answer = Math.max(answer, minValue);
        }
        System.out.println(answer);
    }
}

```
