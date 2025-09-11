# 📘 Vishal's DSA Notes

Welcome to my **DSA Learning Notes**.  
This repo is just **one README.md file** where I write all my important DSA concepts, shortcuts, and code snippets.  
So I can open this repo anytime and revise everything quickly 🚀.

## 🔹 Roadmap
1. Arrays ✅
2. Recursion ✅
3. Divide and Conquer ✅
4. Sorting Algorithms ✅
5. 2D Arrays ✅
6. Strings ✅


---


# 📚 Arrays

## 1. Get Largest Element in Array

```java
public static int getLargest(int Numbers[]) {
   int largest = Integer.MIN_VALUE; // -Infinity
   for(int i = 0; i < Numbers.length; i++) {
     if(largest < Numbers[i]) {
       largest = Numbers[i];
     }
   }
   return largest;
}
```

## 2. Get Smallest Element in Array
```java
public static int getSmallest(int Numbers[]) {
  int smallest = Integer.MAX_VALUE; // +Infinity
  for(int i = 0; i < Numbers.length; i++) {
    if(smallest > Numbers[i]) {
      smallest = Numbers[i];
    }
  }
  return smallest;
}
```

## 3. Linear Search
```java
public static int LinearSearch(int Numbers[], int key) {
  for(int i = 0; i < Numbers.length; i++) {
    if(Numbers[i] == key) {
      return i;
    }
  }
  return -1;
}
```

## 4. Binary Search (Array must be sorted)
```java
public static int BinearySearch(int Numbers[], int key) {
  int start = 0; int end = Numbers.length - 1;
  while(start <= end) {
    int mid = (start + end)/2;
    if(Numbers[mid] == key) { // found
      return mid;
    } 
    if(Numbers[mid] < key) { // right side
      start = mid + 1;
    }
    else { // left side
      end = mid - 1;
    }
  }
  return -1;
}
```

## 5. Reverse Array
```java
public static void Reverse(int Numbers[]) {
  int first = 0; int last = Numbers.length - 1;
  while(first < last) {
    int temp = Numbers[last];
    Numbers[last] = Numbers[first];
    Numbers[first] = temp;
    first++;
    last--;
  }
}
```

## 6. Print All Pairs in Array
```java
public static void PairsofNum(int Numbers[]) {
  int tp = 0;
  for(int i = 0; i < Numbers.length; i++) {
    int current = Numbers[i];
    for(int j = i + 1; j < Numbers.length; j++) {
      System.out.print("(" + current + "," + Numbers[j] + ")");
      tp++;
    }
  }
  System.out.println();
  System.out.println("Total pairs is : " + tp);

  /*
  total pairs formula 
  total pairs = n(n-1)/2
  */
}
```

## 7. Print All Subarrays
```java
public static void SubArrays(int Numbers[]) {
   int tp = 0;
   for(int i = 0; i < Numbers.length; i++) {
     int start = i;
     for(int j = i; j < Numbers.length; j++) {
       int end = j;
       for(int k = start; k <= end; k++) {
         System.out.print(Numbers[k] + " ");
       }
       tp++;
     }
     System.out.println();
   }
   System.out.println();
   System.out.println("total pairs is : " + tp);
}
```

## 8. Maximum Sum of Subarrays (Brute Force)
```java
public static void MaxSumSubArrays(int Numbers[]) {
  int CurrentSum = 0;
  int MaxSum = Integer.MIN_VALUE;
  for(int i = 0; i < Numbers.length; i++) {
    int start = i;
    for(int j = i; j < Numbers.length; j++) {
      int end = j;
      CurrentSum = 0;
      for(int k = start; k <= end; k++) {
        CurrentSum += Numbers[k];
        System.out.print(CurrentSum + " ");
      }
      if(MaxSum < CurrentSum) {
        MaxSum = CurrentSum;
      }
    }
    System.out.println();
  }
  System.out.println();
  System.out.println(" max sum is above sub Arrays pairs : " + MaxSum);
}
```

