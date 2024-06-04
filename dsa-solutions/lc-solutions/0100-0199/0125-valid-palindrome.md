---
id: valid-palindrome
title: Valid Palindrome Solution
sidebar_label: 0125 Valid Palindrome
tags:
  - String
  - Two Pointer
  - LeetCode
  - Python
  - Java
  - C++
description: "This is a solution to the Valid Palindrome problem on LeetCode."
---

## Problem Description

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

### Examples

**Example 1:**

```
Input: "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
```

**Example 2:**

```
Input: "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
```

### Constraints

- The input string may consist of uppercase and lowercase letters, digits, and punctuation symbols.
- The empty string is considered a valid palindrome.

## Solution for Valid Palindrome Problem

<Tabs>
  <TabItem value="Brute Force" label="Brute Force">
  
### Approach 1: Brute Force

#### Intuition

The brute force approach involves stripping non-alphanumeric characters from the string and then checking if the resulting string is a palindrome by comparing it with its reverse.

#### Implementation

```jsx live
function ValidPalindromeTwoPointer() {
  const isPalindrome = function (s) {
    if (!s) return true;
    let left = 0,
      right = s.length - 1;
    while (left < right) {
      while (left < right && !s[left].match(/[a-zA-Z0-9]/)) left++;
      while (left < right && !s[right].match(/[a-zA-Z0-9]/)) right--;
      if (s[left].toLowerCase() !== s[right].toLowerCase()) return false;
      left++;
      right--;
    }
    return true;
  };

  const input = "A man, a plan, a canal: Panama";
  const output = isPalindrome(input);

  return (
    <div>
      <p>
        <b>Input:</b> {input}
      </p>
      <p>
        <b>Output:</b> {output.toString()}
      </p>
    </div>
  );
}
```

#### Code in Different Languages

<Tabs>
  <TabItem value="JavaScript" label="JavaScript">
  <SolutionAuthor name="@Vipullakum007"/>
   ```javascript
    function isPalindrome(s) {
        if (!s) return true;
        const cleanedS = s.replace(/[^A-Za-z0-9]/g, '').toLowerCase();
        return cleanedS === cleanedS.split('').reverse().join('');
    }
    ```

  </TabItem>
  <TabItem value="TypeScript" label="TypeScript">
  <SolutionAuthor name="@Vipullakum007"/> 
   ```typescript
    function isPalindrome(s: string): boolean {
        if (!s) return true;
        const cleanedS = s.replace(/[^A-Za-z0-9]/g, '').toLowerCase();
        return cleanedS === cleanedS.split('').reverse().join('');
    }

    const input: string = "A man, a plan, a canal: Panama";
    const output: boolean = isPalindrome(input);

    console.log("Input:", input);
    console.log("Output:", output);
    ```

  </TabItem>
  <TabItem value="Python" label="Python">
  <SolutionAuthor name="@Vipullakum007"/>
   ```python
    def is_palindrome(s: str) -> bool:
      if not s:
          return True
      cleaned_s = ''.join(ch.lower() for ch in s if ch.isalnum())
      return cleaned_s == cleaned_s[::-1]

      input_str = "A man, a plan, a canal: Panama"
      output = is_palindrome(input_str)

      print("Input:", input_str)
      print("Output:", output)

    ```

  </TabItem>
  <TabItem value="Java" label="Java">
  <SolutionAuthor name="@Vipullakum007"/>
   ```java
    class Solution {
        public boolean isPalindrome(String s) {
            if (s == null || s.isEmpty()) {
                return true;
            }
            
            String cleanedS = s.replaceAll("[^A-Za-z0-9]", "").toLowerCase();
            return cleanedS.equals(new StringBuilder(cleanedS).reverse().toString());
        }
    }
    ```

  </TabItem>
  <TabItem value="C++" label="C++">
  <SolutionAuthor name="@Vipullakum007"/>
   ```cpp
    class Solution {
    public:
        bool isPalindrome(string s) {
            if (s.empty()) {
                return true;
            }
            
            string cleanedS;
            for (char ch : s) {
                if (isalnum(ch)) {
                    cleanedS += tolower(ch);
                }
            }
            
            string reversedS = cleanedS;
            reverse(reversedS.begin(), reversedS.end());
            
            return cleanedS == reversedS;
        }
    };
    ```

  </TabItem>
</Tabs>

#### Complexity Analysis

