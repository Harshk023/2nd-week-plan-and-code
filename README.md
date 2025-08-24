🚀 2nd-Week-Plan-and-Code
A structured 7-day roadmap covering Hashing, Sliding Window, and Linked Lists. Includes theory notes, clean Python code snippets, and LeetCode problem solutions to strengthen problem-solving skills.

📅 Day-Wise Plan

| Day        | Focus Area & Questions                                                                                                                                                   |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Day 8**  | **Hashmap Basics** – Introduction to hashing, dictionary operations in Python <br> LeetCode #1 – Two Sum                                                                 |
| **Day 9**  | **Subarray Sums with Hashmap** <br> LeetCode #560 – Subarray Sum Equals K                                                                                                |
| **Day 10** | **Sliding Window Basics** – Fixed & variable size windows <br> LeetCode #3 – Longest Substring Without Repeating Characters <br> LeetCode #76 – Minimum Window Substring |
| **Day 11** | **Linked List Basics** – Implement a singly linked list (insert, delete, traverse)                                                                                       |
| **Day 12** | **Classic Linked List Problems** <br> LeetCode #206 – Reverse Linked List <br> LeetCode #141 – Linked List Cycle                                                         |
| **Day 13** | **Merging Lists** <br> LeetCode #21 – Merge Two Sorted Lists                                                                                                             |
| **Day 14** | **Mixed Practice** – 5–6 easy-medium problems (Hashmaps + Linked Lists)                                                                                                  |


"""
Day 8: Hashmap Intro & Two Sum Problem
Author: [Your Name]
Date: [Today's Date]

Topics Covered:
1. Introduction to Hashmaps (Dictionaries in Python)
2. LeetCode #1 - Two Sum
"""

# ----------------------------------------------------
# 1. Introduction to Hashmaps in Python
# ----------------------------------------------------
"""
Hashmap (Dictionary in Python) = Key -> Value storage.

Features:
- Insert, delete, lookup are O(1) on average.
- Useful for fast lookups and frequency counts.
"""

# Example: Storing student marks
marks = {"Alice": 85, "Bob": 92, "Charlie": 78}
print("Marks dictionary:", marks)
print("Bob's marks:", marks["Bob"])

# Adding/updating values
marks["David"] = 88
marks["Alice"] = 90
print("Updated dictionary:", marks)

# Checking if a key exists
print("Is 'Charlie' in marks?", "Charlie" in marks)


# ----------------------------------------------------
# 2. LeetCode #1 - Two Sum
# ----------------------------------------------------
"""
Problem:
Given an array of integers nums and an integer target,
return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution,
and you may not use the same element twice.

Example:
Input: nums = [2,7,11,15], target = 9
Output: [0,1]

Approach:
- Use a hashmap to store (value -> index).
- For each number, check if target - num exists in hashmap.
- If yes, return the indices.

Time Complexity: O(n)
Space Complexity: O(n)
"""

def twoSum(nums, target):
    hashmap = {}  # value -> index
    for i, num in enumerate(nums):
        complement = target - num
        if complement in hashmap:
            return [hashmap[complement], i]
        hashmap[num] = i
    return []

nums_1 = [2, 7, 11, 15]
target_1 = 9
print("LC #1 Input:", nums_1, "Target:", target_1)
print("LC #1 Output:", twoSum(nums_1, target_1))  # [0, 1]

# Another test
nums_1b = [3, 2, 4]
target_1b = 6
print("LC #1 Input:", nums_1b, "Target:", target_1b)
print("LC #1 Output:", twoSum(nums_1b, target_1b))  # [1, 2]

"""
Day 9: Subarray Sum with Hashmap
Author: [Your Name]
Date: [Today's Date]

Topics Covered:
1. Subarray sum basics
2. LeetCode #560 - Subarray Sum Equals K
"""

# ----------------------------------------------------
# 1. Subarray Sum Basics
# ----------------------------------------------------
"""
A subarray is a contiguous part of an array.

Brute Force:
- Check all subarrays and calculate sums.
- Time Complexity: O(n^2), not efficient.

Optimization using Hashmap:
- Use prefix sum + hashmap to store frequency of prefix sums.
- If prefix_sum - k exists in hashmap, it means there is a subarray
  ending at current index with sum = k.
"""

# ----------------------------------------------------
# 2. LeetCode #560 - Subarray Sum Equals K
# ----------------------------------------------------
"""
Problem:
Given an array of integers nums and an integer k,
return the total number of subarrays whose sum equals to k.

Example 1:
Input: nums = [1,1,1], k = 2
Output: 2

Example 2:
Input: nums = [1,2,3], k = 3
Output: 2

Approach:
- Maintain prefix_sum while iterating.
- Use hashmap to store frequency of prefix sums.
- For each prefix_sum, check if (prefix_sum - k) exists in hashmap.
- Add its frequency to count.

Time Complexity: O(n)
Space Complexity: O(n)
"""

