# Zigzag Conversion

**Date:** 2026-05-18  
**Difficulty:** 🟡 **Medium**  
**Tags:** `String`

## Problem Description

The string &quot;PAYPALISHIRING&quot; is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility) P A H N A P L S I I G Y I R And then read line by line: &quot;PAHNAPLSIIGYIR&quot; Write the code that will take a string and make this conversion given a number of rows: string convert(string s, int numRows); Example 1: Input: s = &quot;PAYPALISHIRING&quot;, numRows = 3 Output: &quot;PAHNAPLSIIGYIR&quot; Example 2: Input: s = &quot;PAYPALISHIRING&quot;, numRows = 4 Output: &quot;PINALSIGYAHRPI&quot; Explanation: 

[LeetCode Link](https://leetcode.com/problems/zigzag-conversion)

## Approach

Zigzag Pattern Iteration

> Convert string to zigzag pattern and read line by line

## Solution Logic

1. Initialize character array
2. Iterate over each row
3. Fill character array with characters from string in zigzag order

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | O(n) — where n is the length of the string, because we are iterating over the string once |
| **Space:** | O(n) — where n is the length of the string, because we are storing the result in a character array of the same length |

## Edge Cases Handled

- Single row
- Empty string

## What I Learned

How to convert a string to a zigzag pattern and read it line by line, and how to handle edge cases like single row or empty string

## Similar Problems

- Reverse String
- Rotate Array

## Solution Code

```text
class Solution {
public:
    string convert(string s, int numRows) {
        if (numRows == 1) return s;
        char a[10000];
        std::size_t len = s.length();
        int index =0;
        for (int i = 0; i < numRows; i++) {
            for (int j = i; j < len; j +=2*(numRows-1)) {
                a[index++] = s[j];
                if (i > 0 && i<numRows-1 && j+2*(numRows-1)-2*i<len) {
                    a[index++] = s[j + 2*(numRows - 1)-2*i];
                }
            }
        }
        a[index]='\0';
        return a;
    }
};
```
