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


# ----------------------------------------------------
# Time Complexity Summary:
# ----------------------------------------------------
# Dictionary (insert/search/delete)     O(1) average
# LC #1 Two Sum                         O(n)
# ----------------------------------------------------
