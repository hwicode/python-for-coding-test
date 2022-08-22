```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String s = scanner.nextLine();

        int answer = s.length();
        for (int i = 1; i < s.length() / 2 + 1; i++) {
            String prev = s.substring(0, i);

            String result = "";
            int count = 1;
            for (int j = i; j < s.length(); j += i) {
                String now = "";
                for (int k = j; k < j + i; k++) {
                    if (k < s.length()) {
                        now += s.charAt(k);
                    }
                }

                if(prev.equals(now)) {
                    count++;
                } else {
                    result += count >= 2 ? count + prev : prev;
                    prev = now;
                    count = 1;
                }
            }

            result += count >= 2 ? count + prev : prev;
            answer = Math.min(answer, result.length());
        }

        System.out.println(answer);
    }

}

```