## 🗡️ WEAPON 1: The Accumulator Variable (`sum`, `state`, `product`)

**What it is:**

The most fundamental weapon. It is a simple primitive variable (like an `int` or `long`) that keeps a running total of the window's current state in **O(1)** time.

**When to use:**

Any problem where the condition involves adding, multiplying, or tracking a simple count of elements that can easily be reversed.

**Key words:**

* number
* sum
* odd
* even

### 🧠 The Core Logic (The Mirror Rule)

Because the window slides, whatever you do when an element enters on the right, you must do the exact mathematical opposite when an element leaves on the left.

* If you add the right element → You must subtract the left element.
* If you multiply the right element → You must divide the left element.

```java
// 1. Equip the weapon before the loop
int sum = 0; // or long product = 1;

while (right < nums.length) {

    // 📦 BOX 1: RIGHT ENTERING
    sum += nums[right];

    // 📦 BOX 2: SHRINK CONDITION
    while (sum > target && left <= right) {

        // Mirror Rule
        sum -= nums[left];
        left++;
    }

    // 📦 BOX 3: UPDATE ANSWER
    maxLen = Math.max(maxLen, right - left + 1);

    right++;
}
```

---

## 🗡️ WEAPON 2: The Fixed-Size Frequency Array (`int[256]` or `int[26]`)

**What it is:**

A lightning-fast, highly optimized alternative to `HashMap<Character, Integer>`.

**When to use:**

Any sliding window problem that involves strings or characters.

**Key words:**

* character
* string
* letters

### 🧠 The Core Logic

* If the problem strictly says **only lowercase English letters**, use:

```java
int[] hash = new int[26];
```

* Use `hash[c - 'a']` to map `'a'` to index `0`.

* If the problem includes spaces, symbols, numbers, or uppercase letters, use:

```java
int[] hash = new int[256];
```

* Use `hash[c]` directly because ASCII characters automatically convert to integer indexes.

```java
// 1. Equip the weapon before the loop
int[] hash = new int[256];

while (right < s.length()) {
    char incomingChar = s.charAt(right);

    // 📦 BOX 1: RIGHT ENTERING
    hash[incomingChar]++;

    // 📦 BOX 2: SHRINK CONDITION
    while (hash[incomingChar] > 1) {
        char outgoingChar = s.charAt(left);

        hash[outgoingChar]--;
        left++;
    }

    // 📦 BOX 3: UPDATE ANSWER
    maxLen = Math.max(maxLen, right - left + 1);

    right++;
}
```

---

## ⚔️ WEAPON 3: Substring Search & Target Matching

**What it is:**

A technique that uses a frequency array to track remaining needs.

**When to use:**

Find start indices of all anagrams or permutations of a target pattern within a text.

### 🧠 Core Idea

1. Fill an `int[256]` array with target character frequencies.
2. Decrement frequencies when expanding with `right`.
3. Increment frequencies when shrinking with `left`.
4. When `count == target.length()`, the current window is valid.

```java
    public List<Integer> findAnagrams(String txt, String word) {
    List<Integer> ans = new ArrayList<>();
    int left = 0, right = 0;
    int count = word.length(); // Tracks how many characters we still need
    int[] freq = new int[256];
    
    // 1. Fill the frequency array (The Target)
    for(char ch : word.toCharArray()) freq[ch]++;
    
    // 2. Main engine
    while (right < txt.length()) {
        // 📦 BOX 1: RIGHT ENTERING
        // If freq > 0, the character is needed, so we reduce the total count
        if (freq[txt.charAt(right)] > 0) count--;
        freq[txt.charAt(right)]--; 
        
        // 📦 BOX 2: SHRINK CONDITION (Maintain window size)
        // If the window exceeds word length, slide the left pointer
        while (right - left + 1 > word.length()) {
            freq[txt.charAt(left)]++; // Restore the need
            // If frequency > 0, it means we regained a needed character
            if (freq[txt.charAt(left)] > 0) count++;
            left++;
        }
        
        // 📦 BOX 3: MATCH CONDITION
        // If count is 0, all required characters are in the current window
        if (count == 0  && right-left+1==word.length()) {
            ans.add(left);
        }
        
        right++;
    }
    return ans;
}
}
```

---

## ⚔️ WEAPON 4: Variable Sliding Window (`HashMap` / `HashSet`)

**What it is:**

A high-speed tracker used to ensure every element in your window is unique.

**When to use:**

Problems asking for:

* Longest substring without repeating characters
* Unique elements only

```java
public int lengthOfLongestSubstring(String s) {
    Set<Character> set = new HashSet<>();
    int left = 0, right = 0;
    int maxLen = 0;

    while (right < s.length()) {

        while (set.contains(s.charAt(right))) {
            set.remove(s.charAt(left));
            left++;
        }

        set.add(s.charAt(right));

        maxLen = Math.max(maxLen, right - left + 1);

        right++;
    }

    return maxLen;
}
```
