```java
public class algorithm {

    public static int factorialIterative(int number) {
        int result = 1;
        for(int i = 1; i < number + 1; i++) {
            result *= i;
        }
        return result;
    }

    public static int factorialRecursive(int number) {
        if (number <= 1) {
            return 1;
        }
        return number * factorialIterative(number - 1);
    }

    public static void main(String[] args) {
        System.out.println("반복적으로 구현 : " + factorialIterative(5));
        System.out.println("재귀적으로 구현 : " + factorialRecursive(5));
    }
}

```
