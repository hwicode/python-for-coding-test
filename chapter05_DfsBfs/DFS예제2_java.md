```java
public class algorithm {

    public static boolean[] visited = new boolean[9];
    public static int[][] graph = new int[9][];

    public static void dfs(int x) {
        visited[x] = true;
        System.out.print(x + " ");

        for (int i = 0; i < graph[x].length; i++) {
            int y = graph[x][i];
            if (visited[y] == false) {
                dfs(y);
            }
        }
    }

    public static void main(String[] args) {
        graph[1] = new int[]{2, 3, 8};
        graph[2] = new int[]{1, 7};
        graph[3] = new int[]{1, 4, 5};
        graph[4] = new int[]{3, 5};
        graph[5] = new int[]{3, 4};
        graph[6] = new int[]{7};
        graph[7] = new int[]{2, 6, 8};
        graph[8] = new int[]{1, 7};

        dfs(1);
    }
}
```
