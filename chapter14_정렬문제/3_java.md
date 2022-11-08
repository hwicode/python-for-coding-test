```java
import java.util.Arrays;

class Node implements Comparable<Node> {
    
    private int stage;
    private double fail;

    public Node(int stage, double fail) {
        this.stage = stage;
        this.fail = fail;
    }

    public int getStage() {
        return stage;
    }

    @Override
    public int compareTo(Node other) {
        if (this.fail == other.fail) {
            return Integer.compare(this.stage, other.stage);
        }
        return Double.compare(other.fail, this.fail);
    }
}


public class Main {

    public static void main(String[] args) {
        System.out.println(Arrays.toString(solution(4, new int[]{4, 4, 4, 4, 4})));
    }

    public static int[] solution(int n, int[] stages) {
        int[] array = new int[n + 2];

        for (int stage : stages) {
            array[stage]++;
        }

        int count = stages.length;

        Node[] nodes = new Node[n];
        for (int i = 0; i < n; i++) {
            int person = array[i + 1];
            nodes[i] = new Node(i + 1, person / (double) count);
            count -= person;
        }

        Arrays.sort(nodes);

        int[] result = new int[n];
        for (int i = 0; i < n; i++) {
            result[i] = nodes[i].getStage();
        }
        return result;
    }

}

```
