```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;

public class Main {

    public static List<List<String>> array = new ArrayList<>();
    public static List<List<String>> reversedArray = new ArrayList<>();

    public static void main(String[] args) {
        int[] solution = solution(new String[]{"frodo", "front", "frost", "frozen", "frame", "kakao"}, new String[]{"fro??", "????o", "fr???", "fro???", "pro?"});
        for (int s : solution) {
            System.out.print(s + " ");
        }
    }

    public static int[] solution(String[] words, String[] queries) {
        List<Integer> answer = new ArrayList<>();

        for (int i = 0; i < 10001; i++) {
            array.add(new ArrayList<>());
            reversedArray.add(new ArrayList<>());
        }

        for (int i = 0; i < words.length; i++) {
            String word = words[i];
            array.get(word.length()).add(word);
            word = (new StringBuffer(word)).reverse().toString();
            reversedArray.get(word.length()).add(word);
        }

        for (int i = 0; i < 10001; i++) {
            Collections.sort(array.get(i));
            Collections.sort(reversedArray.get(i));
        }

        for (int i = 0; i < queries.length; i++) {
            String query = queries[i];
            int res = 0;
            if (query.charAt(0) != '?') {
                res = countByRange(array.get(query.length()), query.replaceAll("\\?", "a"), query.replaceAll("\\?", "z"));
            } else {
                query = (new StringBuffer(query)).reverse().toString();
                res = countByRange(reversedArray.get(query.length()), query.replaceAll("\\?", "a"), query.replaceAll("\\?", "z"));
            }
            answer.add(res);
        }

        int[] result = new int[answer.size()];
        for (int i = 0; i < answer.size(); i++) {
            result[i] = answer.get(i);
        }
        return result;
    }

    public static int countByRange(List<String> array, String leftValue, String rightValue) {
        int rightIndex = upperBound(array, rightValue, 0, array.size());
        int leftIndex = lowerBound(array, leftValue, 0, array.size());
        return rightIndex - leftIndex;
    }

    public static int upperBound(List<String> array, String target, int start, int end) {
        while (start < end) {
            int mid = (start + end) / 2;
            if (array.get(mid).compareTo(target) > 0) {
                end = mid;
            } else {
                start = mid + 1;
            }
        }
        return end;
    }

    public static int lowerBound(List<String> array, String target, int start, int end) {
        while (start < end) {
            int mid = (start + end) / 2;
            if (array.get(mid).compareTo(target) >= 0) {
                end = mid;
            } else {
                start = mid + 1;
            }
        }
        return end;
    }

}

```
