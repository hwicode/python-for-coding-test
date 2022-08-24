```java
import java.util.Scanner;

public class Main {

    public static int n, m;
    public static int[][] map;
    public static int[][] temp;
    public static int result = 0;

    public static int[] dx = {-1, 0, 1, 0};
    public static int[] dy = {0, 1, 0, -1};

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        n = scanner.nextInt();
        m = scanner.nextInt();

        map = new int[n][m];
        temp = new int[n][m];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                map[i][j] = scanner.nextInt();
            }
        }

        dfs(0);

        System.out.println(result);
    }

    public static void dfs(int count) {
        if (count == 3) {
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    temp[i][j] = map[i][j];
                }
            }

            for (int i = 0; i < n; i++) {
                for (int j = 0; j < m; j++) {
                    if (temp[i][j] == 2) {
                        virus(i, j);
                    }
                }
            }

            result = Math.max(result, getScore());
            return;
        }

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (map[i][j] == 0) {
                    map[i][j] = 1;
                    count++;
                    dfs(count);
                    map[i][j] = 0;
                    count--;
                }
            }
        }
    }

    public static void virus(int x, int y) {
        for (int i = 0; i < 4; i++) {
            int nx = x + dx[i];
            int ny = y + dy[i];

            if (nx >= 0 && nx < n && ny >= 0 && ny < m) {
                if (temp[nx][ny] == 0) {
                    temp[nx][ny] = 2;
                    virus(nx, ny);
                }
            }
        }
    }

    public static int getScore() {
        int score = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m ; j++) {
                if (temp[i][j] == 0) {
                    score++;
                }
            }
        }
        return score;
    }

}

```