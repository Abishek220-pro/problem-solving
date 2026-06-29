# Universal Weapons of Two Pointers

> Every Two Pointer problem can usually be solved by choosing **one** of these four weapons. Don't memorize problems—identify the clue and apply the correct weapon.

---

# Weapon 1 — Sort First

## Clue

Ask yourself:

* Is the array unsorted?
* Does the original order NOT matter?
* Am I searching for pairs, triplets, or quadruplets?

If **YES**, sort the array first.

---

## Why?

Sorting creates order.

Once the array is ordered, pointer movement becomes logical.

---

## Code Template

```java
Arrays.sort(nums);

int left = 0;
int right = nums.length - 1;

while (left < right) {

}
```

---

## Used In

* Two Sum II (already sorted)
* Two Sum (if sorting is allowed)
* 3Sum
* 3Sum Closest
* 4Sum
* Closest Pair
* K Sum

---

# Weapon 2 — Direction Rule

## Clue

Ask yourself:

> "How do I get closer to the answer?"

If the array is sorted, the answer is always determined by pointer movement.

---

### Rule 1

```text
sum < target

Need Bigger Sum

↓

left++
```

---

### Rule 2

```text
sum > target

Need Smaller Sum

↓

right--
```

---

## Code Template

```java
while (left < right) {

    int sum = nums[left] + nums[right];

    if (sum == target) {

        return answer;

    } else if (sum < target) {

        left++;

    } else {

        right--;

    }
}
```

---

## Used In

* Two Sum II
* 3Sum
* 3Sum Closest
* 4Sum
* Pair Difference
* Pair Distance
* Closest Pair

---

# Weapon 3 — Write Pointer

## Clue

Ask yourself:

* Am I modifying the array?
* Removing elements?
* Removing duplicates?
* Moving elements?

If YES

Use one pointer to read.

Use one pointer to write.

---

## Code Template

```java
int slow = 0;

for (int fast = 0; fast < nums.length; fast++) {

    if (condition) {

        nums[slow] = nums[fast];
        slow++;
    }
}
```

---

## Used In

* Remove Duplicates
* Remove Element
* Move Zeroes
* Compress Array
* Partition Array

---

# Weapon 4 — Skip Invalid Elements

## Clue

Ask yourself:

* Can the same answer appear again?
* Can duplicate values produce duplicate answers?
* Have I already processed this value?

If YES

Skip it.

---

## Code Template

```java
while (left < right && nums[left] == nums[left - 1]) {
    left++;
}

while (left < right && nums[right] == nums[right + 1]) {
    right--;
}
```

Or

```java
if (i > 0 && nums[i] == nums[i - 1]) {
    continue;
}
```

---

## Used In

* 3Sum
* 4Sum
* Combination Problems
* Unique Pair Problems

---

# Universal Decision Flow

```text
Read Problem
      │
      ▼
Is order important?
      │
 ┌────┴────┐
 │         │
No        Yes
 │
 ▼
Weapon 1
Sort First
      │
      ▼
Need pair/triplet?
      │
      ▼
Weapon 2
Direction Rule
      │
      ▼
Need to modify array?
      │
 ┌────┴────┐
 │         │
Yes       No
 │
 ▼
Weapon 3
Write Pointer
      │
      ▼
Duplicate answers possible?
      │
 ┌────┴────┐
 │         │
Yes       No
 │
 ▼
Weapon 4
Skip Duplicates
```

---

# The Four Weapons Cheat Sheet

| See This Clue                      | Use This Weapon                      |
| ---------------------------------- | ------------------------------------ |
| Unsorted array + Pair/Triplet      | **Weapon 1 — Sort First**            |
| Target Sum / Closest / Pair        | **Weapon 2 — Direction Rule**        |
| Remove / Move / Replace / In-place | **Weapon 3 — Write Pointer**         |
| Unique answers / Duplicates        | **Weapon 4 — Skip Invalid Elements** |

---

# The Golden Rule

> **Don't ask:** "Which LeetCode pattern is this?"

> **Ask instead:**
>
> 1. Can I sort?
> 2. How should the pointers move?
> 3. Am I writing back into the array?
> 4. Do I need to skip duplicates?

If you answer these four questions, you can derive the solution for almost every Two Pointers problem without memorizing patterns.
