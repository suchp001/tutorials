# Basic exercises in R

## Exercises

1. Write a program to print "Hello, World!" on the console.

2. Create a vector with numbers from 1 to 10 and calculate their sum.

3. Write a function to check if a given number is prime or not.

4. Create a matrix with dimensions 3x3 and fill it with random numbers. Find the maximum value in the matrix.

5. Write a program to calculate the factorial of a given number using a recursive function.

6. Create a data frame with two columns: "Name" and "Age". Populate the data frame with at least five rows of data.

7. Write a program to read a CSV file and display its contents on the console.

8. Write a function to calculate the mean, median, and mode of a given numeric vector.

9. Create a bar plot to visualize the frequency distribution of a categorical variable in a data frame.





## Solutions
1. Exercise:
```R
# Solution:
print("Hello, World!")
```

2. Exercise:
```R
# Solution:
numbers <- 1:10
sum(numbers)
```

3. Exercise:
```R
# Solution:
is_prime <- function(n) {
  if (n <= 1) {
    return(FALSE)
  }
  
  for (i in 2:(n-1)) {
    if (n %% i == 0) {
      return(FALSE)
    }
  }
  
  return(TRUE)
}

# Testing the function
is_prime(7)  # Output: TRUE
is_prime(10) # Output: FALSE
```

4. Exercise:
```R
# Solution:
matrix <- matrix(runif(9), nrow = 3)
max_value <- max(matrix)
max_value
```

5. Exercise:
```R
# Solution:
factorial <- function(n) {
  if (n <= 1) {
    return(1)
  }
  
  return(n * factorial(n-1))
}

# Testing the function
factorial(5)  # Output: 120
factorial(0)  # Output: 1
```

6. Exercise:
```R
# Solution:
data <- data.frame(
  Name = c("John", "Alice", "Michael", "Emma", "David"),
  Age = c(25, 32, 28, 35, 30)
)
data
```

7. Exercise:
```R
# Solution:
data <- read.csv("data.csv")  # Replace "data.csv" with the actual file name and path
data
```

8. Exercise:
```R
# Solution:
calculate_stats <- function(numbers) {
  mean_value <- mean(numbers)
  median_value <- median(numbers)
  mode_value <- as.numeric(names(table(numbers))[table(numbers) == max(table(numbers))])
  
  return(list(mean = mean_value, median = median_value, mode = mode_value))
}

# Testing the function
calculate_stats(c(1, 2, 2, 3, 4, 5, 5))  # Output: $mean = 3, $median = 3, $mode = 2
```

9. Exercise:
```R
# Solution:
data <- data.frame(
  Category = c("A", "B", "B", "C", "A", "A", "B", "C", "C", "C")
)
barplot(table(data$Category))
```


## Explaination

Exercise 3. The condition if (n %% i == 0) checks if n is divisible by the current value of i without a remainder (%% is the modulus operator in R).

Exercise 5. If the condition in the if statement is not met, the function proceeds to the next line return(n * factorial(n-1)). This line recursively calls the factorial function itself, passing n-1 as the argument. This is where the recursive nature of the function comes into play. In each recursive call, the function calculates the factorial of the number n-1 and multiplies it by n. This process continues until the base case is reached (when n becomes less than or equal to 1).

Exercise 8. **table(numbers)** generates a frequency table for the variable numbers. It counts the occurrences of each unique value in the numbers object and returns a table with the values as the names and the frequencies as the counts.
**max(table(numbers))** finds the maximum frequency in the table generated in the previous step. It determines the highest count among all the values in the numbers object.
**table(numbers) == max(table(numbers))** compares each count in the table with the maximum frequency. It creates a logical vector with TRUE for the counts that match the maximum frequency and FALSE for the rest.
**names(table(numbers))[table(numbers) == max(table(numbers))]** extracts the names from the table where the counts match the maximum frequency. It retrieves the values that correspond to the TRUE elements in the logical vector obtained in the previous step.
**as.numeric(...)** converts the extracted names into numeric values. This step ensures that the result is in a numeric format, allowing for further mathematical operations if needed.

