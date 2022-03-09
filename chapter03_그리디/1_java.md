```java

import java.util.Scanner;

public class Main{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int money = scanner.nextInt();
        int count = 0;

        int[] coinTypes = {500, 100, 50, 10};
        for(int coin : coinTypes) {
            count += money / coin;
            money %= coin;
        }
        System.out.println(count);
    }
}

```
