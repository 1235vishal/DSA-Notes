# 📘 Vishal's DSA Notes

Welcome to my **DSA Learning Notes**.  
This repo is just **one README.md file** where I write all my important DSA concepts, shortcuts, and code snippets.  
So I can open this repo anytime and revise everything quickly 🚀.

## 🔹 Roadmap
1. Arrays ✅
2. Recursion ✅
3. Sorting Algorithms ✅
4. 2D Arrays ✅

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

### 2D Arrays Example
```java
public static void main(String[] args) {
    int matrix[][] = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12},
        {13, 14, 15, 16}
    };

    Search(matrix, 7);
    PrintSpiral(matrix);
    System.out.println("Diagonal Sum = " + DiagonalSum(matrix));
}
```