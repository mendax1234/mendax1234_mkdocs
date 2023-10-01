---
date: 2023-10-01
authors: [Daniel Wenbo]
title: VHDL Introduction
description: >
  A bried introduction to VHDL
categories:
  - NTU SCSE Resources
comments: true
links:
---

# VHDL Introduction
A short and brief introduction to VHDL.

<!-- more -->

## About VHDL

VHDL stands for VHSIC(Very High Speed Integrated Circuit) Hardware Description
Languague, and resulted from an initiative funded by the U.S. Department of 
Defense in the 1980s.

VHDL allows circuit synthesis as well as circuit simulation. The former is the
translation of a source code into a hardware structure that implements the
intended functionality, while the latter is a testing procedure to ensure that 
such functionality is indeed achieved by the synthesized circuit.

## Design Flow

<p align="center"> <img src="/blog/vhdl-intro/design-flow.png" title = "Design Flow"> </p>

## Number and Character Representation in VHDL

### Integers
Examples:

- Base 10(decimals): 5, 32, 3250, 3_250, 3E2(=3*10^2)
- Other bases:

    2#0111# (this is the integer 7)

    16#9F# (this is the integer 159)
    
    3#201#E4 ((2*3^2+0*3^1+1*3^0)*3^4 = 1539)

!!! note
    The underscore character is used to improve readability of numbers. It can
    be used anywhere in a number except at the beginning or end, with no effect
    on the synthesized value.

### Binary Values

- Regular binary form:

    '0'(=0), b'0111'(=7), B'11110000'(=240)

- Octal and hexadecimal forms:

    o'77'(=63), O'77'(=63), x'FF'(=255), X'FF'(=255)

!!! note
    VHDL is not case sensitive, so '0' and 'O' are the same, and 'x' and 'X' are
    the same.

### Characters
Characters from an extended ASCII table are synthesizable. A single character is
represented by a pair of single quotes, while a string of characters(also
synthesizable) is represented by a pair of double quotes.
e.g. 'A', "mp3"