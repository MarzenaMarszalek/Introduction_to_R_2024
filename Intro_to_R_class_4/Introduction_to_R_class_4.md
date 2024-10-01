Introduction to R - class 4<br> <span style="color: gray">Data Wrangling
2</span>
================
Tomasz Gaczorek, Wiesław Babik & Mateusz Chechetkin<br>Marzena
Marszałek<br> <marzena.marszalek@doctoral.uj.edu.pl><br>
2024-10-01

- [Logical expressions](#logical-expressions)
  - [<span style="color: green">**Exercise 1**</span>](#exercise-1)
  - [<span style="color: green">**Exercise 2**</span>](#exercise-2)
  - [<span style="color: green">**Exercise 3**</span>](#exercise-3)
- [Comparisons](#comparisons)
  - [<span style="color: green">**Exercise 4**</span>](#exercise-4)
  - [<span style="color: green">**Exercise 5**</span>](#exercise-5)
  - [<span style="color: green">**Exercise 6**</span>](#exercise-6)
  - [<span style="color: green">**Exercise 7**</span>](#exercise-7)
- [Exclamation mark](#exclamation-mark)
  - [<span style="color: green">**Exercise 8**</span>](#exercise-8)
  - [<span style="color: green">**Exercise 9**</span>](#exercise-9)
- [Logical operators](#logical-operators)
  - [<span style="color: green">**Exercise 10**</span>](#exercise-10)
  - [<span style="color: green">**Exercise 11**</span>](#exercise-11)
- [which() function](#which-function)
  - [<span style="color: green">**Exercise 12**</span>](#exercise-12)
  - [<span style="color: green">**Exercise 13**</span>](#exercise-13)
- [Subsetting with the logical
  expressions](#subsetting-with-the-logical-expressions)
  - [<span style="color: green">**Exercise 14**</span>](#exercise-14)
  - [<span style="color: green">**Exercise 15**</span>](#exercise-15)
  - [<span style="color: green">**Exercise 16**</span>](#exercise-16)
- [dplyr](#dplyr)
  - [<span style="color: green">**Exercise 17**</span>](#exercise-17)
  - [<span style="color: green">**Exercise 18**</span>](#exercise-18)
  - [<span style="color: green">**Exercise 19**</span>](#exercise-19)
  - [SORTING OBSERVATIONS](#sorting-observations)
    - [<span style="color: green">**Exercise 20**</span>](#exercise-20)
    - [<span style="color: green">**Exercise 21**</span>](#exercise-21)
    - [<span style="color: green">**Exercise 22**</span>](#exercise-22)
  - [SUBSETTING COLUMNS](#subsetting-columns)
    - [<span style="color: green">**Exercise 23**</span>](#exercise-23)
    - [<span style="color: green">**Exercise 24**</span>](#exercise-24)
  - [SUBSETTING OBSERVATIONS](#subsetting-observations)
    - [<span style="color: green">**Exercise 25**</span>](#exercise-25)
    - [<span style="color: green">**Exercise 26**</span>](#exercise-26)
  - [MODIFYING COLUMNS](#modifying-columns)
    - [<span style="color: green">**Exercise 27**</span>](#exercise-27)
  - [SUMMARY](#summary)
    - [<span style="color: green">**Exercise 28**</span>](#exercise-28)
  - [PIPELINE OPERATOR AND PIPELINE](#pipeline-operator-and-pipeline)
    - [<span style="color: green">**Exercise 30**</span>](#exercise-30)
  - [GROUPING](#grouping)
    - [<span style="color: green">**Exercise 31**</span>](#exercise-31)
    - [<span style="color: green">**Exercise 32**</span>](#exercise-32)
  - [JOINING](#joining)
    - [<span style="color: green">**Exercise 33**</span>](#exercise-33)
- [<span style="color: darkorange;">Homework</span>](#homework)

## Logical expressions

R as a whole computer architecture (including programming languages) is
based on the **binary information**, the current either flows (`TRUE`)
or not (`FALSE`), (capital letters on purpose) depending on the
conditions. These logical values form a distinct type of data and can
be, similarly to other types, combined into vectors using the same
functions as for numbers and characters.

### <span style="color: green">**Exercise 1**</span>

<span style="color: green">**Create a logical vector with 3 `TRUE` and 2
`FALSE` values and call it `my_logical`. Note that they are internal R
symbols so you should not use quotation marks (`""`).**</span>

Expected result:

    ## [1]  TRUE  TRUE  TRUE FALSE FALSE

*An advice: To make your code shorter you can use `T` instead of `TRUE`
and `F` instead of `FALSE`.*

Formally, logical values correspond to 0 (for `FALSE`) and 1 (for
`TRUE`) and behave like them in every mathematical operations.

### <span style="color: green">**Exercise 2**</span>

<span style="color: green">**Calculate the sum of `my_logical`.**</span>

Expected result:

    ## [1] 3

> **Curiosity**  
> A sum of logical vectors can be used to check a data frame for the
> presence of `NA` cells. To do this, combine the `is.na()` function
> used on the data frame with the `sum()` function.

However, logical vectors have one important distinctive characteristic:
they can be used for **subsetting**. To achieve this you need to provide
logical vector with `TRUE` **for the elements you want to keep** and
`FALSE` **for for the elements you want to discard**. The length of the
logical vector used for subsetting has to be equal to the number of
elements (e.g., columns) in the object we want to subset.

### <span style="color: green">**Exercise 3**</span>

<span style="color: green">**Save 6 first rows of built-in `CO2` dataset
to a chosen variable. Then, using logical vectors return its 1st and 5th
column.**</span>

Expected result:

    ##   Plant uptake
    ## 1   Qn1   16.0
    ## 2   Qn1   30.4
    ## 3   Qn1   34.8
    ## 4   Qn1   37.2
    ## 5   Qn1   35.3
    ## 6   Qn1   39.2

## Comparisons

Normally, no one creates logical vectors on their own. There are created
automatically as the effect of different comparisons. The most common is
testing for equality. It is done with double equal sign (`==`).

### <span style="color: green">**Exercise 4**</span>

<span style="color: green">**Check whether in R: 5 equals 5.00 and
whether `π` equals 3.14.**</span>

Expected result:

    ## [1] TRUE

    ## [1] FALSE

The same stands for all others comparisons but the symbols are
different:

• `==` - equal  
• `!=` - not equal  
• `>` - greater than  
• `>=` - greater than or equal  
• `<` - less than  
• `<=` - less than or equal

> **Curiosity**  
> Double equal sign (`==`) is used for equality because single sign
> (`=`) is already in use. It serves as an alternative for the assigning
> arrow, however, for code purity the arrow is the one recommended.

Note that while comparing two vectors with the symbols shown above, R
does not consider the action as one comparison. It rather compares them
element by element, recycling shorter vector and resulting in logical
vector of longer one’s length. It is the same rule as for mathematical
operations on vectors.

### <span style="color: green">**Exercise 5**</span>

<span style="color: green">**Manually create two vectors. One of the
prime numbers and a second of even numbers. Both should belong to the
range \<0,11\>. Check if they are equal.**</span>

Expected result:

    ## [1]  TRUE FALSE FALSE FALSE FALSE

To check whether vectors (as a whole) are identical use `identical()`
function.

### <span style="color: green">**Exercise 6**</span>

<span style="color: green">**Create two integer vectors from 1 to 10.
Call them differently and compare them with `identical()` function.
Then, change one value within first vector and repeat
comparison.**</span>

Expected result:

    ## [1] TRUE

    ## [1] FALSE

The other useful tool is the `%in%` operator. It provides information
**whether elements of first vector are present in the second one**. Note
that it is focused on the first vector only, so there is **no
recycling**.

### <span style="color: green">**Exercise 7**</span>

<span style="color: green">**Create two character vectors each
consisting of a set of individual characters. The first should contain
your name and the second one the name of other person from the group.
Check how many letter your names have in common. Then, change the order
of names and repeat the comparison.**</span>

## Exclamation mark

Exclamation mark (`!`) works in R as the symbol of negation (=reversing
the statement). Any logical vector preceded by `!` will result in its
reversal - `FALSE` changed into `TRUE` and vice versa.

### <span style="color: green">**Exercise 8**</span>

<span style="color: green">**Having vector of 3 `TRUE` values, return
its negation.**</span>

Expected result:

    ## [1] FALSE FALSE FALSE

More typically `!` is used to negate comparisons. Note that the idea is
the same: you negate logical vector by negating action which produces
it. Remember that negated comparison should be enclosed in parentheses
e.g. `!(2 == 2)`.

### <span style="color: green">**Exercise 9**</span>

<span style="color: green">**Create a sequence of integers from 1 to 100
in which each subsequent element is larger by 3 than the previous one.
Then, create logical vector indicating which elements are larger than
50. Do not use `>` sign.**</span>

Expected result:

    ##  [1] FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE FALSE
    ## [13] FALSE FALSE FALSE FALSE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE
    ## [25]  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE  TRUE

## Logical operators

The real power of logic in programming is provided by combining
comparisons (use parentheses for clarity). There are two basic
operators:

• `&` - **and** - condition is `TRUE` if both comparison are `TRUE`  
• `|` - **or** - condition is `TRUE` if at least one comparison is
`TRUE`

### <span style="color: green">**Exercise 10**</span>

<span style="color: green">**For an integer vector from 1 to 10, create
logical vector indicating which element is smaller or larger than
5.**</span>

Expected result:

    ##  [1]  TRUE  TRUE  TRUE  TRUE FALSE  TRUE  TRUE  TRUE  TRUE  TRUE

### <span style="color: green">**Exercise 11**</span>

<span style="color: green">**For an integer vector from 1 to 10, create
logical vector indicating which element is divisible by both 2 and
3.**</span>

Expected result:

    ##  [1] FALSE FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE

> **Curiosity**  
> R also uses double version of `&` and `|` operators. Their outcome is
> exactly the same and their role is just related to optimization. While
> using double operators, R checks first condition and if not needed,
> ignore the second one (e.g. in the ‘AND’ statement if the first
> condition is `FALSE`, there is no need to check the second one as the
> result will always be `FALSE`). Note that they are often used when
> conditions are severly time-consuming.

## which() function

Frequently, the question is not about logical vectors themselves but
rather about **which element of a vector fulfills given condition**. The
answer is provided by `which()` function. It takes comparison as an
argument and **return a vector of indexes** that can be used for
subsetting.

### <span style="color: green">**Exercise 12**</span>

<span style="color: green">**Construct a vector with first 20 integers
divisible by 3. Which elements of it are larger or equal 21?**</span>

Expected result:

### <span style="color: green">**Exercise 13**</span>

<span style="color: green">**Having indexes of values larger or equal 21
from the previous exercise, return the values from the vector.**</span>

Expected result:

    ##  [1] 21 24 27 30 33 36 39 42 45 48 51 54 57 60

## Subsetting with the logical expressions

As stated before subsetting can be done directly with logical vectors
(`TRUE` for each kept element). In practice, it is even simpler. All you
need to provide is a **condition instead of a coordinate**
e.g. `vector[condition]` will return only the elements fulfilling given
condition.

For example: There is a vector `a <- c(1,2,3,4)`. We want to subset
elements of this vector that are greater then 2.  
The formula will look like this: `a[a>2]`.  
Then the result will be: `[1] 3 4`.

The logic behind is as follows:

- condition (here: `[a>2]`) generates a logical vector - **positions are
  denoted as a series of `TRUE` and `FALSE`**. In this example the
  logical vector is: `[1] FALSE FALSE  TRUE  TRUE`.  
- elements in this logical vector are used to **return the elements of
  the vector you want to subset**, for which coordinate equals `TRUE`,
  so here 2 last elements of the vector will be returned: `[1] 3 4`

Note that you cannot see the `TRUE`/`FALSE` vector itself but it is if
fact generated and used during subsetting operation.

### <span style="color: green">**Exercise 14**</span>

<span style="color: green">**For an integer vector from 1 to 100, return
elements higher than vector’s mean.**</span>

Expected result:

    ##  [1]  51  52  53  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69
    ## [20]  70  71  72  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  88
    ## [39]  89  90  91  92  93  94  95  96  97  98  99 100

The same pattern applies for subsetting data frames.

### <span style="color: green">**Exercise 15**</span>

<span style="color: green">**Using built-in dataset `CO2`, return
observation for `Qn2` plant.**</span>

Epected result:

    ##    Plant   Type  Treatment conc uptake
    ## 8    Qn2 Quebec nonchilled   95   13.6
    ## 9    Qn2 Quebec nonchilled  175   27.3
    ## 10   Qn2 Quebec nonchilled  250   37.1
    ## 11   Qn2 Quebec nonchilled  350   41.8
    ## 12   Qn2 Quebec nonchilled  500   40.6
    ## 13   Qn2 Quebec nonchilled  675   41.4
    ## 14   Qn2 Quebec nonchilled 1000   44.3

*An advice: To obtain the logical vector with one element for each row,
you need to make comparison based on a column
e.g.`my_data[my_data$my_column != 5,]` would result in the observations
(including all columns) from `my_data` in which the value for
`my_collumn` does not equal 5.*

### <span style="color: green">**Exercise 16**</span>

<span style="color: green">**Using built-in dataset `CO2`, return
observation from `Mississippi` `chilled` plant with an `uptake` higher
than 20 ummol/m2 x s.**</span>

Expected result:

    ##    Plant        Type Treatment conc uptake
    ## 69   Mc1 Mississippi   chilled  675   22.2
    ## 70   Mc1 Mississippi   chilled 1000   21.9

## dplyr

`dplyr` is an extremely popular R package that helps to easily manage
the data frames.

### <span style="color: green">**Exercise 17**</span>

<span style="color: green">**Install and load the `dplyr`
package.**</span>

### <span style="color: green">**Exercise 18**</span>

<span style="color: green">**Upload the
[rats.csv](https://github.com/MarzenaMarszalek/Introduction_to_R_2024/blob/main/Intro_to_R_class_4/rats.csv)
file into an object called `my_data`.**</span>

Expected result (first 10 rows):

    ##    Glycogen Treatment Rat Liver
    ## 1       131         1   1     1
    ## 2       130         1   1     1
    ## 3       131         1   1     2
    ## 4       125         1   1     2
    ## 5       136         1   1     3
    ## 6       142         1   1     3
    ## 7       150         1   2     1
    ## 8       148         1   2     1
    ## 9       140         1   2     2
    ## 10      143         1   2     2

### <span style="color: green">**Exercise 19**</span>

<span style="color: green">**Modify `my_data` by adding the column with
ID at the beginning.**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Rat Liver
    ## 1   1      131         1   1     1
    ## 2   2      130         1   1     1
    ## 3   3      131         1   1     2
    ## 4   4      125         1   1     2
    ## 5   5      136         1   1     3
    ## 6   6      142         1   1     3
    ## 7   7      150         1   2     1
    ## 8   8      148         1   2     1
    ## 9   9      140         1   2     2
    ## 10 10      143         1   2     2

All subsequent functions come from the loaded `dplyr` package.
Importantly, names of columns provided to `dplyr` functions **do not
need quotation marks**.

### SORTING OBSERVATIONS

To sort the data, use `arrange()` function in the following manner:
`arrange(dataset,ordering_column)`

#### <span style="color: green">**Exercise 20**</span>

<span style="color: green">**Obtain the observations from `my_data`
sorted with increasing levels of glycogen.**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Rat Liver
    ## 1   4      125         1   1     2
    ## 2  26      125         3   1     1
    ## 3  36      127         3   2     3
    ## 4   2      130         1   1     1
    ## 5   1      131         1   1     1
    ## 6   3      131         1   1     2
    ## 7  25      134         3   1     1
    ## 8  35      134         3   2     3
    ## 9  29      135         3   1     3
    ## 10  5      136         1   1     3

To obtain the descending order put the name of column inside `desc()`
function.

#### <span style="color: green">**Exercise 21**</span>

<span style="color: green">**Obtain the observations from `my_data`
sorted with the decreasing levels of glycogen.**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Rat Liver
    ## 1  23      162         2   2     3
    ## 2  11      160         1   2     3
    ## 3  13      157         2   1     1
    ## 4  20      155         2   2     1
    ## 5  15      154         2   1     2
    ## 6  18      153         2   1     3
    ## 7  24      152         2   2     3
    ## 8  19      151         2   2     1
    ## 9   7      150         1   2     1
    ## 10 12      150         1   2     3

You can also sort the data by **multiple columns**. Do it by adding an
additional column in the following manner:
`arrange(dataset,ordering_column1,ordering_column2)`. Note that the
priority of sorting is denoted by the order of function arguments.

#### <span style="color: green">**Exercise 22**</span>

<span style="color: green">**Obtain the observations from `my_data`
sorted firstly by `Treatment` column and then by `Rat` column. Both in
ascending order.**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Rat Liver
    ## 1   1      131         1   1     1
    ## 2   2      130         1   1     1
    ## 3   3      131         1   1     2
    ## 4   4      125         1   1     2
    ## 5   5      136         1   1     3
    ## 6   6      142         1   1     3
    ## 7   7      150         1   2     1
    ## 8   8      148         1   2     1
    ## 9   9      140         1   2     2
    ## 10 10      143         1   2     2

### SUBSETTING COLUMNS

To select particular columns use the `select()` function in the
following way: `select(dataset,column_name1,column_name2)`. Note that
all mentioned columns will be preserved and the rest will be discarded.

#### <span style="color: green">**Exercise 23**</span>

<span style="color: green">**Obtain the `Glycogen` and `Liver` columns
from `my_data.`**</span>

Expected result (first 10 rows):

    ##    Glycogen Liver
    ## 1       131     1
    ## 2       130     1
    ## 3       131     2
    ## 4       125     2
    ## 5       136     3
    ## 6       142     3
    ## 7       150     1
    ## 8       148     1
    ## 9       140     2
    ## 10      143     2

You can also use **minus preceding the column name** which means “**all
except this column**”.

#### <span style="color: green">**Exercise 24**</span>

<span style="color: green">**Obtain the `ID`, `Glycogen`, `Treatment`
and `Liver` columns from `my_data`. Use the minus (`-`) sign.**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Liver
    ## 1   1      131         1     1
    ## 2   2      130         1     1
    ## 3   3      131         1     2
    ## 4   4      125         1     2
    ## 5   5      136         1     3
    ## 6   6      142         1     3
    ## 7   7      150         1     1
    ## 8   8      148         1     1
    ## 9   9      140         1     2
    ## 10 10      143         1     2

### SUBSETTING OBSERVATIONS

To subset the observations, use the `filter()` function in the following
manner: `filter(dataset, your_logical_condition)`. Note that logical
conditions are always related to the values inside a given column.

#### <span style="color: green">**Exercise 25**</span>

<span style="color: green">**Obtain the observations for
`Treatment 1`.**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Rat Liver
    ## 1   1      131         1   1     1
    ## 2   2      130         1   1     1
    ## 3   3      131         1   1     2
    ## 4   4      125         1   1     2
    ## 5   5      136         1   1     3
    ## 6   6      142         1   1     3
    ## 7   7      150         1   2     1
    ## 8   8      148         1   2     1
    ## 9   9      140         1   2     2
    ## 10 10      143         1   2     2

You can also combine several logical conditions by using logical
operators (see above). Note, however, that for each observation under
consideration it needs to result in a single `TRUE` or `FALSE`.

#### <span style="color: green">**Exercise 26**</span>

<span style="color: green">**Obtain the observations for `Treatment` 3
with glycogen level higher than 135.**</span>

Expected result:

    ##   ID Glycogen Treatment Rat Liver
    ## 1 27      138         3   1     2
    ## 2 28      138         3   1     2
    ## 3 30      136         3   1     3
    ## 4 31      138         3   2     1
    ## 5 32      140         3   2     1
    ## 6 33      139         3   2     2
    ## 7 34      138         3   2     2

### MODIFYING COLUMNS

To create a new column based on the others use the `mutate()` function
in the following manner:
`mutate(dataset,new_column_name = recipe_for_values)`. “Recipe for
values” is often a **mathematical formula or simple mathematical
function** based on values of other columns. Note that it is just a
modification of given value for each observation separately.

#### <span style="color: green">**Exercise 27**</span>

<span style="color: green">**Create a new column called `log_Gly` that
will be a natural logarithm transformation of `Glycogen` column.
Overwrite `my_data`**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Rat Liver  log_Gly
    ## 1   1      131         1   1     1 4.875197
    ## 2   2      130         1   1     1 4.867534
    ## 3   3      131         1   1     2 4.875197
    ## 4   4      125         1   1     2 4.828314
    ## 5   5      136         1   1     3 4.912655
    ## 6   6      142         1   1     3 4.955827
    ## 7   7      150         1   2     1 5.010635
    ## 8   8      148         1   2     1 4.997212
    ## 9   9      140         1   2     2 4.941642
    ## 10 10      143         1   2     2 4.962845

### SUMMARY

Make a summary of your dataset with the `summarise()` function. The
syntax is as follows:
`summarise(dataset,name_of_summary1 = recipe_for_value1,name_of_summary2 = recipe_for_value2,…)`.
Recipe in that case is any aggregating function (e.g.`mean())` that will
accept whole column (vector) and result in a single statistics. Note
that this function will result in creation of new table with 1 row of
summary statistics and as many columns as number of statistics
mentioned.

#### <span style="color: green">**Exercise 28**</span>

<span style="color: green">**Create a summary of `my_data` containing
mean, median, maximum value, minimum value and standard deviation of
`Glycogen` column.**</span>

Expected result:

    ##       mean median max min   st_dev
    ## 1 142.2222    141 162 125 9.754445

You can also count the number of observations corresponding to the
groups within a given column e.g. check how many observations were
collected for each treatment. To obtain it use the `count()` function by
typing `count(dataset, = given_column)`. 444444 \####
<span style="color: green">**Exercise 29**</span>
<span style="color: green">**Use `count()` function to calculate how
many treatments were used in a study.**</span>

Expected result:

    ##   Treatment  n
    ## 1         1 12
    ## 2         2 12
    ## 3         3 12

### PIPELINE OPERATOR AND PIPELINE

As you probably noticed all `dplyr` functions have data as the first
argument. Based on this characteristics you can create a pipeline where
the next function **uses the output generated by the previous one**. In
that case you should provide the dataset argument to the first function
only.

Pipeline is created by connecting subsequent functions with `%>%` (pipe)
operator. Remember to skip the data argument in all functions except for
the first one
e.g. `select(dataset,column1,column2) %>% filter(column1 > 50)`.

#### <span style="color: green">**Exercise 30**</span>

<span style="color: green">**Using pipeline and `my_data` data frame: 1.
select `ID`, `Glycogen` and `Liver` column. 2. obtain observations with
glycogen level lower than 140. 3. sort it based on `Glycogen` column in
descending order.**</span>

Expected result (first 10 rows):

    ##    ID Glycogen Liver
    ## 1  33      139     2
    ## 2  27      138     2
    ## 3  28      138     2
    ## 4  31      138     1
    ## 5  34      138     2
    ## 6   5      136     3
    ## 7  30      136     3
    ## 8  29      135     3
    ## 9  25      134     1
    ## 10 35      134     3

### GROUPING

Performing any function over complete dataset is often not what you
really want. Imagine 3 species with a trait of interest. It can be the
case that the overall mean does not reflect the variability among
species. To check value for each species separately you need to **group
your dataset**. Do it by using `group_by()` function in the following
manner group_by(dataset,column_with_groups). This produces a grouped
dataframe and will cause all subsequent functions to **operate on each
group separately**.

#### <span style="color: green">**Exercise 31**</span>

<span style="color: green">**Using pipeline, `group_by()` function and
`my_data` data frame, create a summary table with mean and standard
deviation of `Glycogen` column for each treatment separately.**</span>

Expected result:

    ## # A tibble: 3 × 3
    ##   Treatment  mean st_dev
    ##       <int> <dbl>  <dbl>
    ## 1         1  140.  10.3 
    ## 2         2  151    5.66
    ## 3         3  135.   4.71

*An advice: To perform any action on the whole dataset again, use the
`ungroup()` function.*

#### <span style="color: green">**Exercise 32**</span>

<span style="color: green">**Using pipeline, `group_by()` function and
`my_data` data frame, create a new column with the deviations of
`Glycogen` values from the arithmetic mean in a given
`Treatment`.**</span>

Expected result (first 10 rows):

    ## # A tibble: 10 × 6
    ## # Groups:   Treatment [1]
    ##       ID Glycogen Treatment   Rat Liver log_Gly
    ##    <int>    <int>     <int> <int> <int>   <dbl>
    ##  1     1      131         1     1     1    4.88
    ##  2     2      130         1     1     1    4.87
    ##  3     3      131         1     1     2    4.88
    ##  4     4      125         1     1     2    4.83
    ##  5     5      136         1     1     3    4.91
    ##  6     6      142         1     1     3    4.96
    ##  7     7      150         1     2     1    5.01
    ##  8     8      148         1     2     1    5.00
    ##  9     9      140         1     2     2    4.94
    ## 10    10      143         1     2     2    4.96

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* **ADVANCED**
\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

### JOINING

Imagine having two data frames corresponding to the same study system.
In both of them there is a column with individual IDs. How to bind them
together? Using `cbind()` is rather a bad idea as the order of
observations can differ.

The solution is to use one of the `_join()` functions.

data frame 1:

    ##      ID    V1
    ## 1 ind_1   red
    ## 2 ind_2  blue
    ## 3 ind_3 green

data frame 2:

    ##      ID    V2
    ## 1 ind_2 black
    ## 2 ind_3  blue
    ## 3 ind_4  blue

1.  **`left_join()` - join the values from second table (right) that
    correspond to observation in the first one (left). If there is no
    suitable value in the second table, `NA` is returned.**

``` r
left_join(df1, df2, by = "ID")
```

    ##      ID    V1    V2
    ## 1 ind_1   red  <NA>
    ## 2 ind_2  blue black
    ## 3 ind_3 green  blue

2.  **`right_join()` - join the values from first table (left) that
    correspond to observation in the second one (right). If there is no
    suitable value in the first table, `NA` is returned.**

``` r
right_join(df1, df2, by = "ID")
```

    ##      ID    V1    V2
    ## 1 ind_2  blue black
    ## 2 ind_3 green  blue
    ## 3 ind_4  <NA>  blue

3.  **`inner_join()` - return only that observations that have
    corresponding values in both tables.**

``` r
inner_join(df1, df2, by = "ID")
```

    ##      ID    V1    V2
    ## 1 ind_2  blue black
    ## 2 ind_3 green  blue

4.  **`full_join()` - join what can be joined but **keeps all
    observations**. In case of the lack of suitable value, returns
    `NA`.**

``` r
full_join(df1, df2, by = "ID")
```

    ##      ID    V1    V2
    ## 1 ind_1   red  <NA>
    ## 2 ind_2  blue black
    ## 3 ind_3 green  blue
    ## 4 ind_4  <NA>  blue

Each of the abovementioned functions can be used by typing:
`..._join(first_table,second_table,by = “shared_column_name”)`.

Notice that the name of shared column should be exactly the same in both
tables (eg. `ID`).

#### <span style="color: green">**Exercise 33**</span>

<span style="color: green">\*\*Execute the code below and then join the
observations from `my_data` and `new_data` data frames. Keep all
observations from `my_data` but only those from `new_data` that have
their counterparts in `my_data`.

`new_data <- data.frame("ID" = c(2:100),"weight" = rnorm(99,mean = 150,sd = 20))`

Expected result (first 10 rows):

    ##    ID Glycogen Treatment Rat Liver  log_Gly    weight
    ## 1   1      131         1   1     1 4.875197        NA
    ## 2   2      130         1   1     1 4.867534 150.70727
    ## 3   3      131         1   1     2 4.875197 135.67287
    ## 4   4      125         1   1     2 4.828314 154.07335
    ## 5   5      136         1   1     3 4.912655  97.73738
    ## 6   6      142         1   1     3 4.955827 137.94614
    ## 7   7      150         1   2     1 5.010635 137.57725
    ## 8   8      148         1   2     1 4.997212 180.37743
    ## 9   9      140         1   2     2 4.941642 148.45932
    ## 10 10      143         1   2     2 4.962845 120.79080

> **Curiosity**  
> 1. Using joins let us avoid repeating the same information across many
> data frames.  
> 2. The concept of joins is common in many computer languages but it is
> most often used in databases management (e.g. SQL).

## <span style="color: darkorange;">Homework</span>

<span style="color: darkorange"> 1. Create a vector from 1 to 50. Then,
using R only, calculate how many elements of this vector are higher of
equal than the positive square root of 100. \*Positive square root can
be calculated with the `sqrt()` function.<br> 2. Upload the built-in
`CO2` data set as `hw_data`. Using logical expressions, display the rows
of the data set that have `concentration` below 350 AND `uptake` of over
30.<br> 3. Load the `dplyr` library. In the `hw_data` data frame, sort
the observations first by `concentration`, then by `uptake`. Overwrite
the `hw_data` file so that the columns are permanently sorted in this
manner.<br> 4. Add a new column to the `hw_data` data frame that
displays the `uptake` value as a percent of the maximum value of that
column (=so that the highest value, 45.5, corresponds to 100%). Then
remove the original `uptake` column using a `dplyr` function.<br> 5. Use
the pipe operator to perform multiple functions on the `hw_data` data
frame. Create a summary data frame that displays mean and standard
deviation of the new `uptake` column for `Treatment` groups. Save this
summary as a .csv file.

<span style="color: darkorange">**Upload both your R script and .csv
file to the *Pegaz* platform.**</span>
