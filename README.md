# Is Subsequence
LeetCode

# Question:

Given two strings s and t, return true if s is a subsequence of t, or false otherwise.

A subsequence of a string is a new string that is formed from the original string by deleting some (can be none) of the characters without disturbing the relative positions of the remaining characters. (i.e., "ace" is a subsequence of "abcde" while "aec" is not).

 

Example 1:

Input: s = "abc", t = "ahbgdc"
Output: true
Example 2:

Input: s = "axc", t = "ahbgdc"
Output: false

# Ans:

# Two-Pointer Approach (Optimal)

We use two pointers:

i → scans s

j → scans t

Algorithm:

Start with both at 0.

Move j through t.

If s[i] == t[j], move i forward.

Always move j forward.

At the end, if i == len(s), all characters in s were matched in order.

Code (Python)
class Solution:
    def isSubsequence(self, s: str, t: str) -> bool:
        i, j = 0, 0
        
        while i < len(s) and j < len(t):
            if s[i] == t[j]:
                i += 1
            j += 1
        
        return i == len(s)

Dry Run

s = "abc", t = "ahbgdc"

i=0, j=0 → s[0]="a", t[0]="a" → match → i=1, j=1

i=1, j=1 → s[1]="b", t[1]="h" → not match → j=2

i=1, j=2 → s[1]="b", t[2]="b" → match → i=2, j=3

i=2, j=3 → s[2]="c", t[3]="g" → not match → j=4

i=2, j=4 → s[2]="c", t[4]="d" → not match → j=5

i=2, j=5 → s[2]="c", t[5]="c" → match → i=3, j=6

Now i=3 = len(s) → ✅ True.