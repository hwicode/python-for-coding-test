```java
import java.util.LinkedList;
import java.util.Queue;

public class algorithm {

    public static boolean[] visited = new boolean[9];
    public static int[][] graph = new int[9][];

    public static void bfs(int start) {
        Queue<Integer> q = new LinkedList<>();
        q.offer(start);
        // 현재 노드 방문 처리
        visited[start] = true;
        //큐가 빌 때까지 반복
        while(!q.isEmpty()) {
            // 큐에서 하나의 원소를 뽑아 출력
            int x = q.poll();
            System.out.print(x + " ");
            // 해당 원소와 연결된, 아직 방문하지 않은 원소들을 큐에 삽입
            for (int i = 0; i < graph[x].length; i++) {
                int y = graph[x][i];
                if (visited[y] == false) {
                    q.offer(y);
                    visited[y] = true;
                }
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

        bfs(1);
    }
}
```
