# Check if Array is Sorted

**Topic:** Arrays
**Difficulty:** Easy

## Problem
Given an array of integers, determine whether it is sorted in non-decreasing order.

## Approach
Single pass through the array, comparing each element to its predecessor. If any element is smaller than the one before it, the array isn't sorted — return false immediately. If the loop completes without finding a violation, the array is sorted.
https://www.geeksforgeeks.org/problems/check-if-an-array-is-sorted0701/1
## Code (C#)
```csharp
public class Solution {
    public bool IsSorted(int[] arr) {
        for (int i = 1; i < arr.Length; i++)
        {
            if (arr[i] < arr[i-1])
            {
                return false;
            }
        }
        return true;
    }
}
```

## Complexity
- Time: O(n) — single pass, early exit on first violation
- Space: O(1) — no extra space used

## Notes
- Uses non-strict comparison (`<`), so equal adjacent elements (e.g. [1,2,2,3]) are still considered sorted — adjust to `<=` if strictly increasing is required instead
- Early return on the first violation avoids unnecessary work once the array is known to be unsorted
