# Subsets (Power Set) – Java Backtracking Solution

## 📌 Problem Statement

Given an integer array `nums` of unique elements, return all possible subsets (the power set).

The solution set must not contain duplicate subsets.  
The order of output does not matter.

---

## 🚀 Approach

We use the **Backtracking (Include / Exclude)** technique.

At every index, we have two choices:
1. Include the current element
2. Exclude the current element

This generates `2^n` subsets.

---

## 🧠 Algorithm Steps

1. Start with an empty list.
2. At each index:
   - Add the element to the current subset.
   - Recurse to the next index.
   - Remove the element (backtrack).
   - Recurse without including the element.
3. When index reaches `nums.length`, add the current subset to result.

---

## 💻 Java Implementation

```java
import java.util.*;

class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> list = new ArrayList<>();
        Sets(new ArrayList<>(), nums, 0, list);
        return list;
    }

    public void Sets(List<Integer> ans, int[] nums, int idx, List<List<Integer>> list) {
        if (idx == nums.length) {
            list.add(new ArrayList<>(ans));
            return;
        }

        // Include
        ans.add(nums[idx]);
        Sets(ans, nums, idx + 1, list);

        // Backtrack
        ans.remove(ans.size() - 1);

        // Exclude
        Sets(ans, nums, idx + 1, list);
    }
}
⏱ Time Complexity
O(2^n)

Each element has two choices → Include or Exclude.

📦 Space Complexity
O(n)

Recursive stack depth = n

✅ Example

Input:

nums = [1,2,3]

Output:

[]
[1]
[2]
[3]
[1,2]
[1,3]
[2,3]
[1,2,3]
🔥 Key Concept

Backtracking requires:

add → recurse → remove

Without removing (backtracking), results will be incorrect.

📚 Topics Covered

Recursion

Backtracking

Power Set

Combinatorics

👨‍💻 Author

Sanjeev Sharma
Java & DSA Enthusiast 🚀
