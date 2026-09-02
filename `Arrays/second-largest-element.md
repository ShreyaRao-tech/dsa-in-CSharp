# Second Largest Element in an Array

**Topic:** Arrays
**Difficulty:** Easy

## Problem
Given an array of integers, find and return the second largest distinct element. If no such element exists (array has fewer than 2 elements, or all elements are identical), return -1.
https://takeuforward.org/plus/dsa/problems/second-largest-element
## Approach
Single pass, tracking two values: `largest` and `slargest` (second largest). For each element: if it's greater than `largest`, the old `largest` becomes the new `slargest`, and this element becomes the new `largest`. Otherwise, if it's less than `largest` but greater than the current `slargest`, it becomes the new `slargest`. No sorting needed.

## Code (C#)
```csharp
public class Solution {
    public int SecondLargestElement(List<int> nums) {
        int largest = nums[0];
        int slargest = int.MinValue;
        
        for (int i = 1; i < nums.Count; i++)
        {
            if (nums[i] > largest)
            {
                slargest = largest;
                largest = nums[i];
            }
            else if (nums[i] < largest && nums[i] > slargest)
            {
                slargest = nums[i];
            }
        }
        
        return slargest == int.MinValue ? -1 : slargest;
    }
}
```

## Complexity
- Time: O(n) — single pass
- Space: O(1) — two extra variables only

