---
title       : Homework 1
description : What Is Data Science?
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf


--- type:NormalExercise xp:100 skills:1 key:15d729634a
## Pulling Data From Dataframe

We are going to reproduce the following output by defining a dataframe *df*

*[1] May Aug*
*Levels: Aug Feb Mar May Oct*

Complete the instructions in the console pane according to instructions

*** =instructions

In the editor on the right there is already some sample code. Complete entry according to the following instructions:

- The first column *x* has been added for you
- Complete entries for *y* to contain the values "May", "Oct", "Mar", "Aug", "Feb".  Complete entries for *z* to contain the values 2010, 2015, 2018, 2017, 2019.
- Print current dataframe
- Complete the selection using row, column indicator and assign results to variable *y1*
- Print contents of *y1*
- Use the *$* operator to select same values from column *y* and assign results to variable *y2*.  
- Specify 2 arguments for *all.equal*, the variables *y1* and *y2*

*** =hint
- The *c()* combine function works for all types of vectors not just numeric
- Keep in mind that referencing values from dataframe we specify 2 dimensions, row then column
- When using *c()* function for selection, the values in *c()* are the indices desired for row or column dimension from dataframe
- Keep in mind when working with *$* operator that you are now working with a 1-dimensional vector.  You only need to specify 1 dimension.

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Complete the df definition
df <- data.frame(
    x = c("H", "N", "T", "W", "V"), 
    y = c("May", "Oct", ____, ____, "Feb"), 
    z = c(2010, ____, 2018, ____, 2019)
)

# Print the current dataframe
print(df)

# Modify row values to select desired rows, and assign to variable y1
df[c(1, ____), "y"]

# Print contents of *y1*
print(____)

# Select row values using $ operator, and assign to variable y2
df____y[c(____)]

# Print contents of y2
print(____)

# Determine if y1 and y2 are equivalent
all.equal(____,____)

```

*** =solution
```{r}
# Complete the df definition
df <- data.frame(
    x = c("H", "N", "T", "W", "V"), 
    y = c("May", "Oct", "Mar", "Aug", "Feb"), 
    z = c(2010, 2015, 2018, 2017, 2019)
)

# Print the current dataframe
print(df)

# Modify row values to select desired rows, and assign to variable *y1*
y1 <- df[c(1, 4), "y"]

# Print contents of *y1*
print(y1)

# Select row values using $ operator, and assign to variable *y2*
y2 <- df$y[c(1,4)]

# Print contents of *y1*
print(y2)

# Determine if *y1* and *y2* are equivalent
all.equal(y1,y2)


```

*** =sct
```{r}
test_object("df",
            undefined_msg = "Don't remove the definition of dataframe *df*.",
            incorrect_msg = "Look at your df definition and compare to original requirements.  Order of entries is important.")

test_object("y1",
            undefined_msg = "Did you select row values and assign to variable *y1*?")

test_object("y2",
            undefined_msg = "Did you select row values and assign to variable *y2*?")

test_output_contains("y1", incorrect_msg = "Did your output for *y1* match to our desired outcome?")

test_output_contains("y2", incorrect_msg = "Did your output for *y2* match to our desired outcome?")

test_output_contains(TRUE, incorrect_msg = "Did *y1* and *y2* match?")

success_msg("Nice work.  Dataframes do not always exist when we start EDA.  We can build from scratch using *data.frame* function with named vectors representing each column of interest.  As we continue in the course, we will learn additional ways to create dataframes beyond the built in datasets we explored in DATA200.")

