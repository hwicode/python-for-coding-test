```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int c = scanner.nextInt();

        List<Integer> list = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            list.add(scanner.nextInt());
        }

        Collections.sort(list);

        int start = 1;
        int end = list.get(n - 1) - list.get(0);
        int result = 0;

        while (start <= end) {
            int mid = (start + end) / 2;
            int value = list.get(0);
            int count = 1;
            for (int i = 1; i < n; i++) {
                if (list.get(i) >= value + mid) {
                    value = list.get(i);
                    count++;
                }
            }

            if (count >= c) {
                start = mid + 1;
                result = mid;
            } else {
                end = mid - 1;
            }
        }

        System.out.println(result);
    }

}

```
