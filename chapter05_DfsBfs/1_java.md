```java
import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class algorithm {

    public static int[][] graph;
    public static int count;

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

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                bfs(new int[]{i, j}, n, m);
            }
        }

        System.out.println(count);
    }

    public static void bfs(int[] start, int n, int m) {
        int[][] move = {{0, 0}, {0, 1}, {1, 0}, {1, 1}};
        if(graph[start[0]][start[1]] == 1) {
            return;
        }
        graph[start[0]][start[1]] = 1;
        count++;
        Queue<int[]> queue = new LinkedList<>();
        queue.offer(start);
        while(!queue.isEmpty()) {
            int[] v = queue.poll();
            for(int i = 0; i < move.length; i++) {
                int nextX = v[0] + move[i][0];
                int nextY = v[1] + move[i][1];
                if (nextX >= 0 && nextX < n && nextY >= 0 && nextY < m && graph[nextX][nextY] == 0) {
                    graph[nextX][nextY] = 1;
                    queue.offer(new int[]{nextX, nextY});
                }
            }
        }
    }
}

```
