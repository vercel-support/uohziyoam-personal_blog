---
title: "Quick Sort"
date: 2020-01-10T01:52:44-05:00
draft: false
tags: ["Quick Sort", "Sorting Techniques"]
categories: ["Algorithms"]
author: "Yizhou Mao"
comment: false
toc: true
---

---

Quick Sort Algorithm utilizes the idea of Divide-and-Conquer. It picks a pivot from the array and then partition items around the pivot in the array. Recursively repeat this process until all subarrays have been partitioned. [$ _{[1]} $](#reference)

## **What is Quick Sort?**

Quick Sort is commonly used in Computer Science when required to deal with in-memory sorting problems. Two main actions taken in quick sort are **swap()** and **partition()**. The main idea of quick sort is Divide-and-Conquer. Divide-and-Conquer breaks down a problem into many sub-problems recursively until these sub-problems can be solved directly. As long as all sub-problems have been solved, combine these sub-solutions to give the solutions to the original problem. [$ _{[2]} $](#reference)

## **Quick Sort: How it actually works?**

1. Divide:

   - Partition every elements in the array until
     **each element in the left array <= each element in the right array**

$$
    e.g.
    \begin{array}{|c|c|}
    \hline
    12 & 8 & 14 & 4 & 6 & 13  \\\\
    \hline
    \end{array}
    \Rightarrow
    \begin{array}{|c|c|}
    \hline
    6 & 8 & 4 & 14 & 12 & 13  \\\\
    \hline
    \end{array}
$$

2. Conquer:

   - Apply the quick sort recursively to the subarrays, stopping when a subarray has a single element.

3. Combine:
   - Nothing needs to be done,because of the criterion used in forming the subarrays.

### **Here is a youtube Video explains Quick Sort:**

{{< youtube SLauY6PpjW4 >}}

## **Quick Sort: Real Example**

### Main Function for Quick Sort:

```java
public static int[] quicksort(int[] arr, int left, int right) {
  if (left < right) {
      int location = partition(arr, left, right);
      quicksort(arr, left, location);
      quicksort(arr, location + 1, right);
  }
  return arr;
}
```

### Method for action Partition():

```java
public static int partition(int[] arr, int left, int right) {
  int pivot = arr[(left + right) / 2];
  int start = left - 1;
  int end = right + 1;

  while (true) {
      do {
          start++;
      } while (arr[start] < pivot);

      do {
          end--;
      } while (arr[end] > pivot);

      if (start < end) {
          swap(arr, start, end);
      } else {
          return end;
      }
  }
}
```

### Method for action Swap():

```java
public static void swap(int[] arr, int left, int right) {
  int leftCopy = arr[left];
  arr[left] = arr[right];
  arr[right] = leftCopy;
}
```

## **Related Problems**

1.  **Move all negative numbers to beginning and positive to end with constant extra space.** An array contains both positive and negative numbers in random order. Rearrange the array elements so that all negative numbers appear before all positive numbers. [$ _{[3]} $](#reference)

        Input: -12, 11, -13, -5, 6, -7, 5, -3, -6
        Output: -12, -13, -5, -7, -3, -6, 11, 6, 5

    ```java
    public static void moveAllNegative(int[] arr) {
        int positivei = 0;

        for (int i = 0; i < arr.length; i++) {
            if (arr[i] < 0) {
                int temp = arr[positivei];
                arr[positivei] = arr[i];
                arr[i] = temp;
                positivei++;
            }
        }
    }
    ```

## **References** {#reference}

http://en.wikipedia.org/wiki/Quicksort

http://cs-people.bu.edu/dgs

https://www.geeksforgeeks.org/move-negative-numbers-beginning-positive-end-constant-extra-space

$$
$$
