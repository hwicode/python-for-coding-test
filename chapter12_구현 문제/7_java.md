```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Combination {

    private int n;
    private int r;
    private int[] now;
    private List<List<Position>> result;

    public Combination(int n, int r) {
        this.n = n;
        this.r = r;
        now = new int[r];
        result = new ArrayList<>();
    }

    public List<List<Position>> getResult() {
        return result;
    }

    public void combination(List<Position> positions, int depth, int index, int target) {
        if (depth == r) {
            List<Position> temp = new ArrayList<>();
            for (int i = 0; i < now.length; i++) {
                temp.add(positions.get(now[i]));
            }
            result.add(temp);
            return;
        }

        if (target == n) return;
        now[index] = target;
        combination(positions, depth + 1, index + 1, target + 1);
        combination(positions, depth, index, target + 1);
    }
}

class Position {
    private final int x;
    private final int y;

    public Position(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() {
        return x;
    }

    public int getY() {
        return y;
    }
}

public class Main {

    public static List<Position> houses = new ArrayList<>();
    public static List<Position> chickens = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();
        int m = scanner.nextInt();

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                int input = scanner.nextInt();
                if (input == 1) houses.add(new Position(i, j));
                if (input == 2) chickens.add(new Position(i, j));
            }
        }

        Combination combination = new Combination(chickens.size(), m);
        combination.combination(chickens, 0, 0, 0);
        List<List<Position>> chickenList = combination.getResult();

        int result = (int) 1e9;
        for (int i = 0; i < chickenList.size(); i++) {
            result = Math.min(result, getSum(chickenList.get(i)));
        }

        System.out.println(result);
    }

    public static int getSum(List<Position> candidates) {
        int result = 0;
        for (int i = 0; i < houses.size(); i++) {
            int hx = houses.get(i).getX();
            int hy = houses.get(i).getY();
            int temp = (int) 1e9;
            for (int j = 0; j < candidates.size(); j++) {
                int cx = candidates.get(j).getX();
                int cy = candidates.get(j).getY();
                temp = Math.min(temp, Math.abs(hx - cx) + Math.abs(hy - cy));
            }
            result += temp;
        }
        return result;
    }
}

```
