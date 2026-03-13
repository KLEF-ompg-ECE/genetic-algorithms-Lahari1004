# Assignment 2 — Genetic Algorithm: Knapsack Problem

## Observation Report

**Student Name  :** Dasari Lahari
**Student ID    :** 2310040036
**Date Submitted:** 11-03-2026

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

The fitness() function calculates the total value of the selected items in the knapsack. If the total weight exceeds the maximum allowed weight, the function returns 0. This prevents the genetic algorithm from selecting invalid solutions that exceed the weight limit.

---

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

The tournament_select() function randomly selects a small group of individuals from the population and chooses the one with the highest fitness. This means better solutions have a higher chance of being selected.

---

**Q3. Look at the `run_ga()` loop. Find this line:**

`next_gen = [best_chromosome[:]]`

**What is this doing? Why is it important to always keep the best solution?**

The line copies the best solution from the current generation to the next generation. It ensures that the best solution found so far is never lost during crossover or mutation.

---

# Experiment 1 — Baseline Run

Run the program without changing anything.

| Metric                             | Your result |
| ---------------------------------- | ----------- |
| Number of generations              | 50          |
| Best value at generation 1         | 60          |
| Final best value                   | 77          |
| Total weight of best solution (kg) | 14.4 / 15.0 |
| Is solution valid (Yes / No)       | Yes         |

---

**Copy the printed packing list here:**

```
Best Packing List
--------------------------------------
+ Water bottle
+ First aid kit
+ Tent
+ Torch
+ Energy bars (x6)
+ Rain jacket
+ Map & compass
+ Camera
+ Cooking stove
+ Sunscreen
+ Power bank
--------------------------------------
```

---

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**

The biggest improvement happens in the first few generations where the value quickly increases from around 60 to about 75. After generation 10 the improvements become smaller. The curve then flattens, showing that the algorithm has converged to a stable solution.

---

# Experiment 2 — Effect of Mutation Rate

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve                 |
| ------------- | ---------------- | ----------- | ------ | ------------------------------ |
| 0.01          | 75               | 14.9        | Yes    | Rapid improvement then plateau |
| 0.05          | 77               | 14.4        | Yes    | Fast rise then gradual plateau |
| 0.30          | 78               | 14.1        | Yes    | Gradual rise then plateau      |

---

**Compare the three plots. What happens when mutation is too low? Too high?**

When the mutation rate is too low, the algorithm improves quickly but can get stuck because there is not enough diversity in the population. When the mutation rate is too high, the search becomes more random and convergence becomes slower. A moderate mutation rate balances exploration and exploitation.

---

**Which mutation_rate gave the best result? Why do you think that is?**

The mutation rate of **0.30** produced the best final value of 78. Higher mutation introduces more diversity, allowing the algorithm to explore more combinations of items and discover slightly better solutions.

---

# Summary

| Experiment    | Key setting          | Final value | Main finding                                   |
| ------------- | -------------------- | ----------- | ---------------------------------------------- |
| Baseline      | mutation_rate = 0.05 | 77          | Fast improvement then convergence              |
| Mutation rate | mutation_rate = 0.30 | 78          | Higher mutation found slightly better solution |

---

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments?**

The most important thing I learned about Genetic Algorithms is how parameters like mutation rate affect the search process. Mutation helps maintain diversity so the algorithm does not get stuck in poor solutions. However, too much mutation can make the search random and slow convergence. A balanced mutation rate helps the algorithm explore new possibilities while still improving good solutions.

## Submission Checklist

- [x] Student name and ID filled in
- [x] Q1, Q2, Q3 answered
- [x] Experiment 1: table filled, packing list pasted, plot observation written
- [x] Experiment 2: results table filled (3 rows), observation and answer written
- [x] Summary table completed and reflection written
- [x] plots/ contains: experiment_1.png, experiment_2a.png, experiment_2b.png, experiment_2c.png
