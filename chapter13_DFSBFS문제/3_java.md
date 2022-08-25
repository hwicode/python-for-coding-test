```java
import java.util.*;

class Virus implements Comparable<Virus> {

    private int x;
    private int y;
    private int number;

    public Virus(int x, int y, int number) {
        this.x = x;
        this.y = y;
        this.number = number;
    }

    public int getX() {
        return x;
    }

    public int getY() {
        return y;
    }

    public int getNumber() {
        return number;
    }

    @Override
    public int compareTo(Virus other) {
        if (number < other.number) {
            return -1;
        } else {
            return 1;
        }
    }
}

public class Main {

    public static int n, k;
    public static int[][] graph;
    public static int s, x, y;

    public static Queue<Virus> queue = new PriorityQueue<>();
    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        n = scanner.nextInt();
        k = scanner.nextInt();

        graph = new int[n + 1][n + 1];
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n; j++) {
                graph[i][j] = scanner.nextInt();
            }
        }

        s = scanner.nextInt();
        x = scanner.nextInt();
        y = scanner.nextInt();

        bfs(s);

        System.out.println(graph[x][y]);
    }

    public static void bfs(int second) {
        for (int i = 0; i < second; i++) {
            checkVirus();
            while (!queue.isEmpty()) {
                Virus virus = queue.poll();
                spread(virus);
            }
        }
    }

    public static void checkVirus() {
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n; j++) {
                if (graph[i][j] != 0) {
                    queue.offer(new Virus(i, j, graph[i][j]));
                }
            }
        }
    }

    public static void spread(Virus virus) {
        for (int i = 0; i < 4; i++) {
            int nx = virus.getX() + dx[i];
            int ny = virus.getY() + dy[i];
            if (nx >= 1 && nx <= n && ny >= 1 && ny <= n) {
                if (graph[nx][ny] == 0) {
                    graph[nx][ny] = virus.getNumber();
                }
            }
        }
    }

}
```