## 9. Maximum Sum using Prefix Array
```java
public static void PrefixSubArray(int Numbers[]) {
  int CurrentSum = 0;
  int MaxSum = Integer.MIN_VALUE;
  int prefix[] = new int[Numbers.length];
  prefix[0] = Numbers[0];

  // calculate prefix array
  for(int i = 1; i < prefix.length; i++) {
    prefix[i] = prefix[i - 1] + Numbers[i];
  }

  for(int i = 0; i < Numbers.length; i++) {
    int start = i;
    for(int j = i; j < Numbers.length; j++) {
      int end = j;
      CurrentSum = start == 0 ? prefix[end] : prefix[end] - prefix[start - 1];
      if(MaxSum < CurrentSum) {
        MaxSum = CurrentSum;
      }
    }
  }
  System.out.println(" max sum is : " + MaxSum);
}
```

## 10. Maximum Sum using Kadane's Algorithm
```java
public static void KandansSum(int Numbers[]) {
  int currentSum = 0;
  int MaxSum = Integer.MIN_VALUE;
  for(int i = 0; i < Numbers.length; i++) {
    currentSum = currentSum + Numbers[i];
    if(currentSum < 0) {
       currentSum = 0;
    }
    MaxSum = Math.max(currentSum, MaxSum);
  }
  System.out.println(" max value of array with help of Kandans Sum is : " + MaxSum);
}
```

---

# 🔄 Recursion

## 1. Print Numbers in Decreasing Order (n to 1)
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static void RecursionPrintDec(int n) {
  if( n == 1 ) {
    System.out.println(n);
    return;
  }
  System.out.print(n + " ");
  RecursionPrintDec(n - 1);
}
```

## 2. Print Numbers in Increasing Order (1 to n)
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static void RecursionPrintIncre(int n) {
  if(  n == 1 ) {
    System.out.println(n);
    return;
  } 
  RecursionPrintIncre(n - 1);
  System.out.print(n + " ");
}
```

## 3. Factorial of n (n!)
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static int factorial(int n) {
  if( n == 0) {
    return 1;
  }
  int fnm1 = factorial(n - 1);
  int fn = n * fnm1;  // Fixed: was calling factorial(n-1) twice
  return fn;
}
```

## 4. Sum of First n Natural Numbers
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static int calSum(int n) {
  if( n == 1) {
    return 1;
  }
  int Snm1 = calSum(n-1);
  int Sn =  n + Snm1;
  return Sn;
}
```

## 5. Fibonacci Number (nth term)
**Time Complexity**: O(2^n) | **Space Complexity**: O(n)
```java
public static int fib(int n) {
  if( n == 0 || n == 1) {
    return n;
  }
  int Fnm1 = fib(n - 1);
  int Fnm2 = fib(n - 2);
  int Fn = Fnm1 + Fnm2;
  return Fn;
}
```

## 6. Check if Array is Sorted
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static boolean isSorted(int arr[], int i) {
  if( i == arr.length - 1) {
    return true;
  }
  if(arr[i] > arr[i + 1]) {
    return false;
  }
  return isSorted(arr, i+1);
}
```

## 7. First Occurrence of Element in Array
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static int firstOccurance(int arr[], int key, int i) {
  if(i == arr.length) {
    return -1;
  }
  if(arr[i] == key) {
    return i;
  }
  return firstOccurance(arr, key, i+1);
}
```

## 8. Last Occurrence of Element in Array
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static int lastOccurance(int arr[], int key, int i) {
  if(i == arr.length) {
    return -1;
  }
  int isfound = lastOccurance(arr, key, i + 1);
  if(isfound == -1 && arr[i] == key) {
    return i;
  }
  return isfound;
}
```

## 9. Power of Number (x^n) - Basic
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static int FindPower(int x , int n) {
  if( n == 0) {  // Fixed: should be n == 0, not n == 1
    return 1;
  }
  return x * FindPower(x, n-1);  // Fixed: simplified logic
}
```

## 10. Optimized Power (a^n) - Divide & Conquer
**Time Complexity**: O(log n) | **Space Complexity**: O(log n)
```java
public static int optimizedPower(int a , int n) {
  if( n == 0) {
    return 1;
  }
  int half = optimizedPower(a, n/2);
  int halfPowerSq = half * half;
  if( n % 2 != 0) {
    halfPowerSq = a * halfPowerSq;
  }
  return halfPowerSq;
}
```

