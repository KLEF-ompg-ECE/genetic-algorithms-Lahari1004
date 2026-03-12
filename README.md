# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :** Dasari Lahari 
**Student ID    :** 2310040036
**Date Submitted:** 11-03-2026

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `ga_knapsack.py` and read through it. Then answer these questions.

**Q1. What does the `fitness()` function return? Why does an overweight solution score 0?**

```
The fitness() function calculates the total value of the selected items in the knapsack. If the total weight exceeds the maximum allowed weight, the function returns 0. This prevents the genetic algorithm from selecting invalid solutions that exceed the weight limit.
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
The tournament_select() function randomly selects a small group of individuals from the population and chooses the one with the highest fitness. This means better solutions have a higher chance of being selected. 
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
The line next_gen = [best_chromosome[:]] copies the best solution from the current generation to the next generation. It ensures that the best solution found so far is never lost during crossover or mutation.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations |50|
| Best value at generation 1 |60|
| Final best value |77|
| Total weight of best solution (kg) |14.4/15.0 kg|
| Is solution valid (Yes / No) | Yes|

**Copy the printed packing list here:**
```
Best Packing List
--------------------------------------
  + Water bottle
  + First aid kit
  + Sleeping bag
  + Torch
  + Energy bars (x6)
  + Rain jacket
  + Map & compass
  + Cooking stove
  + Rope (10 m)
  + Sunscreen
  + Power bank
--------------------------------------
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
The biggest improvement happens in the first few generations, where the best value quickly increases from around 60 to about 75. After that, the improvements become smaller and the curve rises slowly until it reaches about 77. The curve then flattens, showing that the genetic algorithm has converged and found a near-optimal solution.
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         |    75           |14.9/15.0 kg |  Yes   |Rapid early improvement then flat|
| 0.05         |    77           |14.4/15.0 kg |  Yes   |Fast rise then gradual plateau.|
| 0.30         |    78           |14.1/15.0 kg |  Yes   |Gradual rise with stepwise improvements, then plateau.|

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
When mutation is too low (0.01), the algorithm improves early but quickly gets stuck due to low diversity. When mutation is too high (0.30), the search becomes more random and improvements are slower, while a moderate rate (0.05) balances exploration and convergence.
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
The mutation rate of 0.30 gave the best final value (78). This may happen because the higher mutation introduces more diversity in the population, allowing the algorithm to explore more possible combinations and eventually find a slightly better solution. However, it also causes slower convergence compared to the moderate mutation rate.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 | | |
| 2 — Mutation rate | mutation_rate = ___ | | |

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
[ YOUR REFLECTION ]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
