```java
import java.util.*;

public class Main {

    public static int n, m, k, x;
    public static int[] distance = new int[300001];
    public static List<List<Integer>> graph = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        n = scanner.nextInt();
        m = scanner.nextInt();
        k = scanner.nextInt();
        x = scanner.nextInt();

        for (int i = 0; i <= n; i++) {
            graph.add(new ArrayList<>());
            distance[i] = -1;
        }

        for (int i = 0; i < m; i++) {
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            graph.get(a).add(b);
        }

        bfs(x);
        
        int count = 0;
        for (int i = 1; i <= n; i++) {
            if (distance[i] == k) {
                System.out.println(i);
                count += 1;
            }
        }

        if (count == 0) {
            System.out.println(-1);
        }
    }

    public static void bfs(int x) {
        distance[x] = 0;
        Queue<Integer> queue = new LinkedList<>();
        queue.offer(x);

        while(!queue.isEmpty()) {
            int now = queue.poll();
            for (int i = 0; i < graph.get(now).size(); i++) {
                int nextNode = graph.get(now).get(i);
                if (distance[nextNode] == -1) {
                    distance[nextNode] = distance[now] + 1;
                    queue.offer(nextNode);
                }
            }
        }
    }

}

```