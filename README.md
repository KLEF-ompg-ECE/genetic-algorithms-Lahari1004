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
| Is solution valid (Yes / No) | Yes |

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

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
The biggest improvement happens during the first few generations when the value quickly increases from about 60 to around 75. After generation 10 the improvements become smaller. The curve then flattens, showing that the algorithm has converged to a near optimal solution.
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
When the mutation rate is very low (0.01), the algorithm improves quickly at first but then gets stuck because the population loses diversity. With a moderate mutation rate (0.05), the algorithm balances exploration and exploitation and converges smoothly. When the mutation rate is very high (0.30), the search becomes more random and convergence is slower, although it may still find a good solution.
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
The mutation rate of 0.30 produced the best final value of 78. The higher mutation introduces more diversity into the population, which helps the algorithm explore more combinations of items. This allowed the algorithm to discover a slightly better solution than the other mutation rates.
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 | 77|Fast improvement then stable convergence. |
| 2 — Mutation rate | mutation_rate = 0.30|78 | Higher mutation found a slightly better solution.|

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
The most important thing I learned about Genetic Algorithms is how parameters such as mutation rate affect the search process. Mutation helps maintain diversity in the population so that the algorithm does not get stuck in poor solutions. However, too much mutation can make the search too random and slow convergence. A balanced mutation rate helps the algorithm explore new possibilities while still improving good solutions over generations.
```

---

## Submission Checklist

- [x] Student name and ID filled in
- [x] Q1, Q2, Q3 answered
- [x] Experiment 1: table filled, packing list pasted, plot observation written
- [x] Experiment 2: results table filled (3 rows), observation and answer written
- [x] Summary table completed and reflection written
- [x] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
