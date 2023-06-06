Exercises on the Iris dataset:

1. Load the necessary packages in R, including the `tidyverse` package.

2. Read the "iris" dataset into a tibble using the `as_tibble()` function.

3. Display the first 6 rows of the iris dataset.

4. Filter the iris dataset to include only the rows where the "Species" column is "versicolor".

5. Group the iris dataset by the "Species" column and calculate the mean values for each numerical variable.

6. Sort the iris dataset by the "Sepal.Length" column in descending order.

7. Create a new column in the iris dataset called "Petal.Area" that represents the product of "Petal.Length" and "Petal.Width".

8. Create a summary table that shows the count and average of "Sepal.Width" for each unique value of "Species" (i.e. for each row).

9. Write the transformed iris dataset to a new file named "transformed_iris.csv" in CSV format using the `write_csv()` function.

10. Create a scatter plot of sepal length (`Sepal.Length`) versus sepal width (`Sepal.Width`) using the `plot()` function.

11. Calculate the correlation coefficient between petal length (`Petal.Length`) and petal width (`Petal.Width`) in the Iris dataset using the `cor()` function.

12. Group the Iris dataset by species and calculate the mean petal width (`Petal.Width`) for each species using the `aggregate()` function.

13. Create box plots of sepal width (`Sepal.Width`) for each species in the Iris dataset using the `boxplot()` function.

14. Perform a t-test between the sepal length (`Sepal.Length`) of the "setosa" and "versicolor" species in the Iris dataset using the `t.test()` function.
