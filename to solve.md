Problem Statement
This message will be auto-pinned
Given two strings, str1, and str2, where str1 contains exactly one character more than str2, find the indices of the characters in str1 that can be removed to make str1 equal to str2. Return the array of indices in increasing order. If it is not possible, return the array [-1]. 

Note: Use 0-based indexing.

Example

str1 = "abdgggda"

str2 = "abdggda"

Any "g" character at positions 3, 4, or 5 can be deleted to obtain str2. Return [3, 4, 5].

Input Format
Function Description

Complete the function getRemovableIndices in the editor below.

getRemovableIndices has the following parameters:

string str1: the string to modify

string str2: the target string

Output Format
Output Format

     int[]: the indices of characters that can be removed from str1 in ascending order, or [-1] if it is not possible to match str2

Constraints
Constraints

2 ≤ |str1| ≤ 2 * 10^5

1 ≤ |str2| ≤ 2 * 10^5

|str1| = |str2| + 1 

str1 and str2 only contain lowercase English letters.