## 11. Tiling Problem (2×n floor with 2×1 tiles)
**Formula**: f(n) = f(n-1) + f(n-2)  
**Time Complexity**: O(2^n) | **Space Complexity**: O(n)
```java
public static int tilingProblem(int n) {
  if(n == 0 || n == 1) {
    return 1;
  }
  int fnm1 = tilingProblem(n-1);
  int fnm2 = tilingProblem(n-2);
  int totalway = fnm1 + fnm2;
  return totalway;
}
```

## 12. Remove Duplicates from String
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static void RemoveDublicates(String str, int idx, StringBuilder newStr, boolean map[]) {
  if(idx == str.length()) {
    System.out.println(newStr);
    return;
  }
  char currChar = str.charAt(idx);
  if(map[currChar-'a'] == true) {
    RemoveDublicates(str, idx+1, newStr, map);
  }
  else {
    map[currChar-'a'] = true;
    RemoveDublicates(str, idx+1, newStr.append(currChar), map);
  }
}
```

## 13. Friends Pairing Problem
**Formula**: f(n) = f(n-1) + (n-1)*f(n-2)  
**Time Complexity**: O(2^n) | **Space Complexity**: O(n)
```java
public static int friendsPairing(int n) {
  if(n == 1 || n ==2) {
    return n;
  }
  int fnm1 = friendsPairing(n-1);
  int fnm2 = friendsPairing(n-2);
  int pairsWays = (n-1) * fnm2;
  int totalWays = fnm1 + pairsWays;
  return totalWays;
}
```

## 14. Binary Strings without Consecutive 1s
**Time Complexity**: O(2^n) | **Space Complexity**: O(n)
```java
public static void PrintBinaryConsecutiveStrings(int n , int lastPlace, String str){
  if(n == 0) {
    System.out.println(str);
    return;
  }
  PrintBinaryConsecutiveStrings(n-1, 0, str+"0");
  if(lastPlace == 0) {
    PrintBinaryConsecutiveStrings(n-1, 1, str+"1");
  }
}
```
# ⚔️ Divide and Conquer

## Utility Function - Print Array
```java
public static void PrintArr(int arr[]) {
  for(int i = 0; i < arr.length; i++) {
    System.out.print(arr[i] + " ");
  }
  System.out.println();
}
```

## 1. Merge Sort Algorithm
**Time Complexity**: O(n log n) | **Space Complexity**: O(n)  
**Best for**: Stable sorting, guaranteed O(n log n) performance

```java
public static void MergeSort(int arr[], int si, int ei) {
  // base case
  if(si >= ei) {
    return;
  }
  
  // divide
  int mid = si + (ei - si)/2;  // Prevents integer overflow
  MergeSort(arr, si, mid);     // left part 
  MergeSort(arr, mid+1, ei);   // right part
  Merge(arr, si, mid, ei);     // merge both parts
}

public static void Merge(int arr[], int si, int mid, int ei) {
  // Create temporary array: left(0,3)=4 right(4,6)=3 -> 6-0+1
  int temp[] = new int[ei - si + 1];
  int i = si;     // iterator for left part
  int j = mid + 1; // iterator for right part
  int k = 0;      // iterator for temp array
  
  // Compare and merge
  while(i <= mid && j <= ei) {
    if(arr[i] < arr[j]) {
      temp[k] = arr[i];
      i++;
    } else {
      temp[k] = arr[j];
      j++;
    }
    k++;
  }
  
  // Add remaining elements from left part
  while(i <= mid) {
    temp[k++] = arr[i++];
  }
  
  // Add remaining elements from right part
  while(j <= ei) {
    temp[k++] = arr[j++];
  }
  
  // Copy temp array back to original array
  for(k = 0, i = si; k < temp.length; k++, i++) {
    arr[i] = temp[k];
  }
}
```

## 2. Quick Sort Algorithm
**Time Complexity**: O(n log n) average, O(n²) worst | **Space Complexity**: O(log n)  
**Best for**: In-place sorting, average case performance

```java
public static void quickSort(int arr[], int si, int ei) {
  if(si >= ei) {
    return;
  }
  
  // Partition and get pivot index
  int pIdx = partition(arr, si, ei);
  quickSort(arr, si, pIdx - 1);  // sort left part
  quickSort(arr, pIdx + 1, ei);  // sort right part
}

