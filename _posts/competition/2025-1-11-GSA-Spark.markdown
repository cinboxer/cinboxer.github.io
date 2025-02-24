---
layout:     post
title:      "GSA Spark summary"
subtitle:   " \"GSA Spark 比赛总结\""
date:       2025-01-11 13:10:00
author:     "Mickle"
header-img: "img/new/GSA_Capital.svg"
catalog: true
mathjax: true
tags:
    - competition
    - code
---

# Details

- **Day 1**: Very simple, just write python code to sum the numbers between 1 and n.
- **Day 2**: Using Bayes' Theorem to Calculate Posterior Probability

  ## **Bayes' Theorem Formula**

  $$
  P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}
  $$

  Where:

  - **$ P(A\|B) $**: The posterior probability of $ A $ given $ B $ (the probability of $ A $ after observing $ B $).
  - **$ P(B\|A) $**: The likelihood (the probability of observing $ B $ given $ A $).
  - $ P(A) $: The prior probability of $ A $ (our initial belief about $ A $ before observing $ B $).
  - $ P(B) $: The marginal probability of $ B $ (the total probability of observing $ B $ under all possible scenarios).
  <br>
  > ⚠️ **Warning:** The prerequisite for using the **law of total probability** is that the events $ B_1, B_2, \dots, B_n $ are **mutually exclusive** (i.e., pairwise disjoint) and their union forms the **entire sample space** (i.e., they cover all possible outcomes).

