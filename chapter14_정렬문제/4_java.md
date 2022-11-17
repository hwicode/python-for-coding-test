```java
import java.util.PriorityQueue;
import java.util.Queue;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();

        Queue<Integer> queue = new PriorityQueue<>();
        for (int i = 0; i < n; i++) {
            queue.offer(scanner.nextInt());
        }

        int result = 0;
        while (queue.size() != 1) {
            int one = queue.poll();
            int two = queue.poll();

            int summary = one + two;
            result += summary;
            queue.offer(summary);
        }

        System.out.println(result);
    }

}

```
