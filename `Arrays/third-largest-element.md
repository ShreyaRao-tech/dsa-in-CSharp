# Third Largest Element in an Array

**Topic:** Arrays
**Difficulty:** Easy

## Problem
Given an array of positive integers, find the third largest element. Return -1 if fewer than 3 elements exist. Duplicate values count toward filling the largest/second-largest/third-largest positions (e.g. [5,5,5] returns 5).
https://www.geeksforgeeks.org/problems/third-largest-element/1
## Approach
Single pass, tracking three running values: `largest`, `slargest`, `tlargest`. For each element, check top-down: if it beats `largest`, shift everything down one slot; else if it beats `slargest`, shift down into third; else if it beats `tlargest`, it takes the third slot directly. An upfront length check (`< 3`) handles the -1 case. No sorting needed.

## Code (C#)
```csharp
public class Solution {
    public int ThirdLargest(int[] arr) {
        if (arr.Length < 3)
        {
            return -1;
        }
        
        int largest = int.MinValue;
        int slargest = int.MinValue;
        int tlargest = int.MinValue;
        
        for (int i = 0; i < arr.Length; i++)
        {
            if (arr[i] > largest)
            {
                tlargest = slargest;
                slargest = largest;
                largest = arr[i];
            }
            else if (arr[i] > slargest)
            {
                tlargest = slargest;
                slargest = arr[i];
            }
            else if (arr[i] > tlargest)
            {
                tlargest = arr[i];
            }
        }
        
        return tlargest;
    }
}
```

## Complexity
- Time: O(n) — single pass
- Space: O(1) — three extra variables only

