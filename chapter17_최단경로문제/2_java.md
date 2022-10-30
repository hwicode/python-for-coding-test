```java
import java.util.Arrays;
import java.util.Scanner;

public class Main {

    public static final int INF = (int) 1e9;

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        int[][] graph = new int[n + 1][n + 1];
        for (int i = 1; i <= n; i++) {
            Arrays.fill(graph[i], INF);
        }

        for (int a = 1; a <= n; a++) {
            for (int b = 1; b <= n; b++) {
                if (a == b) graph[a][b] = 0;
            }
        }

        for (int i = 0; i < m; i++) {
            int a = scanner.nextInt();
            int b = scanner.nextInt();
            graph[a][b] = 1;
        }

        for (int k = 1; k <= n; k++) {
            for (int a = 1; a <= n; a++) {
                for (int b = 1; b <= n; b++) {
                    graph[a][b] = Math.min(graph[a][b], graph[a][k] + graph[k][b]);
                }
            }
        }

        int result = 0;
        for (int i = 1; i <= n; i++) {
            int count = 0;
            for (int j = 1; j <= n; j++) {
                if (graph[i][j] != INF || graph[j][i] != INF) {
                    count++;
                }
            }
            if (count == n) {
                result++;
            }
        }

        System.out.println(result);
    }

}

```
