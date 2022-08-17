```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

class Edge implements Comparable<Edge> {

    private int nodeA;
    private int nodeB;
    private int cost;

    public Edge(int nodeA, int nodeB, int cost) {
        this.nodeA = nodeA;
        this.nodeB = nodeB;
        this.cost = cost;
    }

    public int getNodeA() {
        return nodeA;
    }

    public int getNodeB() {
        return nodeB;
    }

    public int getCost() {
        return cost;
    }

    @Override
    public int compareTo(Edge other) {
        if (cost < other.cost) {
            return -1;
        } else {
            return 1;
        }
    }
}

public class Main {

    public static int n, m;
    public static int[] parent = new int[100001];
    public static List<Edge> edges = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        n = scanner.nextInt();
        m = scanner.nextInt();

        for (int i = 1; i <= n; i++) {
            parent[i] = i;
        }

        for (int i = 0; i < m; i++) {
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            int cost = scanner.nextInt();

            edges.add(new Edge(a, b, cost));
        }

        Collections.sort(edges);

        int result = 0;
        int last = 0;
        for (Edge edge : edges) {
            int nodeA = edge.getNodeA();
            int nodeB = edge.getNodeB();
            int cost = edge.getCost();

            if (findParent(nodeA) != findParent(nodeB)) {
                result += cost;
                last = cost;
                unionParent(nodeA, nodeB);
            }
        }

        System.out.println(result - last);

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
        } else {
            return parent[x] = findParent(parent[x]);
        }
    }

}
```