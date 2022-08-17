```java
import java.util.*;

public class Main {

    public static int n;
    public static int[] times = new int[501];
    public static int[] indegree = new int[501];
    public static List<List<Integer>> graph = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        n = scanner.nextInt();

        for (int i = 0; i <= n; i++) {
            graph.add(new ArrayList<>());
        }

        for (int i = 1; i <= n; i++) {
            times[i] = scanner.nextInt();

            int x = scanner.nextInt();
            while (x != -1) {
                graph.get(x).add(i);
                indegree[i] ++;
                x = scanner.nextInt();
            }
        }

        int[] results = topologySort();

        for (int i = 1; i <= n; i++) {
            System.out.println(results[i]);
        }
    }

    public static int[] topologySort() {
        int[] results = new int[n + 1];
        for (int i = 1; i <= n; i++) {
            results[i] = times[i];
        }

        Queue<Integer> queue = new LinkedList<>();
        for (int i = 1; i <= n; i++) {
            if (indegree[i] == 0) {
                queue.offer(i);
            }
        }

        while (!queue.isEmpty()) {
            int now = queue.poll();
            List<Integer> adjacencyList = graph.get(now);
            for (int i : adjacencyList) {
                results[i] = Math.max(results[i], results[now] + times[i]);
                indegree[i] -= 1;
                if (indegree[i] == 0) {
                    queue.add(i);
                }
            }
        }

        return results;
    }

}
```