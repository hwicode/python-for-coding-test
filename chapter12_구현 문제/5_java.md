```java
import java.util.*;

class Node {

    private int time;
    private char direction;

    public Node(int time, char direction) {
        this.time = time;
        this.direction = direction;
    }

    public int getTime() {
        return this.time;
    }

    public char getDirection() {
        return this.direction;
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
        return this.x;
    }

    public int getY() {
        return this.y;
    }
}

public class Main {

    public static int n, k, l;
    public static int[][] map = new int[101][101];
    public static List<Node> information = new ArrayList<>(); 
    
    public static int dx[] = {0, 1, 0, -1};
    public static int dy[] = {1, 0, -1, 0};

    public static int turn(int direction, char c) {
        if (c == 'L') direction = (direction == 0) ? 3 : direction - 1;
        else direction = (direction + 1) % 4;
        return direction;
    }

    public static int simulate() {
        int x = 1, y = 1;
        map[x][y] = 2; 
        int direction = 0;
        int time = 0;
        int index = 0; // 다음에 회전할 정보
        
        Queue<Position> q = new LinkedList<>();
        q.offer(new Position(x, y));

        while (true) {
            int nx = x + dx[direction];
            int ny = y + dy[direction];
            
            if (1 <= nx && nx <= n && 1 <= ny && ny <= n && map[nx][ny] != 2) {
                
                if (map[nx][ny] == 0) {
                    map[nx][ny] = 2;
                    q.offer(new Position(nx, ny));
                    Position prev = q.poll();
                    map[prev.getX()][prev.getY()] = 0;
                }
                
                if (map[nx][ny] == 1) {
                    map[nx][ny] = 2;
                    q.offer(new Position(nx, ny));
                }
            }
           
            else {
                time += 1;
                break;
            }
           
            x = nx;
            y = ny;
            time += 1;
            if (index < l && time == information.get(index).getTime()) { 
                direction = turn(direction, information.get(index).getDirection());
                index += 1;
            }
        }
        return time;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        n = sc.nextInt();
        k = sc.nextInt();

        for (int i = 0; i < k; i++) {
            int a = sc.nextInt();
            int b = sc.nextInt();
            map[a][b] = 1;
        }

        l = sc.nextInt();
        for (int i = 0; i < l; i++) {
            int x = sc.nextInt();
            char c = sc.next().charAt(0);
            information.add(new Node(x, c));
        }

        System.out.println(simulate());
    }

}```