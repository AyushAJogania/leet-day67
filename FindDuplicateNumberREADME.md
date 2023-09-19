# leet-day67

# Find the Duplicate Number

## Problem Description

Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive. There is only one repeated number in `nums`, return this repeated number.

You must solve the problem without modifying the array `nums` and use only constant extra space.

### Example 1:

**Input**: `nums = [1,3,4,2,2]`  
**Output**: `2`

### Example 2:

**Input**: `nums = [3,1,3,4,2]`  
**Output**: `3`

### Constraints:

- `1 <= n <= 10^5`
- `nums.length == n + 1`
- `1 <= nums[i] <= n`
- All the integers in `nums` appear only once except for precisely one integer which appears two or more times.

## Approach and Algorithm

To solve this problem efficiently, we can use the **Floyd's Tortoise and Hare** algorithm, also known as cycle detection algorithm. This algorithm is used to detect cycles in linked lists but can be adapted to find duplicate elements in an array.

The key idea is to view the array as a linked list, where each element `nums[i]` represents the next index to jump to (i.e., `nums[nums[i]]` is the next node in the linked list). Since there is exactly one repeated number, there will be a cycle in this linked list.

Here's a step-by-step explanation of the algorithm:

1. Initialize two pointers, `slow` and `fast`, both starting from the first element of the array.

2. In **Phase 1**, advance `slow` by one step and `fast` by two steps in each iteration until they meet at the intersection point inside the cycle. This phase guarantees that they will meet inside the cycle.

3. In **Phase 2**, reset one of the pointers, either `slow` or `fast`, to the beginning of the array, and keep the other pointer at the intersection point. Advance both pointers by one step at a time until they meet again. The point at which they meet is the entrance to the cycle.

4. Return the duplicate element, which is the same as the value at the meeting point of `slow` and `fast` in **Phase 2**.

The time complexity of this algorithm is linear, O(n), as it makes two passes through the array, and it uses only constant extra space, O(1).

## How to Use

You can use the provided C++ code to find the duplicate number in an array. Simply pass your input array `nums` to the `findDuplicate` function, and it will return the duplicate number.

```cpp
int findDuplicate(vector<int>& nums) {
    // Implementation of Floyd's Tortoise and Hare Algorithm
    // ...
}
```

## Follow-up Questions

1. **How can we prove that at least one duplicate number must exist in nums?**

   The problem statement guarantees that there is exactly one repeated number in `nums`. To prove this, we can use the Pigeonhole Principle. If there are `n` distinct values in the range `[1, n]`, then there are `n` pigeonholes (possible values), but there are `n + 1` pigeons (numbers in `nums`). Therefore, at least one pigeonhole must contain more than one pigeon, implying the existence of a duplicate number.

2. **Can you solve the problem in linear runtime complexity?**

   Yes, the provided algorithm solves the problem in linear runtime complexity, O(n), making it an efficient solution for large input arrays.
