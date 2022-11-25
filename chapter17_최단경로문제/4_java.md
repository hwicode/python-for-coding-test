```java
import java.util.*;

public class Main {

    public static List<List<Integer>> graph = new ArrayList<>();
    public static int[] d;
    public static boolean[] visited;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int m = scanner.nextInt();

        d = new int[n + 1];
        visited = new boolean[n + 1];

        for (int i = 0; i < n + 1; i++) {
            graph.add(new ArrayList<>());
        }

        for (int i = 0; i < m; i++) {
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            graph.get(a).add(b);
            graph.get(b).add(a);
        }

        dijkstra(1);
        
        int distance = 0;
        for (int i = 1; i < n + 1; i++) {
            distance = Math.max(distance, d[i]);
        }
        int count = 0;
        for (int i = 1; i < n + 1; i++) {
            if (d[i] == distance) {
                count++;
            }
        }
        int number = 0;
        for (int i = 1; i < n + 1; i++) {
            if (d[i] == distance) {
                number = i;
                break;
            }
        }

        System.out.println(number + " " + distance + " " + count);
    }

    public static void dijkstra(int x) {
        Queue<Integer> queue = new LinkedList<>();
        queue.offer(x);
        visited[x] = true;

        while (!queue.isEmpty()) {
            x = queue.poll();
            for (int i : graph.get(x)) {
                if (!visited[i]) {
                    visited[i] = true;
                    d[i] = d[x] + 1;
                    queue.offer(i);
                }
            }
        }
    }

}

```
