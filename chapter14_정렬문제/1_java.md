```java
import java.util.Arrays;
import java.util.Scanner;

class Student implements Comparable<Student> {

    private String name;
    private int korean;
    private int english;
    private int math;

    public Student(String name, int korean, int english, int math) {
        this.name = name;
        this.korean = korean;
        this.english = english;
        this.math = math;
    }

    public String getName() {
        return name;
    }

    @Override
    public int compareTo(Student other) {
        if (korean == other.korean && english == other.english && math == other.math) {
            return name.compareTo(other.name);
        }

        if (korean == other.korean && english == other.english) {
            return Integer.compare(other.math, math);
        }

        if (korean == other.korean) {
            return Integer.compare(english, other.english);
        }

        return Integer.compare(other.korean, korean);
    }
}

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int n = scanner.nextInt();


        Student[] array = new Student[n];
        for (int i = 0; i < n; i++) {
            String name = scanner.next();
            int korean = scanner.nextInt();
            int english = scanner.nextInt();
            int math = scanner.nextInt();
            array[i] = new Student(name, korean, english, math);
        }

        Arrays.sort(array);

        for (int i = 0; i < n; i++) {
            System.out.println(array[i].getName());
        }
    }

}

```