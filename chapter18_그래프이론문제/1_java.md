```java
import java.util.Scanner;

public class Main {

    public static int[] parent = new int[501];

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        for (int i = 1; i <= n; i++) {
            parent[i] = i;
        }

        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= n; j++) {
                int x = scanner.nextInt();
                if (x == 1) {
                    unionParent(i, j);
                }
            }
        }

        int[] plans = new int[m];
        for (int i = 0; i < m; i++) {
            plans[i] = scanner.nextInt();
        }

        boolean answer = true;
        int parentPlan = findParent(plans[0]);
        for (int i = 1; i < m; i++) {
            if (findParent(i) != parentPlan) {
                answer = false;
                break;
            }
        }

        if (answer) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }
    }

    public static void unionParent(int a, int b) {
        a = findParent(a);
        b = findParent(b);

        if (a < b) {
            parent[b] = a;
        } else {
            parent[a] = b;
        }
    }

    public static int findParent(int x) {
        if (parent[x] == x) {
            return x;
        }

        return parent[x] = findParent(parent[x]);
    }

}
```