public static int partition(int arr[], int si, int ei) {
  int pivot = arr[ei];  // choose last element as pivot
  int i = si - 1;       // index for smaller elements
  
  for(int j = si; j < ei; j++) {
    if(arr[j] <= pivot) {
      i++;
      // swap arr[i] and arr[j]
      int temp = arr[j];
      arr[j] = arr[i];
      arr[i] = temp;
    }
  }
  
  i++;
  // Place pivot in correct position
  int temp = pivot;
  arr[ei] = arr[i];
  arr[i] = temp;
  return i;  // return pivot index
}
```

## 3. Rotated Array Search
**Time Complexity**: O(log n) | **Space Complexity**: O(log n)  
**Problem**: Search element in a sorted rotated array

```java
public static int RotateSearch(int arr[], int tar, int si, int ei) {
  // base case
  if(si > ei) {
    return -1;
  }
  
  // find mid
  int mid = si + (ei - si) / 2;
  
  // case: found target
  if(arr[mid] == tar) {
    return mid;
  }
  
  // mid on L1 (left sorted part)
  if(arr[si] <= arr[mid]) {
    // case a: target in left sorted part
    if(arr[si] <= tar && tar <= arr[mid]) {
      return RotateSearch(arr, tar, si, mid - 1);
    } else {
      // case b: target in right part
      return RotateSearch(arr, tar, mid + 1, ei);
    }
  }
  // mid on L2 (right sorted part)
  else {
    // case c: target in right sorted part
    if(arr[mid] <= tar && tar <= arr[ei]) {
      return RotateSearch(arr, tar, mid + 1, ei);
    } else {
      // case d: target in left part
      return RotateSearch(arr, tar, si, mid - 1);
    }
  }
}
```

---

---

# 📘 Sorting Algorithms in Java

Here are some commonly used sorting algorithms with implementations in **Java**.

## 🔹 1. Bubble Sort
Repeatedly compares adjacent elements and swaps if needed.  
**Time Complexity**: O(n²) | **Best Case**: O(n) (already sorted)

```java
public static void BubbleSorting(int arr[]) {
   for(int turn = 0; turn < arr.length-1; turn++) {
       for(int j = 0; j < arr.length-1-turn; j++) {
           if(arr[j] > arr[j+1]) {
               int temp = arr[j];
               arr[j] = arr[j+1];
               arr[j+1] = temp;
           }
       }
   }
}
```

## 2. Selection Sort
Finds the minimum element and puts it at the beginning.  
**Time Complexity**: O(n²) | **Not Stable**

```java
public static void SelectionSorting(int arr[]) {
    for(int i = 0; i < arr.length - 1; i++) {
        int minPos = i;
        for(int j = i + 1; j < arr.length; j++) {
            if(arr[minPos] > arr[j]) {
                minPos = j;
            }
        }
        int temp = arr[minPos];
        arr[minPos] = arr[i];
        arr[i] = temp;
    }
}
```

## 3. Insertion Sort
Inserts each element in the correct position.  
**Time Complexity**: O(n²) | **Best Case**: O(n) (already sorted)

```java
public static void InsertionSorting(int arr[]) {
    for(int i = 1; i < arr.length; i++) {
        int curr = arr[i];
        int prev = i - 1;
        while(prev >= 0 && arr[prev] > curr) {
            arr[prev + 1] = arr[prev];
            prev--;
        }
        arr[prev + 1] = curr;
    }
}
```

## 4. Counting Sort
Works well when range of input numbers is small.  
**Time Complexity**: O(n + k) | **Not Comparison Based**

```java
public static void CountingSorting(int arr[]) {
    int largest = Integer.MIN_VALUE;
    for(int i = 0; i < arr.length; i++) {
        largest = Math.max(largest, arr[i]);
    }

    int count[] = new int[largest + 1];
    for(int i = 0; i < arr.length; i++) {
        count[arr[i]]++;
    }

    int j = 0;
    for(int i = 0; i < count.length; i++) {
        while(count[i] > 0) {
            arr[j] = i;
            j++;
            count[i]--;
        }
    }
}
```

## 5. Built-in Sorting in Java {MOST IMPORTANT SHORTCUT METHOD}
**Best for Interviews** → Always use Arrays.sort()

```java
import java.util.Arrays;
import java.util.Collections;

