---
layout: post
title: The Skyline Problem
---

<h2 class="lightBlue">{{ page.title }}</h2>

<p class="description">{{ page.date | date_to_string }}</p>

A city's skyline is the outer contour of the silhouette formed by all the buildings in that city when viewed from a distance. Now suppose you are given the locations and height of all the buildings as shown on a cityscape photo (Figure A), write a program to output the skyline formed by these buildings collectively (Figure B).

<div><a href="https://leetcode.com/static/images/problemset/skyline1.jpg" target="_blank"><img style=" max-width: 45%;" src="https://leetcode.com/static/images/problemset/skyline1.jpg" border="0" alt="Buildings"></a><a href="https://leetcode.com/static/images/problemset/skyline2.jpg" target="_blank"><img style=" max-width: 45%;" src="https://leetcode.com/static/images/problemset/skyline2.jpg" border="0" alt="Skyline Contour"></a></div>

The geometric information of each building is represented by a triplet of integers [Li, Ri, Hi], where Li and Ri are the x coordinates of the left and right edge of the ith building, respectively, and Hi is its height. It is guaranteed that 0 ≤ Li, Ri ≤ INT_MAX, 0 < Hi ≤ INT_MAX, and Ri - Li > 0. You may assume all buildings are perfect rectangles grounded on an absolutely flat surface at height 0.

For instance, the dimensions of all buildings in Figure A are recorded as: [ [2 9 10], [3 7 15], [5 12 12], [15 20 10], [19 24 8] ] .

The output is a list of "key points" (red dots in Figure B) in the format of [ [x1,y1], [x2, y2], [x3, y3], ... ] that uniquely defines a skyline. A key point is the left endpoint of a horizontal line segment. Note that the last key point, where the rightmost building ends, is merely used to mark the termination of the skyline, and always has zero height. Also, the ground in between any two adjacent buildings should be considered part of the skyline contour.

For instance, the skyline in Figure B should be represented as:[ [2 10], [3 15], [7 12], [12 0], [15 10], [20 8], [24, 0] ].

Notes:

<ul>
	<li>The number of buildings in any input list is guaranteed to be in the range [0, 10000].</li>
	<li>The input list is already sorted in ascending order by the left x position Li.</li>
	<li>The output list must be sorted by the x position.</li>
	<li>There must be no consecutive horizontal lines of equal height in the output skyline. For instance, [...[2 3], [4 5], [7 5], [11 5], [12 7]...] is not acceptable; the three lines of height 5 should be merged into one in the final output as such: [...[2 3], [4 5], [12 7], ...]</li>
</ul>


<br/>
<strong>Solution:</strong>
1. Sweep line with max-heap:

Notice that "key points" are either the left or right edges of the buildings. Therefore, we first obtain both the edges of all the N buildings, and store the 2N edges in a sorted array. Maintain a max-heap of building heights while scanning through the edge array: If the current edge is a left edge, then add the height of its associated building to the max-heap; if the edge is a right one, remove the associated height from the heap. Then we take the top value of the heap (yi) as the maximum height at the current edge position (xi). Now (xi, yi) is a potential key point. If yi is the same as the height of the last key point in the result list, it means that this key point is not a REAL key point, but rather a horizontal continuation of the last point, so it should be discarded; otherwise, we add (xi,yi) to the result list because it is a real key point. Repeat this process until all the edges are checked.

It takes O(NlogN) time to sort the edge array. For each of the 2N edges, it takes O(1) time to query the maximum height but O(logN) time to add or remove elements. Overall, this solution takes O(NlogN) time.

For C++ programmers: As appealing as the solution may sound, it is not particularly C++ friendly. As of yet, C++ standard still does not support removal of a non-top element from a heap in a portable way. If you are to try this solution in C++, you may need to implement your own heap structure or even resort to other libraries that supports the removal operation.

2. Divide and Conquer:

Divide the list of buildings into two halves. Recursively get the skyline of both halves, and then merge the two skylines in O(n) time (see if you can figure out this part yourself). According to Master's Theorem, this solution takes O(NlogN) time as well, the same as merge sort.

Be warned, my friend, thou art about to do some serious coding should thou dare this path. Dauntlessly define thy classes and meticulously do thy math. Listen to the prophecy if thou must, but do not let thy own sword idle with rust. By the journey's end, may thy toil and sweat be duly repaid, and no more interviews shalt thou again be afraid.

Analysis written by "@stellari":https://leetcode.com/discuss/user/stellari.