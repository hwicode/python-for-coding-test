```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class algorithm {

    public static int[][] graph;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int m = scanner.nextInt();
        scanner.nextLine();

        graph = new int[n][m];
        for (int i = 0; i < n; i++) {
            String str = scanner.nextLine();
            for (int j = 0; j < m; j++) {
                graph[i][j] = str.charAt(j) - '0';
            }
        }

        bfs(n, m);
        System.out.println(graph[n - 1][m - 1]);
    }

    public static void bfs(int n, int m) {
        int[][] move = {{-1, 0}, {1, 0}, {0, 1}, {0, -1}};
        Queue<int[]> queue = new LinkedList<>();
        queue.offer(new int[]{0, 0});

        while(!queue.isEmpty()) {
            int[] step = queue.poll();
            for (int i = 0; i < move.length; i++) {
                int nextX = step[0] + move[i][0];
                int nextY = step[1] + move[i][1];
                if (nextX >= 0 && nextX < n && nextY >= 0 && nextY < m && graph[nextX][nextY] == 1) {
                    queue.offer(new int[]{nextX, nextY});
                    graph[nextX][nextY] = graph[step[0]][step[1]] + 1;
                }
            }
        }
    }
}

```
