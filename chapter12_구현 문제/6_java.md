```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

class Node implements Comparable<Node> {

    private int x;
    private int y;
    private int stuff;

    public Node(int x, int y, int stuff) {
        this.x = x;
        this.y = y;
        this.stuff = stuff;
    }

    public int getX() {
        return x;
    }

    public int getY() {
        return y;
    }

    public int getStuff() {
        return stuff;
    }

    @Override
    public int compareTo(Node other) {
        if (this.x == other.x && this.y == other.y) {
            return Integer.compare(this.stuff, other.stuff);
        }
        if (this.x == other.x) {
            return Integer.compare(this.y, other.y);
        }
        return Integer.compare(this.x, other.x);
    }
}

public class Main {

    public int[][] solution(int n, int[][] buildFrame) {
        List<List<Integer>> answer = new ArrayList<>();
        for (int i = 0; i < buildFrame.length; i++) {
            int x = buildFrame[i][0];
            int y = buildFrame[i][1];
            int stuff = buildFrame[i][2];
            int operate = buildFrame[i][3];

            if (operate == 0) {
                int index = 0;
                for (int j = 0; j < answer.size(); j++) {
                    if (x == answer.get(j).get(0) && y == answer.get(j).get(1) && stuff == answer.get(j).get(2)) {
                        index = j;
                        break;
                    }
                }
                List<Integer> erased = answer.get(index);
                answer.remove(index);
                if (!possible(answer)) {
                    answer.add(erased);
                }
            }
            
            if (operate == 1) {
                List<Integer> inserted = new ArrayList<>();
                inserted.add(x);
                inserted.add(y);
                inserted.add(stuff);
                answer.add(inserted);
                if (!possible(answer)) {
                    answer.remove(answer.size() - 1);
                }
            }
        }

        List<Node> nodes = new ArrayList<>();
        for (int i = 0; i < answer.size(); i++) {
            int x = answer.get(i).get(0);
            int y = answer.get(i).get(1);
            int stuff = answer.get(i).get(2);
            nodes.add(new Node(x, y, stuff));
        }

        Collections.sort(nodes);
        
        int[][] result = new int[nodes.size()][3];
        for (int i = 0; i < nodes.size(); i++) {
            result[i][0] = nodes.get(i).getX();
            result[i][1] = nodes.get(i).getY();
            result[i][2] = nodes.get(i).getStuff();
        }
        return result;
    }

    public boolean possible(List<List<Integer>> answer) {
        for (int i = 0; i < answer.size(); i++) {
            int x = answer.get(i).get(0);
            int y = answer.get(i).get(1);
            int stuff = answer.get(i).get(2);

            if (stuff == 0) {
                boolean check = false;

                if (y == 0) {
                    check = true;
                }

                for (int j = 0; j < answer.size(); j++) {
                    if (x - 1 == answer.get(j).get(0) && y == answer.get(j).get(1) && 1 == answer.get(j).get(2)) {
                        check = true;
                    }

                    if (x == answer.get(j).get(0) && y == answer.get(j).get(1) && 1 == answer.get(j).get(2)) {
                        check = true;
                    }

                    if (x == answer.get(j).get(0) && y - 1 == answer.get(j).get(1) && 0 == answer.get(j).get(2)) {
                        check = true;
                    }
                }
                if (!check) {
                    return false;
                }
            } else if (stuff == 1) {
                boolean check = false;
                boolean left = false;
                boolean right = false;
                for (int j = 0; j < answer.size(); j++) {

                    if (x == answer.get(j).get(0) && y - 1 == answer.get(j).get(1) && 0 == answer.get(j).get(2)) {
                        check = true;
                    }
                    
                    if (x + 1 == answer.get(j).get(0) && y - 1 == answer.get(j).get(1) && 0 == answer.get(j).get(2)) {
                        check = true;
                    }

                    if (x - 1 == answer.get(j).get(0) && y == answer.get(j).get(1) && 1 == answer.get(j).get(2)) {
                        left = true;
                    }
                    
                    if (x + 1 == answer.get(j).get(0) && y == answer.get(j).get(1) && 1 == answer.get(j).get(2)) {
                        right = true;
                    }
                }
                if (left && right) {
                    check = true;
                }
                
                if (!check) {
                    return false;
                }
            }
        }
        return true;
    }

}
```