```java
import java.util.Scanner;

public class algorithm {

    private static int turnLeft(int d) {
        d++;
        if (d == 4) {
            d = 0;
        }
        return d;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        int m = scanner.nextInt();
        scanner.nextLine();

        int a = scanner.nextInt();
        int b = scanner.nextInt();
        int d = scanner.nextInt();
        scanner.nextLine();

        int[][] map = new int[n][m];
        for (int i = 0; i < n; i++) {
            int[] line = new int[m];
            for (int j = 0; j < m; j++) {
                line[j] = scanner.nextInt();
            }
            map[i] = line;
            scanner.nextLine();
        }


        int[][] steps = {{-1, 0}, {0, -1}, {1, 0}, {0, 1}};

        int answer = 1;

        while (true) {
            int turnNumber = 0;
            while (turnNumber != 4) {
                d = turnLeft(d);
                turnNumber++;
                int nextA = a + steps[d][0];
                int nextB = b + steps[d][1];
                if (map[nextA][nextB] == 0) {
                    map[a][b] = 1;
                    a = nextA;
                    b = nextB;
                    turnNumber = 0;
                    answer++;
                }
            }
            d = turnLeft(turnLeft(d));
            int nextA = a + steps[d][0];
            int nextB = b + steps[d][1];
            if (map[nextA][nextB] == 0) {
                map[a][b] = 1;
                a = nextA;
                b = nextB;
                answer++;
            } else {
                break;
            }
        }
        System.out.println(answer);
    }
}
```
