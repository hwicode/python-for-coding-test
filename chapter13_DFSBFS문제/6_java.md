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
        this.now = new int[r];
        this.result = new ArrayList<>();
    }

    public void combination(List<Position> list, int depth, int index, int target) {
        if (depth == r) {
            List<Position> temp = new ArrayList<>();
            for (int i = 0; i < now.length; i++) {
                temp.add(list.get(now[i]));
            }
            result.add(temp);
            return;
        }
        if (target == n) return;
        now[index] = target;
        combination(list, depth + 1, index + 1, target + 1);
        combination(list, depth, index, target + 1);
    }

    public List<List<Position>> getResult() {
        return result;
    }
}

class Position {
    private int x;
    private int y;

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

    public static int n;
    public static char[][] board = new char[6][6];
    public static List<Position> teachers = new ArrayList<>();
    public static List<Position> spaces = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        n = scanner.nextInt();

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                board[i][j] = scanner.next().charAt(0);
                if (board[i][j] == 'T') {
                    teachers.add(new Position(i, j));
                }

                if (board[i][j] == 'X') {
                    spaces.add(new Position(i, j));
                }
            }
        }

        Combination combination = new Combination(spaces.size(), 3);
        combination.combination(spaces, 0, 0, 0);
        List<List<Position>> spaceList = combination.getResult();

        boolean found = false;
        for (int i = 0; i < spaceList.size(); i++) {
            for (int j = 0; j < spaceList.get(i).size(); j++) {
                int x = spaceList.get(i).get(j).getX();
                int y = spaceList.get(i).get(j).getY();
                board[x][y] = 'O';
            }

            if (!process()) {
                found = true;
                break;
            }

            for (int j = 0; j < spaceList.get(i).size(); j++) {
                int x = spaceList.get(i).get(j).getX();
                int y = spaceList.get(i).get(j).getY();
                board[x][y] = 'X';
            }
        }

        if (found) {
            System.out.println("YES");
        } else {
            System.out.println("NO");
        }

    }

    public static boolean watch(int x, int y, int direction) {
        if (direction == 0) {
            while (y >= 0) {
                if (board[x][y] == 'S') {
                    return true;
                }

                if (board[x][y] == 'O') {
                    return false;
                }
                y--;
            }
        }

        if (direction == 1) {
            while (y < n) {
                if (board[x][y] == 'S') {
                    return true;
                }

                if (board[x][y] == 'O') {
                    return false;
                }
                y++;
            }
        }

        if (direction == 2) {
            while (x >= 0) {
                if (board[x][y] == 'S') {
                    return true;
                }

                if (board[x][y] == 'O') {
                    return false;
                }
                x--;
            }
        }

        if (direction == 3) {
            while (x < n) {
                if (board[x][y] == 'S') {
                    return true;
                }

                if (board[x][y] == 'O') {
                    return false;
                }
                x++;
            }
        }
        return false;
    }

    public static boolean process() {
        for (int i = 0; i < teachers.size(); i++) {
            int x = teachers.get(i).getX();
            int y = teachers.get(i).getY();
            for (int j = 0; j < 4; j++) {
                if (watch(x, y, j)) {
                    return true;
                }
            }
        }
        return false;
    }
}

```
