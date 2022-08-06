```java
import java.util.*;

class Node implements Comparable<Node> {
    private int index;
    private int distance;

    public Node(int index, int distance) {
        this.index = index;
        this.distance = distance;
    }

    public int getIndex() {
        return index;
    }

    public int getDistance() {
        return distance;
    }

    @Override
    public int compareTo(Node other) {
        if (this.distance < other.distance) {
            return -1;
        }
        return 1;
    }
}

public class algorithm {

    public static final int INFINITY = (int) 1e9;
    public static List<List<Node>> graph = new ArrayList<>();

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();
        int start = scanner.nextInt();

        for (int i = 0; i < n + 1; i++) {
            graph.add(new ArrayList<>());
        }

        for (int i = 0; i < m; i++) {
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            int z = scanner.nextInt();
            graph.get(x).add(new Node(y, z));
        }

        int[] d = new int[n + 1];

        Arrays.fill(d, INFINITY);

        dijkstra(d, start);

        int count = 0;
        int maxDistance = 0;
        for (int i = 1; i < n + 1; i++) {
            if (d[i] != INFINITY && d[i] != 0) {
                count++;
                maxDistance = Math.max(maxDistance, d[i]);
            }
        }

        System.out.println(count + " " + maxDistance);

    }

    public static void dijkstra(int[] d, int start) {
        Queue<Node> priorityQueue = new PriorityQueue<>();
        priorityQueue.offer(new Node(start, 0));
        d[start] = 0;

        while (!priorityQueue.isEmpty()) {
            Node node = priorityQueue.poll();

            int now = node.getIndex();
            int distance = node.getDistance();

            if (d[now] < distance) {
                continue;
            }

            for (int i = 0; i < graph.get(now).size(); i++) {
                int cost = d[now] + graph.get(now).get(i).getDistance();
                int index = graph.get(now).get(i).getIndex();

                if (cost < d[index]) {
                    d[index] = cost;
                    priorityQueue.offer(new Node(index, cost));
                }
            }

        }
    }

}

```
