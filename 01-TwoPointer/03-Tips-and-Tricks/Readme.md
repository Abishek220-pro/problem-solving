# Tips & Tricks (Two Pointers)

> **Goal:** Think logically, not by memorization. Every pointer movement should have a clear reason.

---

# Tip 1 — Read the Constraints First

Before writing any code, read the constraints carefully.

Ask yourself:

* Is the array sorted?
* Can I sort it?
* Is in-place modification required?
* Are duplicate answers allowed?
* Is extra space allowed?

Many problems reveal the correct approach through their constraints.

---

# Tip 2 — Identify the Pointer Type

Choose the pointer type before coding.

| Clue                            | Pointer Type       |
| ------------------------------- | ------------------ |
| Sorted Array                    | Opposite Direction |
| Remove / Move / Replace         | Same Direction     |
| Linked List                     | Fast & Slow        |
| Continuous Subarray / Substring | Sliding Window     |

Never start coding before choosing the pointer type.

---

# Tip 3 — Every Pointer Must Have a Job

Always know why each pointer exists.

Examples

```text
Left  → Smaller values

Right → Larger values
```

or

```text
Fast → Reads

Slow → Writes
```

If you cannot explain a pointer's purpose, your solution is probably incorrect.

---

# Tip 4 — Never Move Pointers Randomly

Every movement must improve the answer.

For sorted arrays:

```text
sum < target

Need Bigger Sum

↓

left++
```

```text
sum > target

Need Smaller Sum

↓

right--
```

Always ask:

> "Why am I moving this pointer?"

---

# Tip 5 — Sort Only When Allowed

Sorting is one of the strongest tools.

Sort only when:

* Original order does not matter.
* Indices are not required.
* The problem allows rearranging elements.

Otherwise, do **not** sort.

---

# Tip 6 — Think Before Using Extra Space

Before creating:

* HashMap
* HashSet
* Extra Array

Ask:

> Can Two Pointers solve this in O(1) space?

Interviewers often expect the optimized solution.

---

# Tip 7 — Skip Duplicate Work

Duplicate values often produce duplicate answers.

Skip already processed elements.

Example:

```java
while (left < right && nums[left] == nums[left - 1]) {
    left++;
}
```

Common in:

* 3Sum
* 4Sum
* Combination problems

---

# Tip 8 — Dry Run on Paper

Before coding:

Draw the array.

```text
Index : 0 1 2 3 4

Array : 1 2 3 4 5

Left

Right
```

Move the pointers manually.

This catches most logical mistakes.

---

# Tip 9 — Watch Boundary Conditions

Always test:

* Empty array
* One element
* Two elements
* All duplicates
* No solution
* All elements same
* Negative numbers
* Large values

Most interview bugs happen here.

---

# Tip 10 — Choose the Correct Loop

Opposite Direction

```java
while (left < right)
```

Same Direction

```java
for (int fast = 0; fast < n; fast++)
```

Fast & Slow

```java
while (fast != null && fast.next != null)
```

Sliding Window

```java
for (int right = 0; right < n; right++)
```

Wrong loop conditions cause infinite loops and missed cases.

---

# Tip 11 — Update the Answer at the Right Time

Ask yourself:

Should I update the answer:

* Before moving pointers?
* After moving pointers?

Updating too early or too late is a common mistake.

---

# Tip 12 — Don't Lose Valid Answers

When you find a valid answer:

Ask:

* Should I stop?
* Continue searching?
* Skip duplicates?
* Store the answer?

Different problems require different actions.

---

# Tip 13 — Time Complexity Check

Ask yourself:

How many times does each pointer move?

If each pointer moves at most **n** times:

```text
Time Complexity = O(n)
```

If sorting is used:

```text
O(n log n) + O(n)
```

---

# Tip 14 — Space Complexity Check

Most Two Pointer solutions use:

```text
O(1)
```

Extra space is usually unnecessary unless explicitly required.

---

# Tip 15 — Explain Your Pointer Movement

During interviews, explain:

> Why does the left pointer move?

> Why does the right pointer move?

Being able to explain the movement is often more important than writing the code.

---

# Common Mistakes

❌ Moving both pointers without reason

❌ Forgetting to sort (when allowed)

❌ Sorting when order matters

❌ Forgetting duplicate skipping

❌ Wrong loop condition

❌ Infinite loop

❌ Updating answer at the wrong time

❌ Missing edge cases

❌ Forgetting in-place requirements

❌ Not checking constraints

---

# Interview Mental Checklist

Before coding, ask yourself:

* [ ] What is the data structure?
* [ ] Which pointer type should I use?
* [ ] Is the array sorted?
* [ ] Can I sort it?
* [ ] Why does the left pointer move?
* [ ] Why does the right pointer move?
* [ ] Am I modifying the array?
* [ ] Do I need to skip duplicates?
* [ ] What is my stopping condition?
* [ ] Have I tested edge cases?
* [ ] What are the time and space complexities?

---

# Golden Rules

1. **Read constraints before choosing an algorithm.**
2. **Every pointer must have a clear purpose.**
3. **Never move a pointer without a logical reason.**
4. **Dry run before writing code.**
5. **Derive the solution—don't memorize it.**
