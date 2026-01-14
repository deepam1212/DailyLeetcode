**Finish Maximum Jobs**


**Problem Description**
```swift
There are N jobs to be done, but you can do only one job at a time.

Given an array A denoting the start time of the jobs and an array B denoting the finish time of the jobs.

Your aim is to select jobs in such a way so that you can finish the maximum number of jobs.

Return the maximum number of jobs you can finish.
```
**Problem Constraints**

```swift
1 <= N <= 105

1 <= A[i] < B[i] <= 109
```

**Input Format**

```swift
The first argument is an integer array A of size N, denoting the start time of the jobs.
The second argument is an integer array B of size N, denoting the finish time of the jobs.
```

**Output Format**

```swift
Return an integer denoting the maximum number of jobs you can finish.
```

**Example Input**

```swift
Input 1:

 A = [1, 5, 7, 1]
 B = [7, 8, 8, 8]
Input 2:

 A = [3, 2, 6]
 B = [9, 8, 9]
```

**Example Output**

```swift
Output 1:

 2
Output 2:

 1
```

**Example Explanation**

```swift
Explanation 1:

 We can finish the job in the period of time: (1, 7) and (7, 8).

Explanation 2:

 Since all three jobs collide with each other. We can do only 1 job.
```

```swift
import Foundation

class Solution {
	func solve(_ A: inout [Int], _ B: inout [Int]) -> Int {
        let n: Int = A.count
        if n == 0 {return 0}
        //
        var jobs = Array(repeating: Array(repeating: 0, count: 2), count: n)
        //
        for i in 0..<n {
            jobs[i][0] = A[i]
            jobs[i][1] = B[i]
        }
        //
        jobs.sort{$0[1] < $1[1]}
        //
        var count: Int = 1
        var last = jobs[0][1]
        //
        for index in 1..<n {
            if jobs[index][0] >= last {
                count += 1
                last = jobs[index][1]
            }
        }
        //
        return count
	}
}
```
**Seats**

**Problem Description**
```swift
There is a row of seats represented by string A. Assume that it contains N seats adjacent to each other.
There is a group of people who are already seated in that row randomly. i.e. some are sitting together & some are scattered.
An occupied seat is marked with a character 'x' and an unoccupied seat is marked with a dot ('.')

Now your target is to make the whole group sit together i.e. next to each other, without having any vacant seat between them in such a way that the total number of hops or jumps to move them should be minimum.

In one jump a person can move to the adjacent seat (if available).

NOTE: 1. Return your answer modulo 107 + 3.
```
**Problem Constraints**
```swift
1 <= N <= 1000000
A[i] = 'x' or '.'
```
**Input Format**
```swift
The first and only argument is a string A of size N.
```

**Output Format**

```swift
Return an integer denoting the minimum number of jumps required.
```

**Example Input**

```swift
Input 1:

 A = "....x..xx...x.."
Input 2:

 A = "....xxx"
```

**Example Output**

```swift
Output 1:

 5
Output 2:

 0
```

**Example Explanation**

```swift
Explanation 1:

 Here is the row having 15 seats represented by the String (0, 1, 2, 3, ......... , 14) 
                 . . . . x . . x x . . . x . . 
 Now to make them sit together one of approaches is -
                 . . . . . . x x x x . . . . .
 Steps To achieve this:
 1) Move the person sitting at 4th index to 6th index: Number of jumps by him =   (6 - 4) = 2
 2) Bring the person sitting at 12th index to 9th index: Number of jumps by him = (12 - 9) = 3
 So, total number of jumps made: 2 + 3 = 5 which is the minimum possible.

 If we other ways to make them sit together but the number of jumps will exceed 5 and that will not be minimum.
 
Explanation 2:

 They are already together. So, the cost is zero.
```

```swift
import Foundation

class Solution {
	func seats(_ A: inout String) -> Int {
        let mod = 10000003
        var positions: [Int] = []
        var charArr: [Character] = Array(A)
        //
        for (index, item) in charArr.enumerated() {
            if item == "x" {
                positions.append(index)
            }
        }
        //
        let n = positions.count
        if n == 0 {return 0}
        let mid = n / 2
        let medianSeat = positions[mid]
        var moves: Int = 0
        //
        for i in 0..<n {
            let target = medianSeat - (mid - i)
            moves += abs(positions[i] - target)
        }
        //
        return moves % mod
	}
}
```

**Q1. Running Median**

**Problem Description**

```java
Flipkart is currently dealing with the difficulty of precisely estimating and displaying the expected delivery time for orders to a specific pin code. The existing method relies on historical delivery time data for that pin code, using the median value as the expected delivery time. As the order history expands with new entries, Flipkart aims to enhance this process by dynamically updating the expected delivery time whenever a new delivery time is added. The objective is to find the expected delivery time after each new element is incorporated into the list of delivery times. End Goal: With every addition of new delivery time, requirement is to find the median value.

Why Median ? The median is calculated because it provides a more robust measure of the expected delivery time The median is less sensitive to outliers or extreme values than the mean. In the context of delivery times, this is crucial because occasional delays or unusually fast deliveries (outliers) can skew the mean significantly, leading to inaccurate estimations.


Given an array of integers, A denoting the delivery times for each order. New arrays of integer B and C are formed, each time a new delivery data is encountered, append it at the end of B and append the median of array B at the end of C. Your task is to find and return the array C.

NOTE:

If the number of elements is N in B and N is odd, then consider the median as B[N/2] ( B must be in sorted order).
If the number of elements is N in B and N is even, then consider the median as B[N/2-1]. ( B must be in sorted order).
```
**Problem Constraints**

```java
1 <= length of the array <= 100000
1 <= A[i] <= 109
```

**Input Format**

```java
The only argument given is the integer array A.
```

**Output Format**

```java
Return an integer array C, C[i] denotes the median of the first i delivery times.
```

**Example Input**

```java
Input 1:

 A = [1, 2, 5, 4, 3]
Input 2:

 A = [5, 17, 100, 11]
```

**Example Output**

```java
Output 1:

 [1, 1, 2, 2, 3]
Output 2:

 [5, 5, 17, 11]
```

**Example Explanation**

```java
Explanation 1:



 Delivery Times      median
 [1]                   1
 [1, 2]                1
 [1, 2, 5]             2 
 [1, 2, 5, 4]          2
 [1, 2, 5, 4, 3]       3
Explanation 2:

 Delivery Times     median
 [5]                  5
 [5, 17]              5
 [5, 17, 100]         17
 [5, 17, 100, 11]     11 
```

```java
public class Solution {
    public int[] solve(int[] A) {
        //
        PriorityQueue<Integer> maxHeap = new PriorityQueue<Integer>(Collections.reverseOrder());
        PriorityQueue<Integer> minHeap = new PriorityQueue<Integer>();
        //
        ArrayList<Integer> result = new ArrayList<Integer>();
        //
        for(int num: A) {
            if (maxHeap.isEmpty() || num <= maxHeap.peek()) {
                maxHeap.add(num);
            } else {
                minHeap.add(num);
            }
            //
            if (maxHeap.size() > minHeap.size() + 1) {
                minHeap.add(maxHeap.poll());
            } else if (minHeap.size() > maxHeap.size()) {
                maxHeap.add(minHeap.poll());
            }
            //
            result.add(maxHeap.peek());
        }
        //
        int[] output = new int[result.size()];
        //
        for(int i = 0; i < result.size(); i++) {
            output[i] = result.get(i);
        }
        //
        return output;
    }
}
```


















