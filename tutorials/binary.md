---
title: "The Line Follower & Binary"
tags: [Binary]
keywords:
sidebar: tutorials
permalink: line_follower_binary.html
---


### Binary Code

Oddly enough, now is a good time to discuss binary.

We all know that computers represent data as 1s and 0s, but what does that really mean? Well, it's about to become immediately relevant to your ability to program this robot.

Binary is called a numerical base.

Decimal is the base that we are used to, where there are 10 digits (0-9), and we add additional digits to make bigger numbers.

In binary, there are two digits (0 & 1), and we add additional digits to make bigger numbers.

Binary was chosen as the numerical system for computers because computers use transistors, which can be thought of as switches which only go on or off, to represent basically everything. Since a switch can only be on or off, this naturally maps to there being two values for each digit in the computer's number system. Hence binary.

Each switch, a 1 or 0 is called a bit.

8 bits make a byte.

{{ site.data.alerts.tip }}
<ul>
<li>If you have heard of 8-bit, 16-bit, 32-bit, or 64-bit computer architectures, this refers to the number of bits used to represent an integer and other basic things in the computer.</li>
<li>Notice that the lengths are all powers of two. This is no mistake. Using powers of two is typically more efficient when designing things for computers.</li>
</ul>
{{ site.data.alerts.end }}

We need to know a couple more things before we can understand binary. We need to quickly understand exponents.

Left-Hand-Side    | Equals
--------|-------------
2	| 2
2 * 2	    |4
2 * 2 * 2	| 8
2 * 2 * 2 * 2	| 16

We can also state these as exponents, which just means multiplying the number by itself as many times as is in the exponent.

Left-Hand-Side    | Exponent    | Equals
--------|-------------|-------------
2	| 2<sup>1</sup>	| 2
2 * 2	    | 2<sup>2</sup>	    |4
2 * 2 * 2	| 2<sup>3</sup>	| 8
2 * 2 * 2 * 2	| 2<sup>4</sup>	| 16

Okay, but here's one which will really blow your mind if you haven't seen it before.

 Exponent    | Equals
-------------|-------------
2<sup>0</sup>	| 1

{{ site.data.alerts.tip }}
Explaining this would really get the camp off-course, but if you are curious, you can learn more <a href="http://scienceline.ucsb.edu/getkey.php?key=2626">here</a>.
{{ site.data.alerts.end }}

