---
layout:     post
title:      "Hall of Mirrors 3"
subtitle:   " \"Jane Street puzzle\""
date:       2025-03-23 22:10:00
author:     "Mickle"
header-img: "img/new/JaneStreet_icon.jpg"
catalog: true
mathjax: true
tags:
    - competition
    - math
---

## Hall of Mirrors 3 <br> (March 2025 : Puzzle)

![Hall of Mirrors 3](/img/in-post-new/Hall_of_Mirrors_3.jpg)

The perimeter of a 10-by-10 square field is surrounded by lasers pointing into the field. (Each laser begins half a unit from the edge of the field, as indicated by the •’s.)

Some of the lasers have numbers beside them. Place diagonal mirrors in some of the cells so that the product of the segment lengths of a laser’s path matches the clue numbers. (For instance, the segments for the “75” path in the example puzzle have lengths 5, 3, 5.) Mirrors may not be placed in orthogonally adjacent cells.

Once finished, determine the missing clue numbers for the perimeter, and calculate the sum of these clues for each side of the square. The answer to this puzzle is the product of these four sums.

### Answer
This is a very interesting problem. First, let's briefly analyze it and derive some rules:

1. Each of the 4 sides has 10 numbers, totaling 40 numbers. Since they come in pairs, there are 20 light beams. We see that the given conditions provide only 16 values, which correspond to 14 different numbers.

2. Some information comes from the 10×10 chart, and some comes from factorization. The latter can be quite complex—it's simpler for smaller numbers, but once the numbers are larger, a 1 can be distributed at the beginning and the end, while no 1 can appear in the middle (Mirrors may not be placed in orthogonally adjacent cells).

3. Start reasoning from the scenario with the fewest possibilities (ideally a unique number), while also mapping out the cells where mirrors are placed and those where they cannot be placed. The restrictions on placing mirrors come from two aspects:
  a. Mirrors may not be placed in orthogonally adjacent cells.
  b. Once a light beam's path is determined, no additional mirrors can be added along that path.

Based on these rules, after some exploration we have arrived at the following reasoning process and results.

1 → 4 → 9 → 12 → 5 → 3087 → 27(left) → 16 → 112 → 225 → 2025 → 27(right)&405 → 48

![Answer of Hall of Mirrors 3](/img/in-post-new/Answer_Hall_of_Mirrors_3.png)

## Websites

[Hall of Mirrors 3](https://www.janestreet.com/puzzles/hall-of-mirrors-3-index/)

[The simulator of puzzle](https://ouatu.ro/project/hall-of-mirrors-3/)
