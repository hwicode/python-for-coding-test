```java

import java.util.Scanner;

public class algorithm {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int m = scanner.nextInt();
    
        int count = 0;
        while (n != 1) {
            if (n % m == 0) {
                n = n / m;
                count++;
                continue;
            }
            n--;
            count++;
        }
        System.out.println(count);
        }
}

```
