---
layout: post
title: Find the majority number in a number array
---

<h2 class="lightBlue">{{ page.title }}</h2>

<p class="description">{{ page.date | date_to_string }}</p>

Given an array of size n, find the majority element. The majority element is the element that appears more than n/2 times.

You may assume that the array is non-empty and the majority element always exist in the array.

{% highlight java linenos %}
public int majorityElement(int[] a) {
  int n = a.length, m = a[0], c = 1;

  for (int i = 1; i < n; i++) {
    if (a[i] == m) {
      c++;
    } else if (c > 0) {
      c--;
    } else {
      m = a[i]; c = 1;
    }
  }

  return m;
}
{% endhighlight %}