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

Complete all instructions in the console pane

*** =instructions

In the editor on the right, complete the code according to the following instructions:

- Pull up code book for *mtcars* using *help()* function
- Evaluate the structure of *mtcars* to confirm it aligns with help documentation
- Use the *dim()* function to confirm the dimensions, # rows by # columns
- Use the *summary()* function to get an initial set of descriptive statistics
- Confirm there are no missing rows using *sum* and *complete.cases* in combination with *nrow*
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
____(mtcars) - ____(____(mtcars))

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
nrow(mtcars) - sum(complete.cases(mtcars))

# Step Four: Data Preparation, recoding factors and handling missing data, we will skip for this exercise

# Step Five: Assess summary information, initial descriptive statistics
# We already ran *summary()*; if we had changed anything in Step Four we would re-run here

# Step Six: Create a histogram for mpg using titles specified in directions
hist(mtcars$mpg, main="Histogram of mtcars mpg", xlab="mpg")

# Step Six: Create a plot of density curve for mpg using titles specified in directions
plot(density(mtcars$mpg), main="Density curve of mtcars mpg", xlab="mpg")

```

*** =sct
```{r}

test_student_typed("help(mtcars)", fixed=TRUE, not_typed_msg="Did you request help for mtcars dataset?")


test_student_typed("str(mtcars)", fixed=TRUE, not_typed_msg="Did you evaluate structure of mtcars dataset?")


test_student_typed("sum(complete.cases(mtcars))", fixed=TRUE, not_typed_msg="Did you calculate number of complete cases?")


test_student_typed("nrow(mtcars)\b-\bsum(complete.cases(mtcars))", fixed=FALSE, not_typed_msg="Did you calculate number of missing rows?")


test_student_typed('hist(mtcars$mpg,\bmain="Histogram of mtcars mpg",\bxlab="mpg")', fixed=FALSE, not_typed_msg="Check your histogram results for the correct vector and titles")


test_student_typed('plot(density(mtcars$mpg),\bmain="Density curve of mtcars mpg",\bxlab="mpg")', fixed=FALSE, not_typed_msg="Check your density plot results for the correct vector and titles.  Be sure you fit the density plot before you plot the result.  R works from inside out in terms of order of operation.")


success_msg("Excellent.  That is the outline of EDA Goal One.  While we may deviate especially in Step Three, Four, and Six depending on quality and type of data, this is the basic structure that you will continually repeat.")

```


--- type:NormalExercise xp:100 skills:1 key:42e6c4c8a9
## EDA Goal Two and Three (Numeric Data)

Let's practice EDA Goal Two (Describe the Data) and Three (Assess and Transform the Data) for our base dataset *mtcars*

Complete all instructions in the console pane

*** =instructions

In the editor on the right, complete the code according to the following instructions:

- Use the *summary()* function to get an initial set of descriptive statistics for the *mpg* variable
- Generate the quartile values for the *mpg* variable using *quantile()* function with *seq(0,1.0,0.25)*
- Generate the quintile values for the *mpg* variable using *quantile()* function and your own modified *seq()*.  Quintiles are 20%, 40%, etc.
- Use *min* and *max* to calculate the range of values for *mpg*
- Calculate the standard deviation for *mpg*
- Use combination of *diff(), range(), scale()* to calculate the range of z-score values
- Plot the density curve for *mpg* with main="Density curve of mpg", and xlab of "mpg".  Use color "blue" for the actual curve.
- Now convert *am* to a factor variable in order to use this to slice our quantitative data by a categorical variable, set levels as "manual" and "automatic".
- Modify the function *center_stats* to include mean, median, and trimmed mean for 25% trim
- Generate *center_stats* aggregated by the new factor variable using *aggregate()* function.  Use formula notation y~x.
- Modify the function *spread_stats* to include sd, iqr, and range of z scores using *aggregate()* function and formula notation y~x.
- Visualize our distribution now in terms of grouping.  Boxplot is good for this type of visual. Label as "Boxplot of mpg by Transmission", label the x axis "Transmission", the y axis "mpg", and use colors "red" and "blue" for the boxes. 


*** =hint
- This time you will use *summary()* against a specific column, vector, not the full dataframe.
- *quantile(vector, seq(...))* should generate what you need.  Use the sequence from quartile and modify appropriately to generate quintiles.
- Remember that functions are evaluated from inside out, so *diff(range(scale()))* should give you what you need
- Look back at previous exercise if you need in order to generate this density curve.  Set color with *col=*
- Convert a vector to a factor with *factor(vector)*.  You can assign the value back to the original *am* variable.
- Look back at class notes to see what is needed to complete *center_stats* and *spread_stats* along with formula notation
- Look at deck 2 from class this week for format for boxplot.  You do not need to generate a legend.

*** =pre_exercise_code
```{r}
# no pec
```

*** =sample_code
```{r}
# Goal Two: Describe the data for vector of interest.  Start with *summary()* function to get initial measures of central tendency
____(mtcars____)

# Goal Two: Describe the data for vector of interest.  Use *quantile()* function to obtain quartiles
quantile(____$____, seq = c(0, 1.0, 0.25))

# Goal Two: Describe the data for vector of interest.  Use *quantile()* function with modified sequence to obtain quintiles
quintile(____$____, seq = c(0, 1.0, ____))