def subarraySum(nums, k):
    prefix_sum = 0
    count = 0
    hashmap = {0: 1}  # To handle case when prefix_sum itself == k
    
    for num in nums:
        prefix_sum += num
        if prefix_sum - k in hashmap:
            count += hashmap[prefix_sum - k]
        hashmap[prefix_sum] = hashmap.get(prefix_sum, 0) + 1
    
    return count

# Example tests
nums_560a = [1, 1, 1]
k_560a = 2
print("LC #560 Input:", nums_560a, "k =", k_560a)
print("LC #560 Output:", subarraySum(nums_560a, k_560a))  # Output: 2

nums_560b = [1, 2, 3]
k_560b = 3
print("LC #560 Input:", nums_560b, "k =", k_560b)
print("LC #560 Output:", subarraySum(nums_560b, k_560b))  # Output: 2


# ----------------------------------------------------
# Time Complexity Summary:
# ----------------------------------------------------
# Brute Force:        O(n^2)
# Optimized (Hashmap) O(n)
# ----------------------------------------------------


"""
Day 10: Sliding Window Basics
Author: [Your Name]
Date: [Today's Date]

Topics Covered:
1. Introduction to Sliding Window
2. LeetCode #3 - Longest Substring Without Repeating Characters
3. LeetCode #76 - Minimum Window Substring
"""

# ----------------------------------------------------
# 1. Sliding Window Basics
# ----------------------------------------------------
"""
Sliding Window is a technique where we use a "window" (a range of indices)
that expands and contracts to solve substring/subarray problems efficiently.

Use cases:
- Substrings without duplicates
- Subarrays with given sum
- Minimum/maximum subarray problems
"""

# Simple Example: Max sum of subarray of size k
def max_sum_subarray(nums, k):
    window_sum = sum(nums[:k])
    max_sum = window_sum
    
    for i in range(k, len(nums)):
        window_sum += nums[i] - nums[i-k]
        max_sum = max(max_sum, window_sum)
    return max_sum

print("Max sum subarray of size 3:", max_sum_subarray([1,2,3,4,5,6], 3))


# ----------------------------------------------------
# 2. LeetCode #3 - Longest Substring Without Repeating Characters
# ----------------------------------------------------
"""
Problem:
Given a string s, find the length of the longest substring
without repeating characters.

Example:
Input: "abcabcbb"
Output: 3 ("abc")

Approach:
- Use sliding window + hashmap to store last index of characters.
- Move left pointer whenever a duplicate is found.

Time Complexity: O(n)
"""

def lengthOfLongestSubstring(s):
    char_index = {}
    left = 0
    max_len = 0
    
    for right, ch in enumerate(s):
        if ch in char_index and char_index[ch] >= left:
            left = char_index[ch] + 1
        char_index[ch] = right
        max_len = max(max_len, right - left + 1)
    
    return max_len

print("LC #3 Input: 'abcabcbb'")
print("LC #3 Output:", lengthOfLongestSubstring("abcabcbb"))  # 3


# ----------------------------------------------------
# 3. LeetCode #76 - Minimum Window Substring
# ----------------------------------------------------
"""
Problem:
Given two strings s and t, return the minimum window substring of s
such that every character in t is included in the window.
If no such substring exists, return "".

Example:
Input: s = "ADOBECODEBANC", t = "ABC"
Output: "BANC"

Approach:
- Use sliding window + two pointers.
- Expand right pointer until all chars from t are covered.
- Then shrink left pointer to minimize the window.
- Use hashmap for frequency count.

Time Complexity: O(n)
"""

from collections import Counter

def minWindow(s, t):
    if not t or not s:
        return ""
    
    need = Counter(t)
    window = {}
    
    have, need_count = 0, len(need)
    res, res_len = [-1, -1], float("inf")
    
    left = 0
    for right, ch in enumerate(s):
        window[ch] = window.get(ch, 0) + 1
        
        if ch in need and window[ch] == need[ch]:
            have += 1
        
        while have == need_count:
            # Update result if smaller window
            if (right - left + 1) < res_len:
                res = [left, right]
                res_len = right - left + 1
            
            # Pop from left
            window[s[left]] -= 1
            if s[left] in need and window[s[left]] < need[s[left]]:
                have -= 1
            left += 1
    
    l, r = res
    return s[l:r+1] if res_len != float("inf") else ""

print("LC #76 Input: s = 'ADOBECODEBANC', t = 'ABC'")
print("LC #76 Output:", minWindow("ADOBECODEBANC", "ABC"))  # "BANC"


# ----------------------------------------------------
# Time Complexity Summary:
# ----------------------------------------------------
# Max sum subarray (fixed window)        O(n)
# LC #3 Longest substring (variable)     O(n)
# LC #76 Minimum window substring        O(n)
# ----------------------------------------------------

# ----------------------------------------------------
# Time Complexity Summary:
# ----------------------------------------------------
# Dictionary (insert/search/delete)     O(1) average
# LC #1 Two Sum                         O(n)
# ----------------------------------------------------
