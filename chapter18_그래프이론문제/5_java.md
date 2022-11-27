```java
import java.util.*;

public class Main {

    public static int[] indegree = new int[501];
    public static boolean[][] graph = new boolean[501][501];

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int testCase = scanner.nextInt();

        for (int tc = 0; tc < testCase; tc++) {
            Arrays.fill(indegree, 0);
            for (int i = 0; i < 501; i++) {
                Arrays.fill(graph[i], false);
            }

            int n = scanner.nextInt();
            List<Integer> list = new ArrayList<>();
            for (int i = 0; i < n; i++) {
                int x = scanner.nextInt();
                list.add(x);
            }

            for (int i = 0; i < n; i++) {
                for (int j = i + 1; j < n; j++) {
                    graph[list.get(i)][list.get(j)] = true;
                    indegree[list.get(j)] += 1;
                }
            }

            int m = scanner.nextInt();
            for (int i = 0; i < m; i++) {
                int a = scanner.nextInt();
                int b = scanner.nextInt();
                if (graph[a][b]) {
                    graph[a][b] = false;
                    graph[b][a] = true;
                    indegree[a] += 1;
                    indegree[b] -= 1;
                } else {
                    graph[a][b] = true;
                    graph[b][a] = false;
                    indegree[a] -= 1;
                    indegree[b] += 1;
                }
            }

            List<Integer> result = new ArrayList<>();
            Queue<Integer> queue = new LinkedList<>();

            for (int i = 1; i <= list.size(); i++) {
                if (indegree[i] == 0) {
                    queue.offer(i);
                }
            }

            boolean certain = true;
            boolean cycle = false;

            for (int i = 0; i < n; i++) {
                if (queue.size() == 0) {
                    cycle = true;
                    break;
                }
                if (queue.size() >= 2) {
                    certain = false;
                    break;
                }
                int now = queue.poll();
                result.add(now);
                for (int j = 1; j <= n; j++) {
                    if (graph[now][j]) {
                        indegree[j] -= 1;
                        if (indegree[j] == 0) {
                            queue.offer(j);
                        }
                    }
                }
            }

            if (cycle) {
                System.out.println("IMPOSSIBLE");
            } else if (!certain) {
                System.out.println("?");
            } else {
                for (int i = 0; i < result.size(); i++) {
                    System.out.print(result.get(i) + " ");
                }
                System.out.println();
            }
        }
    }

}

```
