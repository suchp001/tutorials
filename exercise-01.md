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

11. Implement a simple guessing game where the user tries to guess a randomly generated number between 1 and 10. Provide feedback if the guess is too high or too low, and congratulate the user when they guess the correct number.





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

10. Exercise:
```R
# Solution:
guessing_game <- function() {
  answer <- sample(1:10, 1)
  attempts <- 0
  
  while (TRUE) {
    guess <- as.integer(readline("Enter your guess (between 1 and 10): "))
    
    if (guess < answer) {
      print("Too low!")
    } else if (guess > answer) {
      print("Too high!")
    } else {
      print("Congratulations! You guessed the correct number.")
      break
    }
    
    attempts <- attempts + 1
  }
  
  print(paste("Total attempts:", attempts))
}

# Run the game
guessing_game()
```

These are the solutions to the exercises. Feel free to ask if you have any questions or need further explanation!