## Goal Three: Assess and transform the measures of central tendency.  At this point, you should have some idea of skewing that we may see when we plot data

## Goal Two: Describe the data for vector of interest.  Use *min()* and *max()* to calculate the range values for *mpg* so we can begin to evaluate spread
____(mtcars$____)
____(____$____)

## Goal Two: Describe the data for vector of interest.  Use *sd()* to calculate standard deviation.
____(____$____)

## Goal Two: Describe the data for vector of interest.  Use combination of *diff(), range(), scale()* to calculate the range of z-score values
____(____(____(mtcars$____)))

# Goal Three: Assess and transform the Measures of spread.  At this point, you should have some idea of shape that we may see when we plot data.entry

# Goal Three: Assess and transform our vector of interest.  Generate a density plot with labeling that follows instructions on left.
____(____(mtcars$____), main="____", xlab="____", col="____")

## Goal Three: Assess and transform.  Re-assess distribution of quantitative variable by evaluating within groups of categorical variable.  Create a categorical variable from the existing *am* vector and replace the vector
mtcars$am <- ____(mtcars$____, levels=c("manual","____"))

## Goal Three: Assess and transform.  Regenerate measures of central tendency by categorical variable *am*.  First, create function for measures of central tendency including mean, median, and trimmed mean with trim of .25.
center_stats <- function(x) (c(mean=____(x), median=____(x), trim=mean(x,trim=____)))

## Goal Three: Now generate the statistics using *aggregate*, the *by* argument, and formula notation.  The function to call is the center_stats function you just created.
aggregate(____~____, data=mtcars, FUN=____)

## Goal Three: Assess and transform.  Create function for measures of spread including sd, iqr, and range of z-scores.  Use *diff(), range(), scale()* to calculate zrange.
spread_stats <- function(x) (c(sd=____(x), iqr=____(x), zrange=____(____(____(x)))))

## Goal Three: Now generate the statistics for spread_stats, grouped by categorical variable and using formula notation.
aggregate(____~____, data=mtcars, FUN=____)

## Goal Three: Assess and transform our vector of interest.  Generate a boxplot with labeling and color that follow instructions on left.
boxplot(____~____, data=____, main="____", xlab="____", ylab="____", col=c(____,____))


```

*** =solution
```{r}
# Goal Two: Describe the data for vector of interest.  Start with *summary()* function to get initial measures of central tendency
summary(mtcars$mpg)

# Goal Two: Describe the data for vector of interest.  Use *quantile()* function to obtain quartiles
quantile(mtcars$mpg, seq = c(0, 1.0, 0.25))

# Goal Two: Describe the data for vector of interest.  Use *quantile()* function with modified sequence to obtain quintiles
quintile(mtcars$mpg, seq = c(0, 1.0, 0.20))

## Goal Three: Assess and transform the measures of central tendency.  At this point, you should have some idea of skewing that we may see when we plot data

## Goal Two: Describe the data for vector of interest.  Use *min()* and *max()* to calculate the range values for *mpg* so we can begin to evaluate spread
min(mtcars$mpg)
max(mtcars$mpg)

## Goal Two: Describe the data for vector of interest.  Use *sd()* to calculate standard deviation.
sd(mtcars$mpg)

## Goal Two: Describe the data for vector of interest.  Use combination of *diff(), range(), scale()* to calculate the range of z-score values
diff(range(scale(mtcars$mpg)))

# Goal Three: Assess and transform the Measures of spread.  At this point, you should have some idea of shape that we may see when we plot data.entry

# Goal Three: Assess and transform our vector of interest.  Generate a density plot with labeling that follows instructions on left.
plot(density(mtcars$mpg), main="Density curve of mpg", xlab="mpg", col="blue")

## Goal Three: Assess and transform.  Re-assess distribution of quantitative variable by evaluating within groups of categorical variable.  Create a categorical variable from the existing *am* vector and replace the vector
mtcars$am <- factor(mtcars$mpg, levels=c("manual","automatic"))

## Goal Three: Assess and transform.  Regenerate measures of central tendency by categorical variable *am*.  First, create function for measures of central tendency including mean, median, and trimmed mean with trim of .25.
center_stats <- function(x) (c(mean=mean(x), median=median(x), trim=mean(x,trim=0.25)))

## Goal Three: Now generate the statistics using *aggregate*, the *by* argument, and formula notation.  The function to call is the center_stats function you just created.
aggregate(mpg~am, data=mtcars, FUN=center_stats)

## Goal Three: Assess and transform.  Create function for measures of spread including sd, iqr, and range of z-scores.  Use *diff(), range(), scale()* to calculate zrange.
spread_stats <- function(x) (c(sd=sd(x), iqr=IQR(x), zrange=diff(range(scale(x)))))

## Goal Three: Now generate the statistics for spread_stats, grouped by categorical variable and using formula notation.
aggregate(mpg~am, data=mtcars, FUN=spread_stats)

## Goal Three: Assess and transform our vector of interest.  Generate a boxplot with labeling and color that follow instructions on left.
boxplot(mpg~am, data=mtcars, main="Boxplot of mpg by Transmission", xlab="Transmission", ylab="mpg", col=c("red","blue"))

```

*** =sct
```{r}


success_msg("Excellent.  That is the outline of EDA Goal One.  While we may deviate especially in Step Three, Four, and Six depending on quality and type of data, this is the basic structure that you will continually repeat.")

```
