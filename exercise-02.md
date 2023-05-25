# Tidyverse

## Exercises focused on handling tables in the tidyverse package


1. Load the tidyverse package and import the "mtcars" dataset.

2. Filter the "mtcars" dataset to include only rows where the number of cylinders is greater than or equal to 6.

3. Sort the filtered dataset from exercise 2 in descending order of horsepower (hp).

4. Create a new column called "hp_to_weight_ratio" in the filtered and sorted dataset from exercise 3, which represents the ratio of horsepower (hp) to weight (wt).

5. Group the dataset from exercise 4 by the number of gears (gear) and calculate the average horsepower (hp) and weight (wt) within each group.

6. Reshape the dataset from exercise 5 using the `pivot_longer()` function to convert the gear column into a new column called "variable" and the corresponding values into a new column called "value".

7. Use the `spread()` function to reshape the dataset from exercise 6 back to its original form.

8. Create a summary table that shows the count and average miles per gallon (mpg) for each unique combination of cylinders (cyl) and gears (gear).

9. Perform an inner join between the "mtcars" dataset and the "iris" dataset based on a common variable. Choose any common variable of your choice.

10. Create a new table that shows the top 3 cars with the highest miles per gallon (mpg) from the "mtcars" dataset, including their respective model names.



# Solutions


1. Load the tidyverse package and import the "mtcars" dataset.

```R
# Solution:
library(tidyverse)
data(mtcars)
```

2. Filter the "mtcars" dataset to include only rows where the number of cylinders is greater than or equal to 6.

```R
# Solution:
filtered_data <- mtcars %>%
  filter(cyl >= 6)
```

3. Sort the filtered dataset from exercise 2 in descending order of horsepower (hp).

```R
# Solution:
sorted_data <- filtered_data %>%
  arrange(desc(hp))
```

4. Create a new column called "hp_to_weight_ratio" in the filtered and sorted dataset from exercise 3, which represents the ratio of horsepower (hp) to weight (wt).

```R
# Solution:
data_with_ratio <- sorted_data %>%
  mutate(hp_to_weight_ratio = hp / wt)
```

5. Group the dataset from exercise 4 by the number of gears (gear) and calculate the average horsepower (hp) and weight (wt) within each group.

```R
# Solution:
grouped_data <- data_with_ratio %>%
  group_by(gear) %>%
  summarize(avg_hp = mean(hp), avg_wt = mean(wt))
```

6. Reshape the dataset from exercise 5 using the `pivot_longer()` function to convert the gear column into a new column called "variable" and the corresponding values into a new column called "value".

```R
# Solution:
reshaped_data <- grouped_data %>%
  pivot_longer(cols = -gear, names_to = "variable", values_to = "value")
```

7. Use the `spread()` function to reshape the dataset from exercise 6 back to its original form.

```R
# Solution:
original_data <- reshaped_data %>%
  spread(key = variable, value = value)
```

8. Create a summary table that shows the count and average miles per gallon (mpg) for each unique combination of cylinders (cyl) and gears (gear).

```R
# Solution:
summary_table <- mtcars %>%
  group_by(cyl, gear) %>%
  summarize(count = n(), avg_mpg = mean(mpg))
```

9. Perform an inner join between the "mtcars" dataset and the "iris" dataset based on a common variable. Choose any common variable of your choice.

```R
# Solution:
joined_data <- inner_join(mtcars, iris, by = "cyl")  # Example: Joining based on "cyl"
```

10. Create a new table that shows the top 3 cars with the highest miles per gallon (mpg) from the "mtcars" dataset, including their respective model names.

```R
# Solution:
top_cars <- mtcars %>%
  top_n(3, mpg) %>%
  select(model = row.names(.), mpg)
```
