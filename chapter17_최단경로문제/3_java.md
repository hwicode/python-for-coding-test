```java
import java.util.Arrays;
import java.util.PriorityQueue;
import java.util.Queue;
import java.util.Scanner;

class Node implements Comparable<Node> {

    private int x;
    private int y;
    private int distance;

    public Node(int x, int y, int distance) {
        this.x = x;
        this.y = y;
        this.distance = distance;
    }

    public int getX() {
        return x;
    }

    public int getY() {
        return y;
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

public class Main {

    public static final int INF = (int) 1e9;
    public static int[][] graph = new int[125][125];
    public static int[][] d = new int[125][125];
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int t = scanner.nextInt();

        for (int testCase = 0; testCase < t; testCase++) {
            int n = scanner.nextInt();

            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    graph[i][j] = scanner.nextInt();
                }
            }

            for (int i = 0; i < n; i++) {
                Arrays.fill(d[i], INF);
            }

            int x = 0, y = 0;
            Queue<Node> queue = new PriorityQueue<>();
            queue.offer(new Node(0, 0, graph[x][y]));

            while(!queue.isEmpty()) {
                Node node = queue.poll();
                int distance = node.getDistance();
                x = node.getX();
                y = node.getY();

                if (d[x][y] < distance) {
                    continue;
                }

                for (int i = 0; i < 4; i++) {
                    int nx = x + dx[i];
                    int ny = y + dy[i];
                    if (nx < 0 || nx >= n || ny < 0 || ny >= n) {
                        continue;
                    }
                    int cost = distance + graph[nx][ny];
                    if (cost < d[nx][ny]) {
                        d[nx][ny] = cost;
                        queue.offer(new Node(nx, ny, cost));
                    }
                }
            }
            System.out.println(d[n - 1][n - 1]);
        }
    }

}

```
