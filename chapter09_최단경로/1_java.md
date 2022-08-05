```java
import java.util.Arrays;
import java.util.Scanner;

public class algorithm {

    public static final int INFINITY = (int) 1e9;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        int[][] graph = new int[n + 1][n + 1];
        for (int i = 0; i < n + 1; i++) {
           Arrays.fill(graph[i], INFINITY);
        }

        for (int a = 1; a < n + 1; a++) {
            for (int b = 1; b < n + 1; b++) {
                if (a == b) {
                    graph[a][b] = 0;
                }
            }
        }

        for (int i = 0; i < m; i++) {
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            graph[a][b] = 1;
            graph[b][a] = 1;
        }

        int x = scanner.nextInt();
        int k = scanner.nextInt();

        for (int c = 1; c < n + 1; c++) {
            for (int a = 1; a < n + 1; a++) {
                for (int b = 1; b < n + 1; b++) {
                    graph[a][b] = Math.min(graph[a][b], graph[a][c] + graph[c][b]);
                }
            }
        }

        int result = graph[1][k] + graph[k][x];

        if (result >= INFINITY) {
            System.out.println(-1);
        } else {
            System.out.println(result);
        }
    }

}

```
