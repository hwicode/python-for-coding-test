```java
import java.util.*;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String s = scanner.nextLine();

        List<Character> characters = new ArrayList<>();
        int number = 0;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) - '0' <= 9) {
                number += s.charAt(i) - '0';
            } else {
                characters.add(s.charAt(i));
            }
        }

        Collections.sort(characters);

        for (Character character : characters) {
            System.out.print(character);
        }

        if (number != 0) {
            System.out.println(number);
        }
    }

}

```