Arrays.sort(arr);                       // ascending
Arrays.sort(arr, 0, 3);                 // range-based sorting
Arrays.sort(arr, Collections.reverseOrder());  // descending (only with Integer[])
```

**⚠️ Note**: Collections.reverseOrder() works only with Integer[], not int[].

---

# 📘 2D Arrays in Java

## 🔹 Searching in 2D Array
Traverse through each element and compare with the key.  
**Time Complexity**: O(n × m)

```java
public static boolean Search(int matrix[][], int key) {
    for(int i = 0; i < matrix.length; i++) {
        for(int j = 0; j < matrix[0].length; j++) {
            if(matrix[i][j] == key) {
                System.out.println("Key found at: (" + i + "," + j + ")");
                return true;
            }
        }
    }
    System.out.println("Key not found");
    return false;
}
```

## Spiral Matrix Traversal
Print elements in spiral order (top → right → bottom → left).  
Use 4 pointers: startRow, endRow, startCol, endCol.

```java
public static void PrintSpiral(int matrix[][]) {
    int startRow = 0, startCol = 0;
    int endRow = matrix.length - 1;
    int endCol = matrix[0].length - 1;

    while(startRow <= endRow && startCol <= endCol) {
        // top
        for(int j = startCol; j <= endCol; j++) {
            System.out.print(matrix[startRow][j] + " ");
        }

        // right
        for(int i = startRow + 1; i <= endRow; i++) {
            System.out.print(matrix[i][endCol] + " ");
        }

        // bottom
        for(int j = endCol - 1; j >= startCol; j--) {
            if(startRow == endRow) break;
            System.out.print(matrix[endRow][j] + " ");
        }

        // left
        for(int i = endRow - 1; i > startRow; i--) {
            if(startCol == endCol) break;
            System.out.print(matrix[i][startCol] + " ");
        }

        startRow++; endRow--;
        startCol++; endCol--;
    }
    System.out.println();
}
```

## Diagonal Sum of Matrix
Primary diagonal: matrix[i][i]  
Secondary diagonal: matrix[i][n-1-i]  
Optimized in O(n) time.

```java
public static int DiagonalSum(int matrix[][]) {
    int sum = 0;
    for(int i = 0; i < matrix.length; i++) {
        // Primary diagonal
        sum += matrix[i][i];

        // Secondary diagonal
        if(i != matrix.length - 1 - i) {
            sum += matrix[i][matrix.length - 1 - i];
        }
    }
    return sum;
}
```

---

## 🏁 Example Usage

### Arrays Example
```java
public static void main(String[] args) {
  int Numbers[] = {2, 4, 6, 8, 10, 12, 14};
  // For Kadane's algorithm use: {-2, -3, 4, -1, -2, 1, 5, -3}

  int key = 8;
  System.out.println("Largest element: " + getLargest(Numbers));
  System.out.println("Smallest element: " + getSmallest(Numbers));
  System.out.println("Linear search result: " + LinearSearch(Numbers, key));
  System.out.println("Binary search result: " + BinearySearch(Numbers, key));
}
```

### Recursion Example
```java
public static void main(String[] args) {
  // Test recursion functions
  RecursionPrintDec(5);           // 5 4 3 2 1
  RecursionPrintIncre(5);         // 1 2 3 4 5
  System.out.println(factorial(5));      // 120
  System.out.println(calSum(5));          // 15
  System.out.println(fib(6));             // 8
  
  int arr[] = {1, 2, 3, 4, 5};
  System.out.println(isSorted(arr, 0));   // true
  
  String str = "appnnacollege";
  RemoveDublicates(str, 0, new StringBuilder(""), new boolean[26]);
  
  PrintBinaryConsecutiveStrings(3, 0, "");  // All 3-bit binary strings without consecutive 1s
}
```

### Divide and Conquer Example
```java
public static void main(String[] args) {
  // Merge Sort Example
  int arr1[] = {6, 3, 9, 5, 2, 8};
  System.out.println("Original array:");
  PrintArr(arr1);
  
  MergeSort(arr1, 0, arr1.length - 1);
  System.out.println("After Merge Sort:");
  PrintArr(arr1);
  
  // Quick Sort Example
  int arr2[] = {6, 3, 9, 5, 2, 8};
  System.out.println("Before Quick Sort:");
  PrintArr(arr2);
  
  quickSort(arr2, 0, arr2.length - 1);
  System.out.println("After Quick Sort:");
  PrintArr(arr2);
  
  // Rotated Array Search Example
  int arr3[] = {4, 5, 6, 7, 0, 1, 2};
  int target = 0;
  int tarIdx = RotateSearch(arr3, target, 0, arr3.length - 1);
  System.out.println("Target " + target + " found at index: " + tarIdx); // Output: 4
}
```
# 🧵 Strings in Java

## 📋 Important String Concepts

### String Properties
- Strings are **IMMUTABLE** in Java
- String literals are stored in **String Pool**
- Use `StringBuilder` for multiple concatenations
- Use `.equals()` for content comparison, not `==`

---

## 🔹 Basic String Operations

### 1. String Input Methods
```java
Scanner sc = new Scanner(System.in);
String word = sc.next();        // takes only single word
String sentence = sc.nextLine(); // takes complete line with spaces
```

### 2. String Length
```java
String name = "vishal singh rajput";
System.out.println(name.length()); // Output: 19
```

### 3. String Concatenation
```java
String firstName = "vishal";
String lastName = "rajput";
String fullName = firstName + " " + lastName;
// Output: "vishal rajput"
```

### 4. Character Access
```java
String fullName = "vishal rajput";
System.out.println(fullName.charAt(5)); // Output: 'l'
```

---

## 🔍 String Comparison

### String Equality Check
```java
String s1 = "vishal";
String s2 = "vishal";           // String literal (same reference)
String s3 = new String("vishal"); // New object (different reference)

