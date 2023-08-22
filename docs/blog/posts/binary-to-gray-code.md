---
date: 2023-08-15
authors: [Daniel Wenbo]
title: The conversion between Binary and Gray Code
description: >
  This post will teach you how to convert Binary to Gray Code and vice versa.
categories:
  - NTU SCSE Resources
links:
---

# The conversion between Binary and Gray Code
On the first class of SC1005, l was confused about Gray code and l found that many of my classmates were confused too. But now, after doing some research, l think l have a better understanding of Gray code. So l want to share my understanding with you. Hey, if you are still confused about Gray code, l hope this post can help you.

<!-- more -->

## What is Gray code?
[**The definition of Gray Code on Wikipedia**](https://en.wikipedia.org/wiki/Gray_code)
> The reflected binary code (RBC), also known as reflected binary (RB) or Gray code after Frank Gray, is an ordering of the binary numeral system such that two successive values differ in only one bit (binary digit). 

In short, the advantage of Gray code is that juts one bit changes for each step.

## How to convert Binary to Gray Code?
### Things you need to know before starting
1. The [**XOR operation**](https://www.baeldung.com/java-xor-operator)


### Binary to Gray code Conversion
1. The Most Significant Bit (MSB) of the gray code is always equal to the MSB of the given binary code.
2. Other bits of the output gray code can be obtained by XORing binary code bit at that index and previous index.

<p align="center"> <img src="/blog/binary-to-gray-code/Gray-Code1.png" title = "Binary code to gray code conversion"> </p>

### Gray code to Binary Conversion
1. The Most Significant Bit (MSB) of the binary code is always equal to the MSB of the given gray code.
2. Other bits of the output binary code can be obtained by checking the gray code bit at that index. If the current gray code bit is 0, then copy the previous binary code bit, else copy the invert of the previous binary code bit.

<p align="center"> <img src="/blog/binary-to-gray-code/Gray-Code2.png"> </p>

## Acknowledgement
- [**The definition of Gray Code on Wikipedia**](https://en.wikipedia.org/wiki/Gray_code)
- [**The XOR operation**](https://www.baeldung.com/java-xor-operator)
- [**The conversion between Binary and Gray Code**](https://www.geeksforgeeks.org/gray-to-binary-and-binary-to-gray-conversion/)
