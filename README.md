# MoiraStadiumBuildFinder
Brute forcer that can figure out the best items to select based on your cash, objective, available slots, etc.


# This code:
- Starts with a list of Moira-relevant stadium items (e.g., I didn't include max ammo items because they're either completely useless or barely give stats)
- You define flags for certain items; this changes item stats (e.g., advanced_nanobiotics = True assumes you're always getting the 10% attack speed boost)
- You define an objective to maximize (and other constraints like max_items, max_cost, mandatory_items, excluded_items)
- The code checks EVERY combination of items limited to these constraints and calculates its objective score and budget (total cost)
- If a new combination has a higher score than an older combination for a specific budget, the new one replaces it. *Ties are stored.
- Once all combinations are checked, this list of budgets and scores is reduced down by removing anything that is both more expensive and has a worse score than something cheaper. Ties aren't removed and are denoted by not having a divider (---------------------).
- Just before it's printed, these (*) ties mentioned earlier are checked for their (coal + dps) score, and whatever is higher is presented as the main suggestion. This form of tiebreaking means that if your objective was dps then the tiebreaker is coal, and vice versa. If there are multiple alternatives, the list is arbitrary.
