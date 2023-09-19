---
date: 2023-09-14
authors: [Daniel Wenbo]
title: Overflow in two's complement system
description: >
  A Brief Introduction to Overflow in two's complement system
categories:
  - NTU SCSE Resources
links:
comments: true
---

# Overflow in two's complement system

In this post, I will mainly discuss **two methods to detect overflow in two's
complement system and the reasons behind them**. Besides, some information about
**overflow bit, carry bit, sign bit and zero bit** in ALU, 
**the practical use of two's complement and unsigned binary system** will be
included.

<!-- more -->


## Two's complement system

According to [Wikipedia](https://en.wikipedia.org/wiki/Two%27s_complement),
two's complement is the most common method of representing signed (positive,
negative, and zero) integers on computers,[1]and more generally, fixed point
binary values. Two's complement uses the binary digit with the greatest place
value as the sign to indicate whether the binary number is positive or negative.
When the most significant bit is 1, the number is signed as negative; and when
the most significant bit is 0 the number is signed as positive.

When you study the two's complement, one important thing you can't avoid is to
learn how to detect the overflow. In the following section, I will introduce two
methods to detect overflow in two's complement system and the reasons behind
them.

!!! note
	In this post, our default is the addition and subtraction between
	**two numbers**. If you are facing the addition between more than two
	numbers, you can use the following method to detect the overflow between the
	first two numbers, and then use the result of the first two numbers to
	detect the overflow between the third number and the result of the first
	two numbers. Repeat this process until you get the final result.

## Two methods to detect overflow in two's complement

### Method 1: Compare the sign bit of operands and result
#### Conclusion

If the sign bit, also known as MSB(Most Significant Bit), of the two operands
are the same, but the sign bit of the result is different from the sign bit of
the operands, then the overflow occurs.

#### Reasons behind

1. __Why do we need to check whether the sign bit of the two operands are
the same?__

	Since if the sign bit of the two operands are different, the result will
	always be in the range of the two operands, which means the result will
	never overflow. Specifically speaking, if you subtract A from B, the result
	will always be smaller than B. Since both A and B are in the range which can
	be represented by two's complement, the result will also always be in the
	range which can be represented by two's complement. Thus,
	**no overflow will occur** when the sign bit of the two operands are
	different. Contrarally speaking, **overflow will only happen** when the sign
	bit of the two operands are the same.

2. __How to understand the [Conclusion](#conclusion)?__

	To rigorously prove that, the problem can be divided into two cases. 
	
	- case one:

		The sign bit of the two operands are both 0 while the sign bit of the
		result if 1. Before you move on, you need to know that in the two's
		complement system, if the sign bit is 0, it means that the number is
		positive. If the sign bit is 1, it means the number is negative. So,
		now let's go back to our case one. In case one, the sign bit of the two
		operands are both 0, which means the two operands are both positive.
		Since the sign bit of the result is 1, which means the result is
		negative. Now, you will find that when you add this two positive
		operands, you get a negative result. There must be something wrong! Yes,
		the result is out of the range which can be represented by two's
		complement. Thus, overflow occurs.

	- case two:
		  
		Now the sign bit of your two operands are both 1, while the sign bit of
		the result is 0. Similar with case one, now you will find that during
		this time, you add two positive number but get a negative number as the
		result. This time, you must be confident that an overflow has happened.

In conclusion, after analyzing these two cases, I have proved that the
[Conclusion](#conclusion) we have mentioned above is correct. Now, you may have 
a basic understanding of the overflow in two's complement system.

#### Implementation

### Method 2: Compare the carry-on bit and carry-out bit of the MSB column
#### Conclusion

If the carry-on bit and carry-out bit of the MSB column are different, then the
overflow occurs.

#### Reasons behind

To rigorously prove that, the problem can be divided into two cases since in a
binary system, we only have 0 and 1.

- case one:

  The carry-on bit is 1 and the carry-out bit is 0. So, in order to let the
  carry-out bit be 1, the sign bit of the two operands must be 0. (You can
  easily understand this by trying yourself. i.e. If any of the sign bit is 1,
  then 1 + 1 = 10, which will generate a carry-out bit of 1. Contraction!) Now,
  let's see the MSB column, which contains three numbers, above the line are the
  sign bits of two operands. Below the line is the sign bit of the result. Based
  on the previous statement, from top to bottom, the three numbers should be 0, 
  0, 1. Now, you will find that the sign bit of the result is different from the
  sign bit of the two operands. Based on what we have already discussed in 
  [Method 1](#method-1-compare-the-sign-bit-of-operands-and-result), you will
  find that an overflow has happened.

- case two:

  Now the carry-on bit is 0 and the carry-out bit is 1. Using the similar method
  discussed in **case one**, you can easily find that the overflow has happened.
  So, I won't repeat it here.

Now, [Method 2](#method-2-compare-the-carry-on-bit-and-carry-out-bit-of-the-msb-column)
has also been proved to be correct! Congratulations! Now, hope that you already
have a brand new undestanding of the overflow in two's complement system.

#### Implementation