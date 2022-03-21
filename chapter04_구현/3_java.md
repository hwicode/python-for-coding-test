```java
import java.util.Scanner;

public class algorithm {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String n = scanner.nextLine();

        int first = (int) n.charAt(0) - 96;
        int second = Character.getNumericValue(n.charAt(1));
        int[][] steps = {{2, 1}, {2, -1}, {-2, 1}, {-2, -1}, {1, 2}, {1, -2}, {-1, 2}, {-1, -2}};

        int count = 0;
        for (int[] step : steps) {
            int length = step[0] + second;
            int width = step[1] + first;
            if (length > 0 && length < 9 && width > 0 && width < 9) {
                count++;
            }
        }

        System.out.println(count);
    }
}
```
