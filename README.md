# 📘 Vishal's DSA Notes

Welcome to my **DSA Learning Notes**.  
This repo is just **one README.md file** where I write all my important DSA concepts, shortcuts, and code snippets.  
So I can open this repo anytime and revise everything quickly 🚀.

## 🔹 Roadmap
1. Arrays ✅


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
## 10. Maximum Sum using Kadane’s Algorithm
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

## 11. Main Method to Test All Functions
```java
public static void main(String[] args) {
  int Numbers[] = {2, 4, 6, 8, 10, 12, 14};
  //below array only for Kadane's algorithm
  // int Numbers[] = {-2, -## 3, 4, -1, -2, 1, 5, -## 3};

  int key = 8;
  System.out.println("our array Largest element is : " + getLargest(Numbers));
  System.out.println("our array Smallest element is : " + getSmallest(Numbers));
  int index = LinearSearch(Numbers, key);
  if(index == -1) {
    System.out.println("not found");
  } else {
    System.out.println("our array key index is  : " + index);
  }
  System.out.println("our array key index using binary search is  : " + BinearySearch(Numbers, key));

  Reverse(Numbers);
  for(int i = 0; i < Numbers.length; i++) {
    System.out.print(Numbers[i] + " ");
  }
  System.out.println();

  PairsofNum(Numbers);
  SubArrays(Numbers);
  MaxSumSubArrays(Numbers);
  PrefixSubArray(Numbers);
  KandansSum(Numbers);
}
```

# 📘 Sorting Algorithms in Java

Here are some commonly used sorting algorithms with implementations in **Java**.

---

## 🔹 1. Bubble Sort
```java
- Repeatedly compares adjacent elements and swaps if needed.  
- Time Complexity: O(n²)  
- Best Case: O(n) (already sorted)  


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
```java
Finds the minimum element and puts it at the beginning.

Time Complexity: O(n²)

Not Stable

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
##  3. Insertion Sort
```java
Inserts each element in the correct position.

Time Complexity: O(n²)

Best Case: O(n) (already sorted)

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
##  4. Counting Sort
```java
Works well when range of input numbers is small.

Time Complexity: O(n + k)

Not Comparison Based

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
##  5. Built-in Sorting in Java {MOST IMPORT SHORTCUT METHODE ARRAYS SORTING}
```java
Best for Interviews → Always use Arrays.sort()

Example:

import java.util.Arrays;
import java.util.Collections;

Arrays.sort(arr);                       // ascending
Arrays.sort(arr, 0, 3);                 // range-based sorting
Arrays.sort(arr, Collections.reverseOrder());  // descending (only with Integer[])
```
##  ️ Note: Collections.reverseOrder() works only with Integer[], not int[].
```java
🏁 Main Method Example

public static void main(String[] args) {
   int arr[] = {4, 5, 1, 2, 3};

   // BubbleSorting(arr);
   // SelectionSorting(arr);
   // InsertionSorting(arr);
   CountingSorting(arr);

   for(int i = 0; i < arr.length; i++) {
       System.out.print(arr[i] + " ");
   }
   System.out.println();
}
```

# 📘 2D Arrays in Java

---

## 🔹 Searching in 2D Array
- Traverse through each element and compare with the key.  
- **Time Complexity**: O(n × m)  

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
```
Print elements in spiral order (top → right → bottom → left).

Use 4 pointers: startRow, endRow, startCol, endCol.

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
##  Diagonal Sum of Matrix
```java
Primary diagonal: matrix[i][i]

Secondary diagonal: matrix[i][n-1-i]

Optimized in O(n) time.

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
## 🏁 Main Method Example
```java
public static void main(String[] args) {
    int matrix[][] = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12},
        {13, 14, 15, 16}
    };

    // Search(matrix, 7);
    // PrintSpiral(matrix);
    System.out.println("Diagonal Sum = " + DiagonalSum(matrix));
}
```