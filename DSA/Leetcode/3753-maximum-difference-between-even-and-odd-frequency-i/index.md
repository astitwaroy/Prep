<div align = "center">
<h style = "margin-bottom: 0px; margin-top: 0px; color : purple;" align = "center" class = "header">

## ⌨ 3753. Maximum Difference Between Even and Odd Frequency I

</h>
</div>

<h2><a href="https://leetcode.com/problems/maximum-difference-between-even-and-odd-frequency-i" target = "_blank">3753. Maximum Difference Between Even and Odd Frequency I</a></h2><h3>Easy</h3><hr><p>You are given a string <code>s</code> consisting of lowercase English letters. Your task is to find the <strong>maximum</strong> difference between the frequency of <strong>two</strong> characters in the string such that:</p>

<ul>
	<li>One of the characters has an <strong>even frequency</strong> in the string.</li>
	<li>The other character has an <strong>odd frequency</strong> in the string.</li>
</ul>

<p>Return the <strong>maximum</strong> difference, calculated as the frequency of the character with an <b>odd</b> frequency <strong>minus</strong> the frequency of the character with an <b>even</b> frequency.</p>

<p>&nbsp;</p>
<p><strong class="example">Example 1:</strong></p>

<div class="example-block">
<p><strong>Input:</strong> <span class="example-io">s = &quot;aaaaabbc&quot;</span></p>

<p><strong>Output:</strong> 3</p>

<p><strong>Explanation:</strong></p>

<ul>
	<li>The character <code>&#39;a&#39;</code> has an <strong>odd frequency</strong> of <code><font face="monospace">5</font></code><font face="monospace">,</font> and <code>&#39;b&#39;</code> has an <strong>even frequency</strong> of <code><font face="monospace">2</font></code>.</li>
	<li>The maximum difference is <code>5 - 2 = 3</code>.</li>
</ul>
</div>

<p><strong class="example">Example 2:</strong></p>

<div class="example-block">
<p><strong>Input:</strong> <span class="example-io">s = &quot;abcabcab&quot;</span></p>

<p><strong>Output:</strong> 1</p>

<p><strong>Explanation:</strong></p>

<ul>
	<li>The character <code>&#39;a&#39;</code> has an <strong>odd frequency</strong> of <code><font face="monospace">3</font></code><font face="monospace">,</font> and <code>&#39;c&#39;</code> has an <strong>even frequency</strong> of <font face="monospace">2</font>.</li>
	<li>The maximum difference is <code>3 - 2 = 1</code>.</li>
</ul>
</div>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>3 &lt;= s.length &lt;= 100</code></li>
	<li><code>s</code> consists only of lowercase English letters.</li>
	<li><code>s</code> contains at least one character with an odd frequency and one with an even frequency.</li>
</ul>

<CodeTabs :languages="[ { name: 'C++', slot: 'cpp' }, { name: 'Java', slot: 'java' } ]">

<template #java>

```java
class Solution {
    public int maxDifference(String s) {
        int n = s.length();
        int freq[] = new int[26];
        for (int i = 0; i < n; i++)
            freq[s.charAt(i) - 'a']++;
        ArrayList<Integer> even = new ArrayList<>();
        ArrayList<Integer> odd = new ArrayList<>();
        for (int i = 0; i < 26; i++) {
            if (freq[i] % 2 == 0 && freq[i] != 0)
                even.add(freq[i]);
            else
                odd.add(freq[i]);
        }
        int maxi = Integer.MIN_VALUE;
        for (int i = 0; i < odd.size(); i++) {
            for (int j = 0; j < even.size(); j++)
                maxi = Math.max(maxi, odd.get(i) - even.get(j));
        }
        return maxi;
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
