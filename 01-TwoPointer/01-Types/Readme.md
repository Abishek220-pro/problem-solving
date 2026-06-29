# Types of Two Pointers

Two Pointers is not a single technique. It consists of multiple pointer movement strategies. Choosing the correct type is the first step toward solving the problem efficiently.

---

# Type 1 — Opposite Direction Pointers

## Idea

Two pointers start from opposite ends of the data structure and move toward each other.

```text
Left                         Right
 ↓                             ↓
[1][2][3][4][5][6][7][8][9]
            ↑   ↑
```

## Pointer Movement

```java
int left = 0;
int right = nums.length - 1;

while (left < right) {

    // Process current elements

    if (condition) {
        left++;
    } else {
        right--;
    }
}
```

## When to Use

* Sorted arrays
* Pair sum problems
* Reverse array/string
* Palindrome checking
* Max area problems
* Water trapping
* Comparing elements from both ends

## Common Problems

* Two Sum II
* Reverse String
* Valid Palindrome
* Container With Most Water
* Trapping Rain Water

## Time Complexity

```
O(n)
```

## Space Complexity

```
O(1)
```

---

# Type 2 — Same Direction Pointers

## Idea

Both pointers move from left to right.

The **fast pointer** explores the array.

The **slow pointer** keeps track of where the next valid element should be placed.

```text
Slow
 ↓
Fast
 ↓
[1][2][2][3][3][4][5]
```

## Pointer Movement

```java
int slow = 0;

for (int fast = 0; fast < nums.length; fast++) {

    if (condition) {

        nums[slow] = nums[fast];
        slow++;
    }
}
```

## When to Use

* Remove duplicates
* Remove elements
* Move zeroes
* In-place modification
* Array compression
* Stable partitioning

## Common Problems

* Remove Duplicates from Sorted Array
* Remove Element
* Move Zeroes
* Sort Colors (variation)

## Time Complexity

```
O(n)
```

## Space Complexity

```
O(1)
```

---

# Type 3 — Fast & Slow Pointer

## Idea

Both pointers start at the same position.

The **slow pointer** moves one step.

The **fast pointer** moves two steps.

```text
Slow →
Fast ──→
```

If a cycle exists, both pointers will eventually meet.

## Pointer Movement

```java
ListNode slow = head;
ListNode fast = head;

while (fast != null && fast.next != null) {

    slow = slow.next;
    fast = fast.next.next;
}
```

## When to Use

* Detect cycles
* Find middle node
* Happy Number
* Cycle entry point
* Linked List traversal

## Common Problems

* Linked List Cycle
* Linked List Cycle II
* Middle of the Linked List
* Happy Number

## Time Complexity

```
O(n)
```

## Space Complexity

```
O(1)
```

---

# Type 4 — Sliding Window (Special Two Pointers)

## Idea

Two pointers maintain a **continuous window**.

The window expands by moving the right pointer.

The window shrinks by moving the left pointer.

```text
Left                 Right
 ↓                     ↓
[1][2][3][4][5][6][7]
```

## Pointer Movement

```java
int left = 0;

for (int right = 0; right < nums.length; right++) {

    // Expand window

    while (windowInvalid) {

        // Shrink window
        left++;
    }

    // Update answer
}
```

## When to Use

* Continuous subarrays
* Continuous substrings
* Maximum length
* Minimum length
* Window optimization

## Common Problems

* Longest Substring Without Repeating Characters
* Minimum Window Substring
* Longest Repeating Character Replacement
* Permutation in String
* Minimum Size Subarray Sum

## Time Complexity

```
O(n)
```

## Space Complexity

```
O(1)
```

*(Some problems may require extra space for a HashMap or HashSet.)*

---

# Comparison Table

| Type               | Pointer Direction             | Best Used For                                         |
| ------------------ | ----------------------------- | ----------------------------------------------------- |
| Opposite Direction | Left → ← Right                | Sorted arrays, pairs, reverse, palindrome             |
| Same Direction     | Slow → Fast →                 | Remove duplicates, move zeroes, in-place modification |
| Fast & Slow        | Slow (1 step), Fast (2 steps) | Linked Lists, cycle detection, middle node            |
| Sliding Window     | Left → Right →                | Continuous subarrays and substrings                   |

---

# How to Choose the Correct Type

```
Is the array sorted?
        │
       Yes
        │
        ▼
Opposite Direction
```

```
Need to remove or overwrite elements?
        │
       Yes
        │
        ▼
Same Direction
```

```
Working with a Linked List?
        │
       Yes
        │
        ▼
Fast & Slow Pointer
```

```
Need a continuous subarray or substring?
        │
       Yes
        │
        ▼
Sliding Window
```

---

# Quick Revision

| Problem Keyword     | Pointer Type       |
| ------------------- | ------------------ |
| Pair                | Opposite Direction |
| Sorted Array        | Opposite Direction |
| Reverse             | Opposite Direction |
| Palindrome          | Opposite Direction |
| Remove Duplicates   | Same Direction     |
| Remove Element      | Same Direction     |
| Move Zeroes         | Same Direction     |
| Linked List Cycle   | Fast & Slow        |
| Middle Node         | Fast & Slow        |
| Happy Number        | Fast & Slow        |
| Longest Substring   | Sliding Window     |
| Minimum Window      | Sliding Window     |
| Continuous Subarray | Sliding Window     |

---

> **Rule to Remember:**
> **Choose the pointer movement based on the problem's structure, not by memorizing the problem name.**
