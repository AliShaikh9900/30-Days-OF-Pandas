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
 LeetCode

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
# Day 4 - Customers Who Never Order

## Problem
Find all customers who never placed any order.

## Approach
1. Use `isin()` to check whether customer IDs exist in the Orders table.
2. Use `~` to select customers whose IDs are not present.
3. Return only the customer names.
4. Rename the output column to `Customers`.

## Pandas Concepts Used
- Boolean Filtering
- `isin()`
- Column Selection
- `rename()`

## Solution

```python
import pandas as pd

def find_customers(customers: pd.DataFrame, orders: pd.DataFrame) -> pd.DataFrame:

    result = customers[
        ~customers['id'].isin(orders['customerId'])
    ]

    return result[['name']].rename(
        columns={'name': 'Customers'}
    )
# Day 3 - Article Views I

## Problem
Find all authors who viewed at least one of their own articles.

## Approach
1. Filter rows where `author_id` equals `viewer_id`.
2. Select the `author_id` column.
3. Remove duplicate authors.
4. Sort in ascending order.
5. Rename the column to `id`.

## Pandas Concepts Used
- Boolean Filtering
- Column Selection
- drop_duplicates()
- sort_values()
- rename()

## Solution

```python
import pandas as pd

def article_views(views: pd.DataFrame) -> pd.DataFrame:

    result = views[
        views['author_id'] == views['viewer_id']
    ]

    return (
        result[['author_id']]
        .drop_duplicates()
        .sort_values('author_id')
        .rename(columns={'author_id': 'id'})
    )
```

## Time Complexity
O(n)

## What I Learned
- Comparing two DataFrame columns
- Filtering matching rows
- Removing duplicates
- Sorting data
- Renaming columns

- # Day 5 - Invalid Tweets

## Problem
Find the IDs of tweets whose content contains more than 15 characters.

## Approach
1. Calculate the length of each tweet using `str.len()`.
2. Filter rows where length is greater than 15.
3. Return only the `tweet_id` column.

## Pandas Concepts Used
- String Operations
- str.len()
- Boolean Filtering
- Column Selection

## Solution

```python
import pandas as pd

def invalid_tweets(tweets: pd.DataFrame) -> pd.DataFrame:

    return tweets[
        tweets['content'].str.len() > 15
    ][['tweet_id']]
```

## Time Complexity
O(n)

## What I Learned
- Working with string columns
- Using `str.len()`
- Filtering rows based on string length
- Returning selected columns

- # Day 6 - Calculate Special Bonus

## Problem
Calculate the bonus of each employee.

Rules:
- Employee ID must be odd.
- Employee name must not start with "M".
- Bonus equals salary if both conditions are satisfied.
- Otherwise, bonus is 0.

## Approach
1. Create a bonus column initialized with 0.
2. Check employees with odd IDs.
3. Exclude employees whose names start with "M".
4. Assign salary as bonus for matching employees.
5. Return employee_id and bonus sorted by employee_id.

## Pandas Concepts Used
- Boolean Filtering
- String Operations
- str.startswith()
- loc[]
- sort_values()

## Solution

```python
import pandas as pd

def calculate_special_bonus(employees: pd.DataFrame) -> pd.DataFrame:

    employees['bonus'] = 0

    condition = (
        (employees['employee_id'] % 2 == 1)
        &
        (~employees['name'].str.startswith('M'))
    )

    employees.loc[condition, 'bonus'] = employees['salary']

    return employees[['employee_id', 'bonus']].sort_values('employee_id')
```

## Time Complexity
O(n)

## What I Learned
- Using multiple conditions in Pandas
- Working with string filters
- Using str.startswith()
- Updating values using loc[]
- Sorting DataFrames

