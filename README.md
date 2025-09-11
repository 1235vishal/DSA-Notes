## String Manipulation

### Example 1: Reverse a String
```java
public class StringReversal {
    public static String reverse(String input) {
        return new StringBuilder(input).reverse().toString();
    }
}
```

### Example 2: Check for Palindrome
```java
public class PalindromeChecker {
    public static boolean isPalindrome(String input) {
        String reversed = new StringBuilder(input).reverse().toString();
        return input.equals(reversed);
    }
}
```

### Example 3: Count Vowels
```java
public class VowelCounter {
    public static int countVowels(String input) {
        int count = 0;
        for (char c : input.toCharArray()) {
            if ("AEIOUaeiou".indexOf(c) != -1) {
                count++;
            }
        }
        return count;
    }
}
```

### Example 4: Remove Spaces
```java
public class SpaceRemover {
    public static String removeSpaces(String input) {
        return input.replaceAll("\\s+", "");
    }
}
```

### Example 5: String to Integer Conversion
```java
public class StringToInteger {
    public static int stringToInt(String input) {
        return Integer.parseInt(input);
    }
}
```