// ❌ Wrong way (compares references)
if(s1 == s2) {
    System.out.println("both are equal"); // This will print
}

if(s1 == s3) {
    System.out.println("both are equal"); // This WON'T print
}

// ✅ Correct way (compares content)
if(s1.equals(s3)) {
    System.out.println("both are equal"); // This will print
}
```

### Lexicographic Comparison
```java
String fruits[] = {"apple", "mango", "banana"};
String largest = fruits[0];

for(int i = 0; i < fruits.length; i++) {
    if(largest.compareTo(fruits[i]) < 0) {
        largest = fruits[i];
    }
}
System.out.println(largest); // Output: "mango"

/*
compareTo() returns:
- 0: strings are equal
- positive: first string > second string
- negative: first string < second string
*/
```

---

## 🛠️ Essential String Problems

### 1. Print Each Character with Space
**Time Complexity**: O(n) | **Space Complexity**: O(1)
```java
public static void PrintString(String fullName) {
    for(int i = 0; i < fullName.length(); i++) {
        System.out.print(fullName.charAt(i) + " ");
    }
    System.out.println();
}
// Input: "Hello" → Output: "H e l l o "
```

### 2. Check Palindrome
**Time Complexity**: O(n) | **Space Complexity**: O(1)
```java
public static boolean isPalindrome(String strP) {
    for(int i = 0; i < strP.length(); i++) {
        int n = strP.length();
        if(strP.charAt(i) != strP.charAt(n - i - 1)) {
            return false;
        }
    }
    return true;
}
// Examples: "racecar" → true, "hello" → false
```

### 3. Shortest Path Problem
**Time Complexity**: O(n) | **Space Complexity**: O(1)
```java
public static float getShortestPath(String path) {
    int x = 0, y = 0;
    for(int i = 0; i < path.length(); i++) {
        char dir = path.charAt(i);
        if(dir == 'S') {
            y--;
        } else if(dir == 'N') {
            y++;
        } else if(dir == 'W') {
            x--;
        } else { // 'E'
            x++;
        }
    }
    int X2 = x * x;
    int Y2 = y * y;
    return (float)Math.sqrt(X2 + Y2);
}
// Input: "WNEENESENNN" → Output: shortest distance from origin
```

### 4. Extract Substring (Manual Implementation)
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static String subStringn(String S, int si, int ei) {
    String substr = "";
    for(int i = si; i < ei; i++) {
        substr += S.charAt(i);
    }
    return substr;
}

// Built-in method (preferred):
// String S = "Hello World";
// System.out.println(S.substring(0, 5)); // Output: "Hello"
```