- Time Complexity: O(n), where n is the length of the input string. We iterate through the string once.
- Space Complexity: O(n), where n is the length of the input string. We create a new string to store the cleaned version of the input.

</TabItem>
<TabItem value="Two Pointer" label="Two Pointer">

### Approach 2: Two Pointer

#### Intuition

The two-pointer approach involves using two pointers, one starting from the beginning of the string and the other starting from the end. We move both pointers towards the center of the string, comparing characters at each step until they meet or cross each other.

#### Implementation

```jsx live
function ValidPalindromeBruteForce() {
  const isPalindrome = function (s) {
    if (!s) return true;
    const cleanedS = s.replace(/[^A-Za-z0-9]/g, "").toLowerCase();
    return cleanedS === cleanedS.split("").reverse().join("");
  };

  const input = "A man, a plan, a canal: Panama";
  const output = isPalindrome(input);

  return (
    <div>
      <p>
        <b>Input:</b> {input}
      </p>
      <p>
        <b>Output:</b> {output.toString()}
      </p>
    </div>
  );
}
```

#### Code in Different Languages

<Tabs>
  <TabItem value="JavaScript" label="JavaScript">
  <SolutionAuthor name="@Vipullakum007"/>
   ```javascript
    function isPalindrome(s) {
        if (!s) return true;
        let left = 0, right = s.length - 1;
        while (left < right) {
            while (left < right && !s[left].match(/[a-zA-Z0-9]/)) left++;
            while (left < right && !s[right].match(/[a-zA-Z0-9]/)) right--;
            if (s[left].toLowerCase() !== s[right].toLowerCase()) return false;
            left++;
            right--;
        }
        return true;
    }
    ```

  </TabItem>
    <TabItem value="TypeScript" label="TypeScript">
  <SolutionAuthor name="@Vipullakum007"/> 
   ```typescript
    function isPalindrome(s: string): boolean {
      if (!s) return true;
      let left = 0, right = s.length - 1;
      while (left < right) {
          while (left < right && !s[left].match(/[a-zA-Z0-9]/)) left++;
          while (left < right && !s[right].match(/[a-zA-Z0-9]/)) right--;
          if (s[left].toLowerCase() !== s[right].toLowerCase()) return false;
          left++;
          right--;
      }
      return true;
    }
    ```

  </TabItem>
  <TabItem value="Java" label="Java">
  <SolutionAuthor name="@Vipullakum007"/>
   ```java
    class Solution {
        public boolean isPalindrome(String s) {
            if (s == null || s.isEmpty()) {
                return true;
            }
            
            int left = 0, right = s.length() - 1;
            while (left < right) {
                while (left < right && !Character.isLetterOrDigit(s.charAt(left))) left++;
                while (left < right && !Character.isLetterOrDigit(s.charAt(right))) right--;
                if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) return false;
                left++;
                right--;
            }
            return true;
        }
    }
    ```

  </TabItem>
  <TabItem value="Python" label="Python">
  <SolutionAuthor name="@Vipullakum007"/>
   ```python
    def is_palindrome(s: str) -> bool:
      if not s:
          return True
      left, right = 0, len(s) - 1
      while left < right:
          while left < right and not s[left].isalnum(): left += 1
          while left < right and not s[right].isalnum(): right -= 1
          if s[left].lower() != s[right].lower(): return False
          left += 1
          right -= 1
      return True
    ```

  </TabItem>
  <TabItem value="C++" label="C++">
  <SolutionAuthor name="@Vipullakum007"/>
   ```cpp
    class Solution {
    public:
        bool isPalindrome(string s) {
            if (s.empty()) {
                return true;
            }
            
            int left = 0, right = s.length() - 1;
            while (left < right) {
                while (left < right && !isalnum(s[left])) left++;
                while (left < right && !isalnum(s[right])) right--;
                if (tolower(s[left]) != tolower(s[right])) return false;
                left++;
                right--;
            }
            return true;
        }
    };
    ```

  </TabItem>
</Tabs>

#### Complexity Analysis

- Time Complexity: O(n), where n is the length of the input string. We iterate through the string once.
- Space Complexity: O(1). We're not using any extra space.

</TabItem>
</Tabs>

## References

- **LeetCode Problem**: [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

- **Solution Link**: [LeetCode Solution](https://leetcode.com/problems/valid-palindrome/solution/)

- **Authors GeeksforGeeks Profile:** [Vipul lakum](https://leetcode.com/u/vipul_lakum_02/)