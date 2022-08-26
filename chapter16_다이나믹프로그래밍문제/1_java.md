```java
import java.util.Scanner;

public class Main {

    public static Scanner scanner = new Scanner(System.in);
    public static int[][] moves = {{-1, -1}, {0, -1}, {1, -1}};

    public static void main(String[] args) {

        int t = scanner.nextInt();
        
        for (int i = 0; i < t; i++) {
            System.out.println(dynamic());
        }
    }

    public static int dynamic() {
        int n = scanner.nextInt();
        int m = scanner.nextInt();

        int[][] map = new int[n + 2][m + 2];
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= m; j++) {
                map[i][j] = scanner.nextInt();
            }
        }

        int[][] dpTable = new int[n + 2][m + 2];
        for (int i = 1; i <= n; i++) {
            dpTable[i][1] = map[i][1];
        }

        for (int j = 2; j <= m; j++) {
            for (int i = 1; i <= n; i++) {
                for (int[] move : moves) {
                    int beforeX = i + move[0];
                    int beforeY = j + move[1];
                    dpTable[i][j] = Math.max(dpTable[i][j], dpTable[beforeX][beforeY] + map[i][j]);
                }
            }
        }

        int result = 0;
        for (int i = 1; i <= n; i++) {
            result = Math.max(result, dpTable[i][m]);
        }

        return result;
    }

}

```