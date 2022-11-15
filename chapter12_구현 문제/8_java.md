```java
import java.util.ArrayList;
import java.util.List;

class Permutation {

    private int n;
    private int r;
    private int[] now;
    private List<List<Integer>> result;

    public Permutation(int n, int r) {
        this.n = n;
        this.r = r;
        this.now = new int[r];
        this.result = new ArrayList<>();
    }

    public List<List<Integer>> getResult() {
        return result;
    }

    public void permutation(int[] array, int depth) {
        if (depth == r) {
            List<Integer> temp = new ArrayList<>();
            for (int i = 0; i < now.length; i++) {
                temp.add(now[i]);
            }
            result.add(temp);
            return;
        }
        for (int i = depth; i < n; i++) {
            swap(array, i, depth);
            now[depth] = array[depth];
            permutation(array, depth + 1);
            swap(array, i, depth);
        }
    }

    private void swap(int[] array, int i, int j) {
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }
}

public class Main {

    public static void main(String[] args) {
        System.out.println(solution(12, new int[]{1, 5, 6, 10}, new int[]{1, 2, 3, 4}));
    }

    public static int solution(int n, int[] weak, int[] dist) {
        List<Integer> weakList = new ArrayList<>();
        for (int i = 0; i < weak.length; i++) {
            weakList.add(weak[i]);
        }
        for (int i = 0; i < weak.length; i++) {
            weakList.add(weak[i] + n);
        }

        int answer = dist.length + 1;
        Permutation perm = new Permutation(dist.length, dist.length);
        perm.permutation(dist, 0);
        List<List<Integer>> distList = perm.getResult();

        for (int start = 0; start < weak.length; start++) {
            for (int i = 0; i < distList.size(); i++) {
                int count = 1;
                int position = weakList.get(start) + distList.get(i).get(count - 1);
                for (int index = start; index < start + weak.length; index++) {
                    if (position < weakList.get(index)) {
                        count++;
                        if (count > dist.length) {
                            break;
                        }
                        position = weakList.get(index) + distList.get(i).get(count - 1);
                    }
                }
                answer = Math.min(answer, count);
            }
        }
        if (answer > dist.length) {
            return -1;
        }
        return answer;
    }

}

```
