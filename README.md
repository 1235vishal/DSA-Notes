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

```java
 2. Get Smallest Element in Array

public static int getSmallest(int Numbers[]) {
  int smallest = Integer.MAX_VALUE; // +Infinity
  for(int i = 0; i < Numbers.length; i++) {
    if(smallest > Numbers[i]) {
      smallest = Numbers[i];
    }
  }
  return smallest;
}
3. Linear Search
public static int LinearSearch(int Numbers[], int key) {
  for(int i = 0; i < Numbers.length; i++) {
    if(Numbers[i] == key) {
      return i;
    }
  }
  return -1;
}

4. Binary Search (Array must be sorted)

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

5. Reverse Array

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

6. Print All Pairs in Array

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

7. Print All Subarrays

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

8. Maximum Sum of Subarrays (Brute Force)

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

9. Maximum Sum using Prefix Array

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

10. Maximum Sum using Kadane’s Algorithm

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

11. Main Method to Test All Functions

public static void main(String[] args) {
  int Numbers[] = {2, 4, 6, 8, 10, 12, 14};
  //below array only for Kadane's algorithm
  // int Numbers[] = {-2, -3, 4, -1, -2, 1, 5, -3};

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