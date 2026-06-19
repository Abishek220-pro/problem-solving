### TYPE 1: Constant / Fixed Size Window:

                    When to use: Look for an exact number or the letter "K" given as a fixed size.

                    Key Words in Problem: "of length K", "subarray of size 3", "substring of length K".

                    Example Questions: * Maximum Sum Subarray of Size K
                                     

   public int fixedWindowTwoLoops(int[] arr, int k) {
    int left = 0;
    int right = 0;
    int sum = 0;
    
    // 1️⃣ FIRST LOOP: Build the initial window of size K (from index 0 to k-1)

    while (right < k) {
        sum += arr[right];
        right++; 
    }
    
    int maxVal = sum;  // Lock the first window's sum
    
    // 2️⃣ SECOND LOOP: Slide the window across the remaining elements

    while (right < arr.length) {

        sum += arr[right]; // Add the incoming element on the right
        
        // Mirror Rule: Remove the outgoing element on the left

        sum -= arr[left];
        
        // Update the maximum answer for the current window

        maxVal = Math.max(maxVal, sum);
        
        // Slide both pointers forward together
        left++;
        right++; 
    }
    
    return maxVal;
}
### TYPE 2 : Longest subarray/Substring where<condition>
                      When to use: The problem asks you to stretch the window to find the biggest 
                      possible answer under a certain limit.

                      Key Words in Problem: "Longest substring...", "Maximum consecutive...", "with at most K...".

                       Example Questions:

                             Longest Substring Without Repeating Characters
                             
                             Max Consecutive Ones III

## Brute fource:
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
## Better :
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
## optimised :

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
### type 3 :no of subarray where <condition>
                     When to use: The problem does not ask for length. It asks "How many?" total subarrays exist.

                      Key Words in Problem: "Count the number of subarrays...", "Subarrays with exactly K...", "Number of substrings...".

                     Example Questions:

                                      Subarrays with K Different Integers
                                      
                                      Binary Subarrays With Sum

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

### Type 4 : shortest / minimun window where <condition>
                                   When to use: The problem asks you to shrink the window to find the smallest possible answer that satisfies a target.
                                   
                                   Key Words in Problem: "Minimum size subarray...", "Shortest substring containing...", "Smallest window...".
                                   
                                   Example Questions:
                                   
                                   Minimum Size Subarray Sum
                                   
                                   Minimum Window Substring

                public int shortestWindowOptimized(int[] nums, int target) {
                       int left = 0;
                       int right = 0;
                       int minLen = Integer.MAX_VALUE;
                       int sum = 0;
                       
                       while (right < nums.length) {
                           // 📦 BOX 1: RIGHT ENTERING
                           sum += nums[right];
                           
                           // 📦 BOX 2: SHRINK CONDITION
                           // The moment the window becomes VALID, try to minimize it
                           while (sum >= target) {
                               // 📦 BOX 3: UPDATE ANSWER
                               minLen = Math.min(minLen, right - left + 1);
                               
                               // Mirror Rule: Remove left element and contract window
                               sum -= nums[left];
                               left++;
                           }
                           
                           right++; // Always expand right
                       }
                       
                       return minLen == Integer.MAX_VALUE ? 0 : minLen;
                }
                       