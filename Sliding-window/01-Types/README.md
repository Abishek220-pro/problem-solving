## TYPE 1: Constant / Fixed Size Window

**When to use:** Look for an exact number or the letter **K** given as a fixed size.

**Key words:**

* "of length K"
* "subarray of size 3"
* "substring of length K"

**Example questions:**

* Maximum Sum Subarray of Size K

```java
public int fixedWindowTwoLoops(int[] arr, int k) {
    int left = 0;
    int right = 0;
    int sum = 0;

    // Build initial window
    while (right < k) {
        sum += arr[right];
        right++;
    }

    int maxVal = sum;

    // Slide window
    while (right < arr.length) {
        sum += arr[right];
        sum -= arr[left];

        maxVal = Math.max(maxVal, sum);

        left++;
        right++;
    }

    return maxVal;
}
```

---

## TYPE 2: Longest Subarray / Substring Where `<condition>`

**When to use:** Find the biggest possible valid window.

**Key words:**

* "Longest substring"
* "Maximum consecutive"
* "At most K"

**Example questions:**

* Longest Substring Without Repeating Characters
* Max Consecutive Ones III

### Brute Force

```java
public int longestSubarrayBruteForce(int[] nums, int k) {
    int maxLen = 0;
    
    // Outer loop picks the starting point 'i'
    for (int i = 0; i < nums.length; i++) {
        int state = 0; // Reset your weapon for every new starting point
        
        // Inner loop expands the ending point 'j'
        for (int j = i; j < nums.length; j++) {
            state += nums[j]; // Add current element
            
            // Check if the current subarray [i...j] is valid
            if (state <= k) {
                maxLen = Math.max(maxLen, j - i + 1);
            } else {
                // Optimization: If condition breaks and numbers are positive, 
                // no need to look further for this 'i'
                break; 
            }
        }
    }
    return maxLen;
}
```

### Better

```java
public int longestSubarrayBetter(int[] nums, int k) {
    int left = 0, right = 0;
    int maxLen = 0;
    int state = 0; // Your Weapon tracker

    while (right < nums.length) {
        state += nums[right]; // 📦 BOX 1: Add incoming element
        
        // 📦 BOX 2: SHRINK CONDITION (Using a WHILE loop)
        // Keep shrinking from the left until the window becomes valid again
        while (state > k) { 
            state -= nums[left]; // Mirror Rule
            left++;
        }
        
        // 📦 BOX 3: UPDATE ANSWER
        // Here, the window is 100% guaranteed to be valid
        maxLen = Math.max(maxLen, right - left + 1);
        
        right++;
    }
    return maxLen;
}
```

### Optimized

```java
public int longestSubarrayOptimized(int[] nums, int k) {
    int left = 0, right = 0;
    int maxLen = 0;
    int state = 0; // Your Weapon tracker

    while (right < nums.length) {
        state += nums[right]; // 📦 BOX 1: Add incoming element
        
        // 🚀 STRIVER OPTIMIZATION: 'if' instead of 'while'
        // We do NOT shrink; we just shift the maximum size window forward
        if (state > k) {
            state -= nums[left]; // Mirror Rule
            left++;
        }
        
        // 📦 BOX 3: UPDATE ANSWER
        // Only record the answer if the current window is strictly VALID
        if (state <= k) {
            maxLen = Math.max(maxLen, right - left + 1);
        }
        
        right++;
    }
    return maxLen;
}
```

---

## TYPE 3: Number of Subarrays Where `<condition>`

**When to use:** The problem asks **"How many?"**

**Key words:**

* "Count the number of subarrays"
* "Subarrays with exactly K"
* "Number of substrings"

**Example questions:**

* Subarrays with K Different Integers
* Binary Subarrays With Sum

### Formula

```text
Exactly(K) = AtMost(K) - AtMost(K - 1)
```

```java
 public class SlidingWindowMastery {
         
             /**
              * Master Function: Finds the number of subarrays meeting a criteria EXACTLY K.
              * Formula: Exactly(K) = AtMost(K) - AtMost(K - 1)
              */
             public int numSubarraysExactlyK(int[] nums, int k) {
                 // X1 = Count of subarrays with At Most K
                 int x1 = numSubarraysAtMostK_Phase1(nums, k);
                 
                 // X2 = Count of subarrays with At Most K - 1
                 int x2 = numSubarraysAtMostK_Phase2(nums, k - 1);
                 
                 // Final Extraction
                 return x1 - x2;
             }
         
             /**
              * PHASE 1: Helper function to calculate subarrays with At Most K
              * Tracks execution using distinct pointers: left1, right1
              */
             private int numSubarraysAtMostK_Phase1(int[] nums, int k) {
                 if (k < 0) return 0; // Edge case safety
                 
                 int left1 = 0;
                 int right1 = 0;
                 int count = 0;
                 int sum = 0;
                 
                 while (right1 < nums.length) {
                     // 📦 BOX 1: RIGHT ENTERING
                     sum += nums[right1];
                     
                     // 📦 BOX 2: SHRINK CONDITION
                     while (sum > k && left1 <= right1) {
                         sum -= nums[left1]; // Mirror Rule
                         left1++;
                     }
                     
                     // 📦 BOX 3: UPDATE COUNT (Adds all valid subarrays ending at right1)
                     count += (right1 - left1 + 1);
                     
                     right1++;
                 }
                 return count;
             }
         
             /**
              * PHASE 2: Helper function to calculate subarrays with At Most K - 1
              * Tracks execution using distinct pointers: left2, right2
              */
             private int numSubarraysAtMostK_Phase2(int[] nums, int k) {
                 if (k < 0) return 0; // Edge case safety
                 
                 int left2 = 0;
                 int right2 = 0;
                 int count = 0;
                 int sum = 0;
                 
                 while (right2 < nums.length) {
                     // 📦 BOX 1: RIGHT ENTERING
                     sum += nums[right2];
                     
                     // 📦 BOX 2: SHRINK CONDITION
                     while (sum > k && left2 <= right2) {
                         sum -= nums[left2]; // Mirror Rule
                         left2++;
                     }
                     
                     // 📦 BOX 3: UPDATE COUNT (Adds all valid subarrays ending at right2)
                     count += (right2 - left2 + 1);
                     
                     right2++;
                 }
                 return count;
             }
         }

```

---

## TYPE 4: Shortest / Minimum Window Where `<condition>`

**When to use:** Find the smallest valid window.

**Key words:**

* "Minimum size subarray"
* "Shortest substring"
* "Smallest window"

**Example questions:**

* Minimum Size Subarray Sum
* Minimum Window Substring

```java
public int shortestWindowOptimized(int[] nums, int target) {
    int left = 0;
    int right = 0;
    int minLen = Integer.MAX_VALUE;
    int sum = 0;

    while (right < nums.length) {
        sum += nums[right];

        while (sum >= target) {
            minLen = Math.min(minLen, right - left + 1);

            sum -= nums[left];
            left++;
        }

        right++;
    }

    return minLen == Integer.MAX_VALUE ? 0 : minLen;
}
```
