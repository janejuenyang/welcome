# SQL Style Guide

Data practitioners write a lot of SQL. There are not industry-consistent standards for how to style SQL code. Here's what I prefer. Whenever you join a data team, ask what their standards are and if they don't have them, it could be valuable to co-create them for consistency across your code base.

## Standards

These style choices are required.

### Logic

- Optimize for readability, not conciseness in code
- Comment liberally, especially when logic is complicated
- Use CTEs instead of subqueries where possible, where each CTE performs one unit of logical work
- Specify join keys: do not use `using`
- Be explicit about your join (i.e. write `inner join` instead of `join`). Generally avoid `right join`s: they are an indicator you should switch the order of your tables in your `FROM` clause
- If joining two or more tables, always prefix your column names with the table alias. If only selecting from one table, prefixes are not needed.
- Use `union all`, not `union *`

### Spacing

- Indents should be four spaces
- Keep to 80 characters max per line. If your condition is lengthy, break into new lines at points that make sense based on the logic and indent appropriately (Note: a couple characters over 80 isn't the end of the world; use your common sense.)
- When a clause has multiple conditions, create a new line per condition and indent each line
- Enter blank newlines between CTEs to visually separate out the logic
- Put spaces around `=`

### Commas

- Use trailing commas, not leading

### Letter case

- Use all lowercase for field names
- Use uppercase for SQL function names

### Naming

- Use the `AS` keyword when aliasing a field or table
- Be as descriptive as possible with CTE names
- Never use <letter><number>, e.g. `c1`, `c2`, as table aliases

## Suggestions

These style choices have more flexibility though it is important to be consistent within a given document on how you style your SQL code.

- **Aliases**: avoid single-letter aliases; preference instead shortened table names, e.g. `cust` for `customers`
- **Boolean conditions**: be explicit about `= TRUE` or `= FALSE`

## Example code

```
WITH records AS (
    SELECT
        id,
        col1,
        col2,
        col3,
        CASE
            WHEN col5 = 1 THEN 'a'
            WHEN col5 = 2 THEN 'b'
            ELSE 'c'
        END AS col4
    # only one table, so no need to have table listed in separate line
    FROM table
    WHERE parameter = TRUE
),

# have a white space line between CTEs
aggregates_to_add AS (
    SELECT
        table.r_id,
        SUM(dim.col1) AS total_field
    FROM
        table
        LEFT JOIN dimensions AS dim ON table.id = dim.x_id
    GROUP BY 1
)

SELECT
    * EXCEPT(aggs.r_id)
FROM
    records
    LEFT JOIN aggregates_to_add AS aggs
        # multiple conditions on joins should be indented and aligned
        ON records.id = aggs.r_id
        AND records.created_at > aggs.created_at

```
