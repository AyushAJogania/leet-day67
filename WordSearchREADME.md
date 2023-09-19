# leet-day67

# README: Word Search on a 2D Grid

## Problem Description

You are given an `m x n` grid of characters, and a string `word`. Your task is to determine if the given word can be constructed by sequentially adjacent cells in the grid, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.

You need to implement the `exist` function that takes the following parameters:

- `board`: A 2D grid of characters, represented as a vector of vectors of characters.
- `word`: The target word, represented as a string.

The function should return `true` if the word exists in the grid, otherwise `false`.


## Solution Approach

The problem can be solved using a backtracking algorithm. The idea is to start searching for the first character of the word in the grid and then explore adjacent cells to find the remaining characters while backtracking when encountering a dead-end.

Here's a step-by-step overview of the solution approach:

1. Iterate through the entire grid to find the first character of the word. When a match is found, call the `backtrack` function to search for the rest of the characters starting from that position.

2. In the `backtrack` function, handle the following base cases:
   - If the end of the word is reached, return `true`, indicating that the entire word has been found.
   - If the current position is out of bounds or the character at that position doesn't match the current character of the word, return `false`, indicating a mismatch.

3. If none of the base cases are met, proceed with the search:
   - Temporarily save the current character.
   - Mark the current cell as visited (using a marker character, such as '#').
   - Recursively explore adjacent cells in all four directions (up, down, left, and right) to find the next character of the word.

4. After exploring all possible paths, restore the original character in the cell (backtrack) and return `true` if the word has been found, or `false` if not.

The backtracking algorithm efficiently searches for the word in the grid, pruning paths that lead to dead-ends. The time complexity of this solution is `O(m * n * 4^k)`, where `k` is the length of the word, and the `4^k` factor accounts for exploring all four directions at each step. The space complexity is `O(k)` due to the recursion stack.

