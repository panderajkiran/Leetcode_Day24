# Leetcode_Day24
# Day 24 — LeetCode 3136: Valid Word

## Problem

Given a string `word`, determine whether it is a valid word.

A word is valid if:

* It contains at least 3 characters.
* It contains only English letters and digits.
* It contains at least one vowel.
* It contains at least one consonant.

## Approach

1. Check if the length of the word is less than 3. If yes, return `false`.
2. Traverse each character:

   * Check whether it is a letter or digit.
   * Convert letters to lowercase.
   * Check whether the character is a vowel.
   * If it is a letter but not a vowel, mark it as a consonant.
3. Return `true` only if both a vowel and a consonant are present.

## Complexity

* **Time Complexity:** `O(n)`
* **Space Complexity:** `O(1)`

## Java Solution

```java
class Solution {
    public boolean isValid(String word) {
        boolean hasVowel = false;
        boolean hasConsonant = false;

        if (word.length() < 3) {
            return false;
        }

        for (char c : word.toCharArray()) {
            if (!Character.isDigit(c) && !Character.isLetter(c)) {
                return false;
            }

            c = Character.toLowerCase(c);

            if ("aeiou".indexOf(c) != -1) {
                hasVowel = true;
            } else if (Character.isLetter(c)) {
                hasConsonant = true;
            }
        }

        return hasVowel && hasConsonant;
    }
}
```

## Key Learning

Today's problem was simple, but it reinforced an important habit: **validate conditions one by one instead of trying to solve everything with one complicated check.**

Breaking a problem into small conditions makes the logic easier to understand, debug, and maintain.
