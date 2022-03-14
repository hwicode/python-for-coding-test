```java
import java.util.Scanner;

public class algorithm {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        scanner.nextLine();
        String[] m = scanner.nextLine().split(" ");
        
        int[] position = {1, 1};

        for(String d : m) {
            int x, y;
            if (d.equals("L")) {
                x = position[0];
                y = position[1] - 1;
            } else if(d.equals("R")) {
                x = position[0];
                y = position[1] + 1;
            } else if(d.equals("U")) {
                x = position[0] - 1;
                y = position[1];
            } else {
                x = position[0] + 1;
                y = position[1];
            }
            if (x > n || x < 1 || y > n || y < 1) {
                continue;
            } else {
                position[0] = x;
                position[1] = y;
            }
        }

        System.out.println(position[0] + " " + position[1]);
        
        }
}
```
