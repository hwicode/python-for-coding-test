```java
import java.util.*;

class Position {

    private final int x;
    private final int y;

    public Position(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() {
        return x;
    }

    public int getY() {
        return y;
    }
}

public class Main {

    public static int n, l, r;
    public static int[][] graph;
    public static int[][] unions;

    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, -1, 0, 1};

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        n = scanner.nextInt();
        l = scanner.nextInt();
        r = scanner.nextInt();

        graph = new int[n][n];
        unions = new int[n][n];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                graph[i][j] =scanner.nextInt();
            }
        }

        int totalCount = 0;
        while (true) {
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    unions[i][j] = -1;
                }
            }

            int index = 0;
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < n; j++) {
                    if (unions[i][j] == -1) {
                        process(i, j, index);
                        index++;
                    }
                }
            }

            if (index == n * n) {
                break;
            }
            totalCount++;
        }

        System.out.println(totalCount);
    }

    public static void process(int x, int y, int index) {
        List<Position> united = new ArrayList<>();
        united.add(new Position(x, y));

        Queue<Position> queue = new LinkedList<>();
        queue.offer(new Position(x, y));
        unions[x][y] = index;
        int summary = graph[x][y];
        int count = 1;

        while (!queue.isEmpty()) {
            Position position = queue.poll();
            x = position.getX();
            y = position.getY();
            for (int i = 0; i < 4; i++) {
                int nx = x + dx[i];
                int ny = y + dy[i];
                if (nx >= 0 && nx < n && ny >= 0 && ny < n && unions[nx][ny] == -1) {
                    int gap = Math.abs(graph[x][y] - graph[nx][ny]);
                    if (gap >= l && gap <= r) {
                        queue.offer(new Position(nx, ny));
                        unions[nx][ny] = index;
                        summary += graph[nx][ny];
                        count++;
                        united.add(new Position(nx, ny));
                    }
                }
            }
        }

        for (int i = 0; i < united.size(); i++) {
            x = united.get(i).getX();
            y = united.get(i).getY();
            graph[x][y] = summary / count;
        }
    }


}

```
