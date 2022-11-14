```java
import java.util.*;

class Food implements Comparable<Food> {

    private int index;
    private int time;

    public Food(int index, int time) {
        this.index = index;
        this.time = time;
    }

    public int getIndex() {
        return index;
    }

    public int getTime() {
        return time;
    }

    @Override
    public int compareTo(Food other) {
        return Integer.compare(this.time, other.time);
    }

}

public class Main {

    public static void main(String[] args) {
        System.out.println(solution(new int[]{3, 1, 2}, 5));
    }

    public static int solution(int[] foodTimes, int k) {
        long summary = 0;
        for (int foodTime : foodTimes) {
            summary += foodTime;
        }

        if (summary <= k) {
            return -1;
        }

        Queue<Food> priorityQueue = new PriorityQueue<>();
        for (int i = 0; i < foodTimes.length; i++) {
            priorityQueue.offer(new Food(i + 1, foodTimes[i]));
        }

        summary = 0;
        long previous = 0;
        long length = foodTimes.length;

        while ((summary + (priorityQueue.peek().getTime() - previous) * length) <= k) {
            int now = priorityQueue.poll().getTime();
            summary += (now - previous) * length;
            length--;
            previous = now;
        }

        List<Food> result = new ArrayList<>();
        while (!priorityQueue.isEmpty()) {
            result.add(priorityQueue.poll());
        }

        Collections.sort(result, Comparator.comparingInt(Food::getIndex));

        return result.get((int) ((k - summary) % length)).getIndex();
    }

}

```
