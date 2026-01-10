**Problem Description**

You are given an array A of integers that represent the lengths of ropes.
You need to connect these ropes into one rope. The cost of joining two ropes equals the sum of their lengths.
Find and return the minimum cost to connect these ropes into one rope.

**Problem Constraints**

```
1 <= length of the array <= 100000
1 <= A[i] <= 1000
```

**Input Format**

The only argument given is the integer array A.

**Output Format**

```
Return an integer denoting the minimum cost to connect these ropes into one rope.
```

**Example Input**

```
Input 1:

 A = [1, 2, 3, 4, 5]

Input 2:

 A = [5, 17, 100, 11]
```
**Example Output**
```
Output 1:

 33

Output 2:

 182
```
**Example Explanation**
```
Explanation 1:

Given array A = [1, 2, 3, 4, 5].
 Connect the ropes in the following manner:
 1 + 2 = 3
 3 + 3 = 6
 4 + 5 = 9
 6 + 9 = 15

 So, total cost  to connect the ropes into one is 3 + 6 + 9 + 15 = 33.
```
```
Explanation 2:

 Given array A = [5, 17, 100, 11].
 Connect the ropes in the following manner:
 5 + 11 = 16
 16 + 17 = 33
 33 + 100 = 133

 So, total cost  to connect the ropes into one is 16 + 33 + 133 = 182.
```
```java
public class Solution {
    public int solve(int[] A) {
        //
        PriorityQueue<Integer> pq = new PriorityQueue<Integer>();
        //
        for(int i = 0; i < A.length; i++) {
            pq.add(A[i]);
        }
        //
        int sum = 0;
        while(pq.size() > 1) {
            int minA = pq.poll();
            int minB = pq.poll();
            int mySum = minA + minB;
            //
            pq.add(mySum);
            sum += mySum;
        }
        //
        return sum;
    }
}
```

**Q2. Build a Heap**

**Problem Description**
```
Given an array A of N integers, convert that array into a min heap and return the array.

NOTE: A min heap is a binary tree where every node has a value less than or equal to its children.
```
**Problem Constraints**

```swift
1 ≤ N ≤ 105

0 ≤ A[i] ≤ 109
```

**Input Format**

```
First and only argument of input contains a single integer array A of length N.
```

**Output Format**

```
Return the reordered array A such that it forms a min heap.
```

**Example Input**
```
Input:
A = [5, 13, -2, 11, 27, 31, 0, 19]
```
**Example Output**
```
Output:

A = [-2, 5, 0, 13, 11, 19, 27, 31]
```
**Example Explanation**

```
One possible Heap is
  
                -2
               /    \
             5       0
            / \    /  \
          13  11  19   27
          /
        31

It can be seen that each parent has a value smaller than its children. Hence it is a Valid Heap.

The Heap in the Array format is [-2, 5, 0, 13, 11, 19, 27, 31].

Some more possible heaps are  [-2, 0, 5, 13, 11, 27, 19, 31], [-2, 5, 0, 11, 27, 13, 19, 31], etc. 
You can return any possible Valid Heap Structure.
```

**Solution:**

```
class Solution {
    public int[] buildHeap(int[] A) {
        //
        int n = A.length;
        //
        for(int i = n/2 - 1; i >= 0; i--) {
            heapify(A, n, i);
        }
        //
        return A;
    }

    void heapify(int[] A, int n, int i) {
        int smallest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;
        //
        if (left < n && A[left] < A[smallest]) {
            smallest = left;
        }
        //
        if (right < n && A[right] < A[smallest]) {
            smallest = right;
        }
        //
        if (smallest != i) {
            // Swap Now
            int temp = A[smallest];
            A[smallest] = A[i];
            A[i] = temp;
            heapify(A, n, smallest);
        }
    }
}
```








