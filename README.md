# 30 Days of Pandas

Welcome to my 30 Days of Pandas challenge repository.

I am solving the LeetCode 30 Days of Pandas study plan to improve my Python, Pandas, and Data Analysis skills.

## Goals
- Learn Pandas fundamentals
- Improve problem-solving skills
- Build consistency through daily practice
- Create a public portfolio of Pandas solutions

## Progress

| Day | Problem | Status |
|------|---------|---------|
| 01 | Big Countries | ✅ Completed |

## Topics Covered
- DataFrame Filtering
- Boolean Indexing
- Column Selection
- Data Manipulation

## Platform
- LeetCode

## Author
Ali Asif Shaikh
B.Tech Computer Science & Engineering



# Day 2 - Recyclable and Low Fat Products

## Problem

Find the IDs of products that are both:

- Low Fat (`low_fats = 'Y'`)
- Recyclable (`recyclable = 'Y'`)

Return the result table in any order.

## Concepts Learned

- DataFrame Filtering
- Multiple Conditions
- AND Operator (`&`)
- Column Selection

## Solution

```python
import pandas as pd

def find_products(products: pd.DataFrame) -> pd.DataFrame:
    return products[
        (products["low_fats"] == "Y") &
        (products["recyclable"] == "Y")
    ][["product_id"]]
```

## Key Learning

- `&` is used for AND conditions in Pandas.
- Each condition should be wrapped in parentheses.
- Use double brackets `[["column"]]` to return selected columns.

## Status

✅ Accepted on LeetCode


