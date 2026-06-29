# 🧠 The Sliding Window Master Rule

Think of Sliding Window like this:

* 👉 `right` pointer = **Explorer**
* 👉 `left` pointer = **Cleaner**

The Explorer keeps moving forward and adding new things.

The Cleaner removes extra things when the window breaks the rules.

Your job is simple:

```text
Add → Check → Remove → Save Answer
```

---

## ✈️ Step 1: Ask These Questions First

Before writing code, ask yourself:

### ❓ Is it a subarray or substring?

If **yes**, Sliding Window might work.

Examples:

* Subarray
* Substring
* Consecutive elements
* Continuous sequence

---

### ❓ Is the window size fixed or changing?

#### Fixed Size

The problem gives a number like `K`.

Examples:

* "Subarray of size K"
* "Substring of length K"

Move the whole window together.

```text
[1 2 3] 4 5
  ↓
1 [2 3 4] 5
```

---

#### Variable Size

The window can grow and shrink.

Examples:

* "Longest..."
* "Shortest..."
* "At most K..."
* "Exactly K..."

---

### ❓ What type of data am I using?

| Data               | Weapon                    |
| ------------------ | ------------------------- |
| Numbers            | `sum`, `product`, `count` |
| Characters         | Frequency Array           |
| Unique Values      | `HashSet`                 |
| Key-Value Tracking | `HashMap`                 |

---

## 🔄 The 4 Magic Steps

Every Sliding Window problem follows the same pattern.

### 1️⃣ Add

Move `right`.

Add the new element.

```java
sum += nums[right];
```

---

### 2️⃣ Check

Ask:

```text
Is my window still valid?
```

Examples:

* `sum > target`
* `duplicates found`
* `count > k`

---

### 3️⃣ Remove

If the window breaks the rule:

Move `left`.

Undo what you added.

```java
sum -= nums[left];
left++;
```

Keep removing until the window becomes valid again.

---

### 4️⃣ Save Answer

Now the window is correct.

Save the answer.

```java
maxLen = Math.max(maxLen, right - left + 1);
```

---

## 🪞 The Mirror Rule

Whatever you do on the right side, undo on the left side.

```text
Add      → Remove
Multiply → Divide
Increase → Decrease
```

Examples:

```java
sum += nums[right];
sum -= nums[left];
```

```java
freq[s.charAt(right)]++;
freq[s.charAt(left)]--;
```

If you forget the Mirror Rule, your answer will be wrong.

---

## ⚠️ Three Things to Check

Before starting your loop:

### Empty Input

```java
if (s == null || s.length() == 0) return 0;
```

### Impossible Target

Can the answer even exist?

If not, return early.

### Whole Array is One Window

If the window size equals the array size, calculate the answer directly.

---

## ⏰ When Should I Update My Answer?

### Longest / Maximum Problems

Update **after removing invalid elements**.

### Shortest / Minimum Problems

Update **inside the shrinking loop**.

---

## 🎓 Remember This Story

```text
right = Explorer 🧭
left  = Cleaner 🧹
```

The Explorer keeps moving.

The Cleaner fixes mistakes.

Together, they keep the window correct.

---

## ⚡ One-Line Formula

```text
Add → Check → Remove → Save
```

If you remember this formula, you can solve almost every Sliding Window problem.
