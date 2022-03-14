```java
import java.util.Scanner;

public class algorithm {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int count = 0;
        for (int i = 0; i < n + 1; i++) {
            for (int j = 0; j < 60; j++) {
                for (int k = 0; k < 60; k++) {
                    String sum = String.valueOf(i) + String.valueOf(j) + String.valueOf(k);
                    if (sum.contains("3")) {
                        count++;
                    }
                }
            }
        }
        
        System.out.println(count);
        
    }
}
```
