# String to Integer (atoi)

**Date:** 2026-05-18  
**Difficulty:** 🟡 **Medium**  
**Tags:** `String`

## Problem Description

Implement the myAtoi(string s) function, which converts a string to a 32-bit signed integer. The algorithm for myAtoi(string s) is as follows: Whitespace : Ignore any leading whitespace ( &quot; &quot; ). Signedness : Determine the sign by checking if the next character is &#39;-&#39; or &#39;+&#39; , assuming positivity if neither present. Conversion : Read the integer by skipping leading zeros until a non-digit character is encountered or the end of the string is reached. If no digits were read, then the result is 0. Rounding : If the integer is out of the 32-bit signed integer range [-2 31 

[LeetCode Link](https://leetcode.com/problems/string-to-integer-atoi)

## Approach

Unknown

> Analysis unavailable

## Solution Logic

1. Could not analyze solution

## Complexity Analysis

| Complexity | Analysis |
|------------|----------|
| **Time:** | Unknown |
| **Space:** | Unknown |

## Edge Cases Handled

None specified

## What I Learned

AI analysis failed — solution still committed to GitHub

## Similar Problems

None suggested

## Solution Code

```text
#include <iostream>
#include <string>
using namespace std;

class Solution {
public:
    int myAtoi(string s) {
        int i = 0, sign = 1;
        long res = 0; // Using long to handle overflow cases

        // Trim leading spaces
        while (i < s.size() && s[i] == ' ') i++;
        if (i == s.size()) return 0;

        // Check for sign
        if (s[i] == '-') { sign = -1; i++; }
        else if (s[i] == '+') i++;

        // Process numerical characters
        while (i < s.size() && isdigit(s[i])) {
            res = res * 10 + (s[i] - '0');

            // Handle overflow
            if (sign * res > INT_MAX) return INT_MAX;
            if (sign * res < INT_MIN) return INT_MIN;

            i++;
        }

        return (int)(sign * res);
    }
};
```
