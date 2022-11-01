```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

class Edge implements Comparable<Edge> {

    private int nodeA;
    private int nodeB;
    private int distance;

    public Edge(int nodeA, int nodeB, int distance) {
        this.nodeA = nodeA;
        this.nodeB = nodeB;
        this.distance = distance;
    }

    public int getNodeA() {
        return nodeA;
    }

    public int getNodeB() {
        return nodeB;
    }

    public int getDistance() {
        return distance;
    }

    @Override
    public int compareTo(Edge o) {
        if (this.distance < o.distance) {
            return -1;
        } else {
            return 1;
        }
    }
}

public class Main {

    public static int[] parent;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        parent = new int[n];
        for (int i = 1; i < n; i++) {
            parent[i] = i;
        }

        List<Edge> edges = new ArrayList<>();
        for (int i = 0; i < m; i++) {
            int x = scanner.nextInt();
            int y = scanner.nextInt();
            int distance = scanner.nextInt();
            edges.add(new Edge(x, y, distance));
        }

        Collections.sort(edges);

        int result = 0;
        for (Edge edge : edges) {
            int nodeA = edge.getNodeA();
            int nodeB = edge.getNodeB();
            int distance = edge.getDistance();
            if (findParent(nodeA) != findParent(nodeB)) {
                unionParent(nodeA, nodeB);
            } else {
                result += distance;
            }
        }

        System.out.println(result);
    }

    public static void unionParent(int a, int b) {
        a = findParent(a);
        b = findParent(b);

        if (a < b) {
            parent[b] = a;
        } else {
            parent[a] = b;
        }
    }

    public static int findParent(int x) {
        if (x == parent[x]) {
            return x;
        }

        return parent[x] = findParent(parent[x]);
    }

}

```
