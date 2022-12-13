```java
import java.util.Arrays;
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

class Node {
    private int x;
    private int y;
    private int distance;

    public Node(int x, int y) {
        this.x = x;
        this.y = y;
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

    public void setDistance(int distance) {
        this.distance = distance;
    }
}

public class Main {

    public static final int INF = (int) 1e9;
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};
    public static int[][] field;
    public static int size = 2;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();

        field = new int[n][n];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                field[i][j] = scanner.nextInt();
            }
        }

        int x = 0;
        int y = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (field[i][j] == 9) {
                    field[i][j] = 0;
                    x = i;
                    y = j;
                }
            }
        }

        int result = 0;
        int ate = 0;
        while (true) {
            Node node = find(bfs(n, x, y));

            if (node == null) {
                System.out.println(result);
                break;
            } else {
                x = node.getX();
                y = node.getY();
                result += node.getDistance();
                field[x][y] = 0;
                ate++;

                if (ate == size) {
                    size++;
                    ate = 0;
                }
            }
        }

    }

    public static int[][] bfs(int n, int x, int y) {
        int[][] dist = new int[n][n];
        for (int[] d : dist) {
            Arrays.fill(d, -1);
        }

        dist[x][y] = 0;

        Queue<Node> queue = new LinkedList<>();
        queue.offer(new Node(x, y));
        while (!queue.isEmpty()) {
            Node node = queue.poll();
            for (int i = 0; i < 4; i++) {
                x = node.getX();
                y = node.getY();
                int nx = x + dx[i];
                int ny = y + dy[i];
                if (nx >= 0 && nx < n && ny >= 0 && ny < n) {
                    if (dist[nx][ny] == -1 && field[nx][ny] <= size) {
                        dist[nx][ny] = dist[x][y] + 1;
                        queue.offer(new Node(nx, ny));
                    }
                }
            }
        }
        return dist;
    }

    public static Node find(int[][] dist) {
        int n = dist.length;
        int x = 0;
        int y = 0;
        int minDist = INF;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (dist[i][j] != -1 && 1 <= field[i][j] && field[i][j] < size) {
                    if (dist[i][j] < minDist) {
                        x = i;
                        y = j;
                        minDist = dist[i][j];
                    }
                }
            }
        }
        if (minDist == INF) {
            return null;
        } else {
            Node node = new Node(x, y);
            node.setDistance(minDist);
            return node;
        }
    }

}


```
