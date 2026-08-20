# London Police Use of Force Analysis (R)

An exploratory data analysis of a real-world dataset of over 75,000 police use-of-force incidents from the London area, built in R using the tidyverse. The project simulates responding to public records (Freedom of Information) requests by extracting specific statistics from the data and visualizing patterns across boroughs, demographics, and tactics used.

## Dataset

- **Source:** London police use-of-force incident reports
- **Size:** 75,429 rows, 45 columns
- **Date range:** July 1, 2020 – December 31, 2020
- Includes fields on subject demographics (age, gender, ethnicity), tactics used, location, contributing factors (e.g., alcohol involvement), and incident outcomes

## Built With

- **R** / **RStudio**
- **tidyverse** (dplyr, stringr, ggplot2, forcats)

## What's in This Repo

- `code23.Rmd` — data exploration and targeted queries: filtering, string detection, and summarizing incident counts by category (e.g., tactics involving dogs, handcuffing, irritant sprays, Tasers)
- `code24.Rmd` — frequency tables and data visualization: building and reordering summary tables, and creating single- and two-variable bar charts (e.g., incidents by borough, age, gender, and ethnicity)
- Dataset CSV used for the analysis

## Key Techniques Used

- **Filtering and pattern matching** with `filter()`, `str_detect()`, and regular expressions (e.g., using `^` anchors to correctly isolate dates by month and avoid substring overcounting)
- **Frequency tables** with `count()` and `summarize()`, including custom column naming and sorting
- **Factor reordering** with `fct_infreq()` and `fct_rev()` to control bar chart ordering (frequency-based vs. natural/ordinal order)
- **Data visualization** with `ggplot2`, including single-category and two-category (stacked and side-by-side) bar plots
- **Group-level filtering** with `group_by()` and `n()` to isolate boroughs exceeding an incident threshold

## Example Analysis

One exercise involved identifying an overcounting bug: searching for the substring `"7/"` to isolate July incidents also matched dates like `8/17/2020` and `9/17/2020`. This was corrected using the regex anchor `"^7/"` to match only dates beginning with `7/`.

## What I Learned

- How to build reusable code patterns for answering ad hoc data questions, rather than writing one-off queries each time
- The importance of testing filter logic against edge cases (like the date-overcounting bug above) rather than trusting a first-pass result
- How to reorder categorical data for visualization purposes without altering the underlying data
