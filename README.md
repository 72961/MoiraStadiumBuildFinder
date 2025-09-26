# MoiraStadiumBuildFinder
Brute forcer to find the best items to select at every budget range for an objective (e.g., right-click dps). Customizable to include specific items, set conditional item stats, etc.


# This code:
- Allows you to set the objective to maximize, such as right-click dps, coalescence dps, orb dps, etc.
- Uses a table of Moira-relevant Stadium items with their stats and costs (e.g., there are no max ammo items because they're irrelevant: useless or extremely cost inefficient)
- You set flags that affect the conditional stats of certain items (e.g., advanced_nanobiotics = True will assume Advanced Nanobiotics always has 10% attack speed)
- Other settings like mandatory_items or excluded_items force it to include item(s) in each combination or remove items from the item pool, respectively
- It then begins calculating the objective score and budget (total cost) of EVERY combination of items limited to these constraints
- During each brute force loop, it compares the score of a given item combination to the previous best score found at that exact budget. If the new item combination has a higher score, the new one replaces it. If the budget and score are tied, both are stored (one /multiple are presented as "Alternatives" in the final printout)
- Once all combinations are checked, this list of budgets and scores is reduced down further by removing any combination that is more expensive AND a worse score than a cheaper combination
- The divider (---------------------) denotes a different score between these budgets, while an empty line denotes no score difference
- Just before it's printed, the ties mentioned earlier ("Alternatives") are checked for their (coal + dps) score, and whatever is higher is presented as the main suggestion while the others are denoted "Alternatives". This form of tiebreaking means that if your objective was dps, then the tiebreaker is coal, and vice versa. If there are multiple alternatives, the order of the "Alternatives" list is arbitrary
- Additional information is calculated and shown below each combination
