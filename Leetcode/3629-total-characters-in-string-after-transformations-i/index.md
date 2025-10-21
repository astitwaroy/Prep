## 3629. Total Characters in String After Transformations I

**Difficulty:** Medium

---

You are given a string `s` and an integer `t`, representing the number of **transformations** to perform. In one **transformation**, every character in `s` is replaced according to the following rules:

- If the character is `'z'`, replace it with the string `"ab"`.
- Otherwise, replace it with the **next** character in the alphabet. For example, `'a'` is replaced with `'b'`, `'b'` is replaced with `'c'`, and so on.

Return the **length** of the resulting string after **exactly** `t` transformations.

Since the answer may be very large, return it **modulo** `10^9 + 7`.

### Example 1:

**Input:** `s = "abcyy", t = 2`

**Output:** `7`

**Explanation:**

- **First Transformation (t = 1)**:
    - `'a'` becomes `'b'`
    - `'b'` becomes `'c'`
    - `'c'` becomes `'d'`
    - `'y'` becomes `'z'`
    - `'y'` becomes `'z'`
    - String after the first transformation: `"bcdzz"`

- **Second Transformation (t = 2)**:
    - `'b'` becomes `'c'`
    - `'c'` becomes `'d'`
    - `'d'` becomes `'e'`
    - `'z'` becomes `"ab"`
    - `'z'` becomes `"ab"`
    - String after the second transformation: `"cdeabab"`

- **Final Length of the string**: The string is `"cdeabab"`, which has 7 characters.

### Example 2:

**Input:** `s = "azbk", t = 1`

**Output:** `5`

**Explanation:**

- **First Transformation (t = 1)**:
    - `'a'` becomes `'b'`
    - `'z'` becomes `"ab"`
    - `'b'` becomes `'c'`
    - `'k'` becomes `'l'`
    - String after the first transformation: `"babcl"`

- **Final Length of the string**: The string is `"babcl"`, which has 5 characters.

### Constraints:

- `1 <= s.length <= 10^5`
- `s` consists only of lowercase English letters.
- `1 <= t <= 10^5`

<CodeTabs :languages="[ { name: 'C++', slot: 'cpp' }, { name: 'Java', slot: 'java' } ]">

<template #java>

```java
class Solution {
    static int MOD = (int)(1e9 + 7);
    public int lengthAfterTransformations(String s, int t) {
        int n = s.length();
        int res = 0;
        int freq[] = new int[26];
        for (int i = 0; i < n; i++)
            freq[s.charAt(i) - 'a']++;
        while (t-->0) {
            int zCount = freq[25];
            for (int i = 24; i >= 0; i--) {
                freq[i + 1] = freq[i];
                freq[i] = 0;
            }
            if (zCount > 0) {
                freq[0] = (freq[0] + zCount) % MOD;
                freq[1] = (freq[1] + zCount) % MOD;
            }
        }
        for (int ele : freq)
            res = (res + ele) % MOD;
        return res;
    }
}
```

</template>

<template #cpp>

```cpp
// Add your C++ solution here
```

</template>

</CodeTabs>