### 5. Title Case Conversion
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static String toUpperCase(String Str) {
    StringBuilder sb = new StringBuilder("");
    
    char ch = Character.toUpperCase(Str.charAt(0));
    sb.append(ch);
    
    for(int i = 1; i < Str.length(); i++) {
        if(Str.charAt(i) == ' ' && i < Str.length() - 1) {
            sb.append(Str.charAt(i));
            i++;
            sb.append(Character.toUpperCase(Str.charAt(i)));
        } else {
            sb.append(Str.charAt(i));
        }
    }
    return sb.toString();
}
// Input: "hi, i am vishal" → Output: "Hi, I Am Vishal"
```

### 6. String Compression
**Time Complexity**: O(n) | **Space Complexity**: O(1)
```java
public static String compress(String Cstr) {
    String newStr = "";
    for(int i = 0; i < Cstr.length(); i++) {
        Integer count = 1;
        while(i < Cstr.length() - 1 && Cstr.charAt(i) == Cstr.charAt(i + 1)) {
            count++;
            i++;
        }
        newStr += Cstr.charAt(i);
        if(count > 1) {
            newStr += count.toString();
        }
    }
    return newStr;
}
// Input: "aaabbcccdd" → Output: "a3b2c3d2"
```

## 🏗️ StringBuilder (For Multiple Operations)

### Why StringBuilder?
- String concatenation creates new objects every time (inefficient)
- StringBuilder is mutable and faster for multiple operations

```java
// ❌ Inefficient (creates multiple String objects)
String result = "";
for(int i = 0; i < 1000; i++) {
    result += i; // Creates new String object each time
}

// ✅ Efficient (modifies same StringBuilder object)
StringBuilder sb = new StringBuilder();
for(int i = 0; i < 1000; i++) {
    sb.append(i); // Modifies existing object
}
String result = sb.toString();
```

### StringBuilder Operations
```java
StringBuilder sb = new StringBuilder("");

// Add characters a to z
for(char ch = 'a'; ch <= 'z'; ch++) {
    sb.append(ch); // append = add at the end
}
System.out.println(sb); // Output: "abcdefghijklmnopqrstuvwxyz"

// Other useful methods:
sb.insert(0, "START");     // Insert at beginning
sb.delete(0, 5);           // Delete characters from index 0 to 4
sb.reverse();              // Reverse the string
sb.setCharAt(0, 'Z');      // Set character at specific index
```

---

## 🎯 Advanced String Problems

### 1. Remove Duplicates (Using Boolean Array)
**Time Complexity**: O(n) | **Space Complexity**: O(1) - constant size array
```java
public static String removeDuplicates(String str) {
    boolean[] seen = new boolean[26]; // for lowercase a-z
    StringBuilder result = new StringBuilder();
    
    for(int i = 0; i < str.length(); i++) {
        char ch = str.charAt(i);
        int index = ch - 'a'; // Convert to array index
        
        if(!seen[index]) {
            seen[index] = true;
            result.append(ch);
        }
    }
    return result.toString();
}
// Input: "programming" → Output: "progamin"
```

### 2. Count Vowels and Consonants
**Time Complexity**: O(n) | **Space Complexity**: O(1)
```java
public static void countVowelsConsonants(String str) {
    int vowels = 0, consonants = 0;
    str = str.toLowerCase();
    
    for(int i = 0; i < str.length(); i++) {
        char ch = str.charAt(i);
        if(ch >= 'a' && ch <= 'z') {
            if(ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
                vowels++;
            } else {
                consonants++;
            }
        }
    }
    System.out.println("Vowels: " + vowels + ", Consonants: " + consonants);
}
```

### 3. Reverse Words in String
**Time Complexity**: O(n) | **Space Complexity**: O(n)
```java
public static String reverseWords(String str) {
    String[] words = str.split(" ");
    StringBuilder result = new StringBuilder();
    
    for(int i = words.length - 1; i >= 0; i--) {
        result.append(words[i]);
        if(i > 0) result.append(" ");
    }
    return result.toString();
}
// Input: "Hello World Java" → Output: "Java World Hello"
```

### 4. Check Anagram
**Time Complexity**: O(n) | **Space Complexity**: O(1)
```java
public static boolean isAnagram(String str1, String str2) {
    if(str1.length() != str2.length()) {
        return false;
    }
    
    int[] charCount = new int[26];
    
    // Count characters in first string
    for(int i = 0; i < str1.length(); i++) {
        charCount[str1.charAt(i) - 'a']++;
    }
    
    // Subtract characters from second string
    for(int i = 0; i < str2.length(); i++) {
        charCount[str2.charAt(i) - 'a']--;
    }
    
    // Check if all counts are zero
    for(int count : charCount) {
        if(count != 0) return false;
    }
    
    return true;
}
// Input: "listen", "silent" → Output: true
```

---

## 🧮 String to Number Conversions

```java
// String to Integer
String numStr = "123";
int num = Integer.parseInt(numStr);

