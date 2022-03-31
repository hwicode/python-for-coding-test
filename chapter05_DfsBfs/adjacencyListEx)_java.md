```java
import java.util.ArrayList;
import java.util.List;

public class algorithm {

    static class Node {

        private int index;
        private int distance;

        public Node(int index, int distance) {
            this.index = index;
            this.distance = distance;
        }

        @Override
        public String toString() {
            return "(" +
                    index + ", " + distance +
                    ')';
        }
    }
    
    public static void main(String[] args) {
        
        List<List<Node>> graph = new ArrayList<>();
        // 그래프 초기화
        for(int i = 0; i < 3; i++) {
            graph.add(new ArrayList<Node>());
        }
        
        graph.get(0).add(new Node(1, 7));
        graph.get(0).add(new Node(2, 5));

        graph.get(1).add(new Node(0, 7));

        graph.get(2).add(new Node(0, 5));

        for(int i = 0; i < graph.size(); i++) {
            for(int j = 0; j < graph.get(i).size(); j++) {
                System.out.print(graph.get(i).get(j).toString() + " ");
            }
            System.out.println();
        }
    }
}
```
