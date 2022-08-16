```java
import java.util.Scanner;

public class Main {

    public static int[] parent = new int[100001];

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        for (int i = 1; i <= n; i++) {
            parent[i] = i;
        }

        for (int i = 0; i < m; i++) {
            int x = scanner.nextInt();
            int a = scanner.nextInt();
            int b = scanner.nextInt();

            switch(x) {
                case 0:
                    unionParent(a, b);
                    break;
                case 1:
                    if (findParent(a) == findParent(b)) {
                        System.out.println("YES");
                    } else {
                        System.out.println("NO");
                    }
                    break;
            }
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