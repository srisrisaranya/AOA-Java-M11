
# EX 1D Sorted Array using Divide and Conquer Approach.
## DATE:
## AIM:
To write a Java program to for given constraints.
Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.

The overall run time complexity should be O(log (m+n)).

## Algorithm

1. Start the program and read the sizes and elements of two sorted arrays, nums1[] and nums2[].

2.Initialize two pointers p1 = 0 and p2 = 0 to traverse both arrays.

3.Merge conceptually:

Use a helper method getMin() to return the smaller of nums1[p1] and nums2[p2], moving the corresponding pointer forward.

Continue calling getMin() until reaching the middle position(s) of the combined sorted sequence.

4.Check the total length (m + n):

If even, take the average of the two middle elements as the median.

If odd, take the middle element as the median.

5.Display the median and stop the program. 

## Program:
```
/*
Program to implement Reverse a String
Developed by: SARANYA S
Register Number: 212223110044 
*/
```
```
import java.util.Scanner;

public class Solution {
    private int p1 = 0, p2 = 0;

    // Get the smaller value between nums1[p1] and nums2[p2], and move the pointer forward
    private int getMin(int[] nums1, int[] nums2) {
        if (p1 < nums1.length && p2 < nums2.length) {
            return nums1[p1] < nums2[p2] ? nums1[p1++] : nums2[p2++];
        } else if (p1 < nums1.length) {
            return nums1[p1++];
        } else if (p2 < nums2.length) {
            return nums2[p2++];
        }
        return -1; // Should not reach here if input is valid
    }

    // Main logic to find median of two sorted arrays
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
       //Type code here...
       
    int m = nums1.length, n = nums2.length;
    int total = m + n;
    int[] merged = new int[total];
    int i = 0, j = 0, k = 0;

    // Merge the two sorted arrays
    while (i < m && j < n) {
        if (nums1[i] <= nums2[j]) {
            merged[k++] = nums1[i++];
        } else {
            merged[k++] = nums2[j++];
        }
    }
    while (i < m) {
        merged[k++] = nums1[i++];
    }
    while (j < n) {
        merged[k++] = nums2[j++];
    }

    // Find the median
    if (total % 2 == 1) {
        return merged[total / 2];   // odd length → middle element
    } else {
        return (merged[total / 2 - 1] + merged[total / 2]) / 2.0;  // even length → average of two middle
    }

    }

    // Main method with user input
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        // Input for nums1
        
        int m = sc.nextInt();
        int[] nums1 = new int[m];
        
        for (int i = 0; i < m; i++) {
            nums1[i] = sc.nextInt();
        }

        // Input for nums2
        
        int n = sc.nextInt();
        int[] nums2 = new int[n];
        
        for (int i = 0; i < n; i++) {
            nums2[i] = sc.nextInt();
        }

        // Find and display the median
        double median = sol.findMedianSortedArrays(nums1, nums2);
        System.out.println("Median of the two sorted arrays = " + median);
        
        sc.close();
    }
}

```

## Output:
<img width="903" height="366" alt="image" src="https://github.com/user-attachments/assets/97693284-4d2a-4247-82cd-d05f250a5bb7" />



## Result:
The program successfully implemented and the expected output is verified.
