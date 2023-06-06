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


## Chandani

1.library(tidyverse)
2.data(iris)
iris_tibble <- as_tibble(iris)
print(iris_tibble)
3.head(iris,6)
4.data(iris)
ver <-filter(iris, Species == "versicolor")
print(ver)
5.mean_value <- iris %>%
group_by(Species) %>%
  summarise(mean(Sepal.Length),mean(Sepal.Width),mean(Petal.Length),mean(Petal.Width))
print(mean_value)
6.sorted <- iris %>%
  arrange(desc(Sepal.Length))
print(sorted)
7.iris <- iris %>%
  mutate(Petal.Area = Petal.Length * Petal.Width)
print(iris)
8.avgdata <- iris %>%
  summarise(avg_Sepal.Width=mean(Sepal.Width))
print(avgdata)
9.data(iris)
write_csv(iris, "iris.csv")
10.data(iris)
plot(iris$Sepal.Width, iris$Sepal.Length, xlab = "Sepal Width", ylab = "Sepal Length", main = "Scatter Plot of Sepal Length vs Sepal")
11.data(iris)
correlation <- cor(iris, Petal.Length,Petal.Width)
print(correlation)
12.mean_petal_width <- aggregate(Petal.Width ~ Species, data = iris, FUN = mean)
print(mean_petal_width)
13.boxplot(iris$Sepal.Width ~ Species, data = iris, xlab = "Species", ylab = "Sepal Width", main = "Box Plot of Sepal Width by Species")
14.setosa_sepal_length <- iris$Sepal.Length[iris$Species == "setosa"]
versicolor_sepal_length <- iris$Sepal.Length[iris$Species == "versicolor"]
result <- t.test(setosa_sepal_length, versicolor_sepal_length)
print(result)

## Keerthana
1.library(tidyverse)
2. as_tibble(iris)
3.iris[1:6,]
4.data(iris)
spe <- filter(iris, Species == "versicolor")
print(spe)
5.iris_means <- iris %>%
  group_by(Species) %>%
  summarise(mean_Sepal_length=mean(Sepal.Length),
            mean_Sepal_Width=mean(Sepal.Width),
            mean_Petal_length=mean(Petal.Length),
            mean_Petal_Width=mean(Petal.Width))
print(iris_means)
6.storted <- iris %>%
  arrange(desc(Sepal.Length))
7.datase <- iris %>%
  mutate(Petal.Area = Petal.Lenght*Petal.Width)
  print(datase)
8.avegdata <- iris %>%
  summarise(avg_Sepal.Width=mean(Sepal.Width))
  print(avegdata)
9.data(iris)
  write_csv(iris,"transformed_iris.csv")
10.data(iris)
plot(iris$Sepal.Length,iris$Sepal.Width, xlab = "Sepal.length",ylab = "Sepal.width",main = "Scatter Plot of Sepal Length vs Sepal Width")
11.data(iris)
correlation <- cor(iris,Petal.Length,Petal.Width)
print(correlation)
12.data(iris)
result <- aggregate(Petal.Width ~ Species, data = iris , FUN = mean)
print(result)
13.data(iris)
boxplot(Sepal.Width ~ Species, data = iris, xlab = "Species", ylab = "Sepal.Width",main = "boxplot of Species vs Sepal.Width")
14.
data(iris)
t_test_result <- t.test(iris$Sepal.Length[iris$Species == "setosa"], iris$Sepal.Length[iris$Species == "versicolor"])
print(t_test_result)


