```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String s = scanner.nextLine();

        System.out.println(solution(s));

    }

    public static String solution(String s) {
        String answer = "";
        if (s.equals("")) {
            return answer;
        }

        int index = balancedIndex(s);
        String u = s.substring(0, index + 1);
        String v = s.substring(index + 1);

        if (checkProper(u)) {
            answer = u + solution(v);
        } else {
            answer = "(";
            answer += solution(v);
            answer += ")";
            u = u.substring(1, u.length() - 1);
            String temp = "";
            for (int i = 0; i < u.length(); i++) {
                if (u.charAt(i) == '(') {
                    temp += ")";
                } else {
                    temp += "(";
                }
            }
            answer += temp;
        }
        return answer;
    }

    public static int balancedIndex(String s) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                count++;
            } else {
                count--;
            }
            if (count == 0) {
                return i;
            }
        }
        return -1;
    }

    public static boolean checkProper(String s) {
        int count = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) == '(') {
                count++;
            } else {
                if (count == 0) {
                    return false;
                }
                count--;
            }
        }
        return true;
    }

}
```