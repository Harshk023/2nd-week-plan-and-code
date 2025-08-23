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



# ----------------------------------------------------
# Time Complexity Summary:
# ----------------------------------------------------
# Dictionary (insert/search/delete)     O(1) average
# LC #1 Two Sum                         O(n)
# ----------------------------------------------------
