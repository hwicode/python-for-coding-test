```java
import java.util.Scanner;

public class Main {

    public static int[] parent;

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int g = scanner.nextInt();
        int p = scanner.nextInt();

        parent = new int[g + 1];
        for (int i = 1; i < g + 1; i++) {
            parent[i] = i;
        }

        int result = 0;
        for (int i = 0; i < p; i++) {
            int x = scanner.nextInt();
            int root = findParent(x);
            if (root == 0) {
                break;
            }
            unionParent(root, root - 1);
            result++;
        }

        System.out.println(result);
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
        if (x == parent[x]) {
            return x;
        }

        return parent[x] = findParent(parent[x]);
    }

}

```