// Integer to String
int number = 123;
String str = Integer.toString(number);
// or
String str2 = String.valueOf(number);

// String to Character Array
String text = "hello";
char[] charArray = text.toCharArray();

// Character Array to String
char[] chars = {'h', 'e', 'l', 'l', 'o'};
String text2 = new String(chars);
```

---

## 📊 Important String Methods Cheat Sheet

```java
String str = "Hello World";

str.length()              // 11
str.charAt(0)             // 'H'
str.indexOf('o')          // 4 (first occurrence)
str.lastIndexOf('o')      // 7 (last occurrence)
str.substring(0, 5)       // "Hello"
str.toLowerCase()         // "hello world"
str.toUpperCase()         // "HELLO WORLD"
str.trim()                // removes leading/trailing spaces
str.replace('l', 'x')     // "Hexxo Worxd"
str.contains("World")     // true
str.startsWith("Hello")   // true
str.endsWith("World")     // true
str.split(" ")            // ["Hello", "World"]
str.isEmpty()             // false
```

---

## 🎯 Practice Problems

### Easy
1. Count frequency of each character
2. Check if string contains only digits
3. Reverse a string using recursion
4. Find first non-repeating character

### Medium
5. Longest common prefix
6. Valid parentheses checker
7. String compression and decompression
8. Minimum window substring

### Hard
9. Edit distance between strings
10. Regular expression matching

---

## 🚀 Pro Tips for String Problems

1. **Always consider edge cases**: empty string, single character, null
2. **Use StringBuilder** for multiple concatenations
3. **Character to index mapping**: `ch - 'a'` for lowercase letters
4. **Two-pointer technique** works great for palindromes and reversals
5. **Hash maps/arrays** are useful for frequency counting
6. **Remember ASCII values**: 'a' = 97, 'A' = 65, '0' = 48
7. **String pool behavior**: Use `.equals()` not `==` for comparison

---

## 📝 Example Usage

```java
public static void main(String[] args) {
    // Test basic operations
    String name = "vishal rajput";
    PrintString(name);
    
    // Test palindrome
    System.out.println(isPalindrome("racecar")); // true
    System.out.println(isPalindrome("hello"));   // false
    
    // Test compression
    System.out.println(compress("aaabbcccdd")); // "a3b2c3d2"
    
    // Test title case
    System.out.println(toUpperCase("hi, i am vishal")); // "Hi, I Am Vishal"
    
    // Test shortest path
    System.out.println(getShortestPath("WNEENESENNN")); // distance
    
    // StringBuilder example
    StringBuilder sb = new StringBuilder();
    for(char ch = 'a'; ch <= 'z'; ch++) {
        sb.append(ch);
    }
    System.out.println(sb.toString()); // "abcdefghijklmnopqrstuvwxyz"
}
```