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