```


--- type:NormalExercise xp:100 skills:1 key:47d81b7a82
## EDA Goal One

Let's practice EDA Goal One, Getting Familiar With Data, for base dataset *mtcars*

Complete the instructions in the console pane according to instructions

*** =instructions

In the editor on the right, complete the code according to the following instructions:

- Pull up code book for *mtcars* using *help()* function
- Evaluate the structure of *mtcars* to confirm it aligns with help documentation
- Use the *dim()* function to confirm the dimensions, # rows by # columns
- Use the *summary()* function to get an initial set of descriptive statistics
- Confirm there are no missing rows using *sum* and *complete.cases*
- Generate a histogram for the *mpg* column, use *main* argument to set the title to "Histogram of mtcars mpg", use *xlab* to set the xlabel to "mpg"
- Generate a density plot for the *mpg* column by generating the density curve, and then using *plot* to plot the result, set the title to "Density curve of mtcars mpg", set xlabel to "mpg"

*** =hint
- Use *str()* to identify structure
- Use *dim()* to confirm rows and columns
- *summary()* with the name of the dataframe
- *complete.cases()* is run against the full dataframe to create logical vector, then *sum* against the vector determines total number of complete cases.  
- Subtract total number of complete cases from number of rows, *nrow* to determine total number of rows missing values
- Remember that using $ operator to retrieve column from dataframe creates a vector
- *hist()* creates histogram for vector of interest, change strings to match to instructions
- *density()* for vector of interest, and *plot()* will plot the result
*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Step One: Identify the data using code book
help(____)

# Step Two: Do values align to documentation?  Look at the structure of the dataframe.
____(mtcars)

# Step Two: Do values align to documentation?  Confirm dimension of # rows and # columns using dim()
____(____)


# Step Three: What condition is the data in?  Get initial summary using summary() 
____(____)


# Step Three: What condition is the data in?  Determine total number of complete cases using complete.cases() in combination with sum()
____(____(____))


# Step Three: Determine total number of rows missing data values by subtracting nrow() from previous complete.cases evaluation
____(____(mtcars)) - ____(mtcars)

# Step Four: Data Preparation, recoding factors and handling missing data, we will skip for this exercise

# Step Five: Assess summary information, initial descriptive statistics
# We already ran *summary()*; if we had changed anything in Step Four we would re-run here

# Step Six: Create a histogram for mpg using titles specified in directions
____(mtcars$____, main="____", xlab="____")

# Step Six: Create a plot of density curve for mpg using titles specified in directions
____(____(mtcars$____), main="____", xlab="____")

```

*** =solution
```{r}
# Step One: Identify the data using code book
help(mtcars)

# Step Two: Do values align to documentation?  Look at the structure of the dataframe.
str(mtcars)

# Step Two: Do values align to documentation?  Confirm dimension of # rows and # columns using dim()
dim(mtcars)

# Step Three: What condition is the data in?  Get initial summary using summary() 
summary(mtcars)

# Step Three: What condition is the data in?  Determine total number of complete cases using complete.cases() in combination with sum()
sum(complete.cases(mtcars))

# Step Three: Determine total number of rows missing data values by subtracting nrow() from previous complete.cases evaluation
sum(complete.cases(mtcars)) - nrow(mtcars)

# Step Four: Data Preparation, recoding factors and handling missing data, we will skip for this exercise

# Step Five: Assess summary information, initial descriptive statistics
# We already ran *summary()*; if we had changed anything in Step Four we would re-run here

# Step Six: Create a histogram for mpg using titles specified in directions
hist(mtcars$mpg, main="Histogram of mtcars mpg", xlab="mpg")

# Step Six: Create a plot of density curve for mpg using titles specified in directions
plot(density(mtcars$mpg), main="Density plot of mtcars mpg", xlab="mpg")

```

*** =sct
```{r}

test_student_typed("help\(mtcars\)", not_typed_msg="Did you request help for mtcars dataset?")


test_student_typed("str\(mtcars\)", not_typed_msg="Did you evaluate structure of mtcars dataset?")


test_student_typed("sum\(complete.cases\(mtcars\)\)", not_typed_msg="Did you calculate number of complete cases?")


test_student_typed("sum\(complete.cases\(mtcars\)\) - nrow\(mtcars\)", not_typed_msg="Did you calculate number of missing rows?")


test_student_typed('hist\(mtcars\$mpg, main\="Histogram of mtcars mpg", xlab\="mpg"\)', not_typed_msg="Check your histogram results for the correct vector and titles")


test_student_typed('plot\(density\(mtcars\$mpg\), main="Density plot of mtcars mpg", xlab="mpg"\)', not_typed_msg="Check your density plot results for the correct vector and titles.  Be sure you fit the density plot before you plot the result.  R works from inside out in terms of order of operation.")

success_msg("Excellent.  That is the outline of EDA Goal One.  While we may deviate especially in Step Three, Four, and Six depending on quality and type of data, this is the basic structure that you will continually repeat.")

```
