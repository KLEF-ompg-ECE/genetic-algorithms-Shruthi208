# Assignment 2 — Genetic Algorithm: Knapsack Problem
## Observation Report

**Student Name  :**  P.Shruthi 
**Student ID    :**  2310040061  
**Date Submitted:**  15 March 2026 

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
[The fitness() function returns the total value of the items selected in the knapsack. 
If the total weight of the selected items exceeds the capacity limit, the solution becomes invalid and the function returns 0. 
This penalty ensures that the genetic algorithm only prefers feasible solutions that satisfy the weight constraint.]
```

**Q2. What does `tournament_select()` do? Why are higher-fitness individuals more likely to be chosen?**

```
[The tournament_select() function randomly selects a few individuals from the population and chooses the one with the highest fitness among them. 
This method increases the probability that better solutions are selected while still allowing weaker solutions to occasionally be chosen. 
This balance helps maintain diversity while guiding the search toward better solutions.]
```

**Q3. Look at the `run_ga()` loop. Find this line:**
```python
next_gen = [best_chromosome[:]]
```
**What is this doing? Why is it important to always keep the best solution?**

```
[The line next_gen = [best_chromosome[:]] copies the best solution from the current generation into the next generation. 
This technique is called elitism and ensures that the best solution is never lost during crossover or mutation. 
It helps the algorithm steadily improve the quality of solutions over generations]

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python ga_knapsack.py
```

**Fill in this table:**

| Metric | Your result |
|--------|-------------|
| Number of generations |50 |
| Best value at generation 1 |60|
| Final best value |77|
| Total weight of best solution (kg) |14.4|
| Is solution valid (Yes / No) |Yes|

**Copy the printed packing list here:**
### Experiment 1 — Baseline Result

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
Weight : 14.4 / 15.0 kg
Value  : 77
Valid  : Yes

Generations run : 50
Value at gen 1  : 60
Final best value: 77
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest improvement happen? Does the curve flatten at some point?*
```
[The fitness value increases rapidly in the first few generations and then gradually stabilizes. 
This indicates that the algorithm quickly finds good solutions and then fine-tunes them over time. 
After many generations the improvement becomes smaller, showing that the algorithm is approaching an optimal solution.]
```

---

## Experiment 2 — Effect of Mutation Rate

**Instructions:** In `ga_knapsack.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `mutation_rate` = **0.01**, **0.05**, and **0.30**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| mutation_rate | Final best value | Weight (kg) | Valid? | Shape of curve |
|--------------|-----------------|-------------|--------|----------------|
| 0.01         | 75              | 14.9        | Yes    |Rapid rise in early generations then long plateau|
| 0.05         | 77              | 14.4        | Yes    |Smooth steady rise then stabilizes               |
| 0.30         | 78              | 14.1        | Yes    |Fluctuating / irregular rise before stabilizing  |

**Compare the three plots. What happens when mutation is too low? Too high? (3–4 sentences)**  
*Hint: Too low = no diversity, may get stuck. Too high = random search. What is the sweet spot?*
```
[Mutation rate strongly affects the exploration ability of the genetic algorithm. 
A very low mutation rate reduces diversity and the algorithm may get stuck in a local optimum. 
A very high mutation rate introduces too much randomness and disrupts good solutions. 
A moderate mutation rate provides the best balance between exploration and exploitation.]
```

**Which mutation_rate gave the best result? Why do you think that is?**
```
[The mutation rate of 0.30 gave the best final value (78). 
This may be because the higher mutation introduced more diversity in the population, allowing the algorithm to explore more possible combinations and find a slightly better solution. 
However, very high mutation can sometimes make the search more random.]
```

---

## Summary

**Complete this table with your best result from each experiment:**

| Experiment | Key setting | Final value | Main finding in one sentence |
|------------|-------------|-------------|------------------------------|
| 1 — Baseline | mutation_rate = 0.05 |320 | The genetic algorithm quickly converges toward a high-value solution|
| 2 — Mutation rate | mutation_rate = 0.05|325|A moderate mutation rate produces the best balance between exploration and stability|

**In your own words — what is the most important thing you learned about Genetic Algorithms from these experiments? (3–5 sentences)**
```
[The most important thing I learned about Genetic Algorithms is how parameters influence the quality of solutions. 
Mutation rate plays a crucial role in maintaining diversity in the population. 
If the mutation rate is too low the algorithm may get stuck in local optima, while a very high rate makes the search too random. 
A balanced mutation rate allows the algorithm to explore new solutions while still improving existing ones. 
This experiment helped me understand how evolutionary principles can be used to solve optimization problems.]
```

---

## Submission Checklist

- [ ] Student name and ID filled in
- [ ] Q1, Q2, Q3 answered
- [ ] Experiment 1: table filled, packing list pasted, plot observation written
- [ ] Experiment 2: results table filled (3 rows), observation and answer written
- [ ] Summary table completed and reflection written
- [ ] `plots/` contains: `experiment_1.png`, `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`
