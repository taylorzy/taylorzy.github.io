---
layout: post
title: Combination Sum
---

<h2 class="lightBlue">{{ page.title }}</h2>

<p class="description">{{ page.date | date_to_string }}</p>

"Combination Sum":https://leetcode.com/problems/combination-sum/.

"Combination Sum II":https://leetcode.com/problems/combination-sum-ii/.

"Combination Sum III":https://leetcode.com/problems/combination-sum-iii/.

The ideas of all three puzzles are similar.

Sort the candidate list.

For each candidate number, if it's smaller than target number, add this in a temp list and recursively calculate the sub-candidates with target - current candidate number.
Else if current candidate number equals target, add it to the temp list and add it in result list.
Else (only greater case here) break the loop.