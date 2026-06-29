# Top 20 Sliding Window Problems (FAANG Roadmap)

> **Goal:** These 20 problems cover almost every major Sliding Window concept asked in coding interviews. Master them by understanding the window movement, not by memorizing the solutions.

---

# 🟢 Level 1 — Fixed Size Window

Learn how to build and slide a constant-size window.

| # | Problem                                         | Difficulty | Main Idea                      | Link                                                                           |
| - | ----------------------------------------------- | ---------- | ------------------------------ | ------------------------------------------------------------------------------ |
| 1 | Maximum Average Subarray I                      | Easy       | Fixed Size Window              | https://leetcode.com/problems/maximum-average-subarray-i/                      |
| 2 | Maximum Sum of Distinct Subarrays With Length K | Medium     | Fixed Window + HashSet         | https://leetcode.com/problems/maximum-sum-of-distinct-subarrays-with-length-k/ |
| 3 | Sliding Window Maximum                          | Hard       | Fixed Window + Monotonic Queue | https://leetcode.com/problems/sliding-window-maximum/                          |

### Skills Learned

* Fixed Size Window
* Build Window
* Slide Window
* Update Answer

---

# 🟡 Level 2 — Longest Valid Window

Grow the window until it becomes invalid.

Shrink until it becomes valid again.

| # | Problem                                        | Difficulty | Main Idea                 | Link                                                                          |
| - | ---------------------------------------------- | ---------- | ------------------------- | ----------------------------------------------------------------------------- |
| 4 | Longest Substring Without Repeating Characters | Medium     | HashMap + Variable Window | https://leetcode.com/problems/longest-substring-without-repeating-characters/ |
| 5 | Max Consecutive Ones III                       | Medium     | At Most K                 | https://leetcode.com/problems/max-consecutive-ones-iii/                       |
| 6 | Longest Repeating Character Replacement        | Medium     | Frequency Window          | https://leetcode.com/problems/longest-repeating-character-replacement/        |
| 7 | Fruit Into Baskets                             | Medium     | At Most Two Types         | https://leetcode.com/problems/fruit-into-baskets/                             |

### Skills Learned

* Variable Window
* Expand
* Shrink
* HashMap
* Frequency Count

---

# 🟠 Level 3 — Minimum Window

Shrink as much as possible while remaining valid.

| #  | Problem                               | Difficulty | Main Idea          | Link                                                                 |
| -- | ------------------------------------- | ---------- | ------------------ | -------------------------------------------------------------------- |
| 8  | Minimum Size Subarray Sum             | Medium     | Minimum Window     | https://leetcode.com/problems/minimum-size-subarray-sum/             |
| 9  | Minimum Window Substring              | Hard       | Frequency Matching | https://leetcode.com/problems/minimum-window-substring/              |
| 10 | Shortest Subarray with Sum at Least K | Hard       | Advanced Window    | https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/ |

### Skills Learned

* Shrink Window
* Minimum Window
* Valid Window Tracking

---

# 🔵 Level 4 — Counting Windows

Instead of finding the longest window, count all valid windows.

| #  | Problem                             | Difficulty | Main Idea                           | Link                                                               |
| -- | ----------------------------------- | ---------- | ----------------------------------- | ------------------------------------------------------------------ |
| 11 | Binary Subarrays With Sum           | Medium     | Exactly K = AtMost(K) − AtMost(K−1) | https://leetcode.com/problems/binary-subarrays-with-sum/           |
| 12 | Count Number of Nice Subarrays      | Medium     | Exactly K Formula                   | https://leetcode.com/problems/count-number-of-nice-subarrays/      |
| 13 | Subarrays with K Different Integers | Hard       | Exactly K Distinct                  | https://leetcode.com/problems/subarrays-with-k-different-integers/ |

### Skills Learned

* Counting Windows
* AtMost(K)
* Exactly(K)
* Prefix Counting

---

# 🟣 Level 5 — Frequency Window

The window depends on character frequencies.

| #  | Problem                                                 | Difficulty | Main Idea              | Link                                                                                   |
| -- | ------------------------------------------------------- | ---------- | ---------------------- | -------------------------------------------------------------------------------------- |
| 14 | Permutation in String                                   | Medium     | Character Frequency    | https://leetcode.com/problems/permutation-in-string/                                   |
| 15 | Find All Anagrams in a String                           | Medium     | Fixed Frequency Window | https://leetcode.com/problems/find-all-anagrams-in-a-string/                           |
| 16 | Maximum Number of Vowels in a Substring of Given Length | Medium     | Frequency Count        | https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/ |

### Skills Learned

* Character Count
* Frequency Array
* Sliding Frequency

---

# 🔴 Level 6 — Mixed Sliding Window

Problems that combine multiple ideas.

| #  | Problem                                              | Difficulty | Main Idea                  | Link                                                                                |
| -- | ---------------------------------------------------- | ---------- | -------------------------- | ----------------------------------------------------------------------------------- |
| 17 | Get Equal Substrings Within Budget                   | Medium     | Budget Window              | https://leetcode.com/problems/get-equal-substrings-within-budget/                   |
| 18 | Frequency of the Most Frequent Element               | Medium     | Sorting + Sliding Window   | https://leetcode.com/problems/frequency-of-the-most-frequent-element/               |
| 19 | Grumpy Bookstore Owner                               | Medium     | Fixed + Gain Window        | https://leetcode.com/problems/grumpy-bookstore-owner/                               |
| 20 | Number of Substrings Containing All Three Characters | Medium     | Counting + Variable Window | https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/ |

### Skills Learned

* Cost-Based Window
* Gain Maximization
* Frequency + Counting
* Mixed Window Techniques

---

# Concept Coverage

| Sliding Window Concept | Problems   |
| ---------------------- | ---------- |
| Fixed Window           | 1, 2, 3    |
| Longest Window         | 4, 5, 6, 7 |
| Minimum Window         | 8, 9, 10   |
| Count Windows          | 11, 12, 13 |
| Frequency Window       | 14, 15, 16 |
| Budget / Cost Window   | 17         |
| Sorting + Window       | 18         |
| Gain Maximization      | 19         |
| Mixed Concepts         | 20         |

---

# Mastery Checklist

For every problem:

* [ ] Identify the window type.
* [ ] Choose the correct template.
* [ ] Define the window state (sum, frequency, count, cost, etc.).
* [ ] Decide when to expand.
* [ ] Decide when to shrink.
* [ ] Update the answer at the correct time.
* [ ] Dry run on paper.
* [ ] Analyze Time Complexity.
* [ ] Analyze Space Complexity.
* [ ] Explain why the left pointer moves.

---

# Success Criteria

You have mastered Sliding Window if, when you see a new problem, you can immediately identify:

1. **Which window type is this?**

   * Fixed Size
   * Longest Window
   * Minimum Window
   * Count Windows
   * Frequency Window
   * Budget/Cost Window

2. **What is my window state?**

   * Sum
   * Frequency Array
   * HashMap
   * Distinct Count
   * Cost
   * Maximum Value

3. **When does the window become invalid?**

4. **Should I expand or shrink?**

> **If you can solve these 20 problems by deriving the logic instead of memorizing the code, you'll be prepared for the vast majority of Sliding Window questions in FAANG-style interviews.**
