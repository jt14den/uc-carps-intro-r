# challenges 

### Challenge 1: Creating a self-contained project

We're going to create a new project in RStudio:

1.  Click the "File" menu button, then "New Project".
2.  Click "New Directory".
3.  Click "New Project".
4.  Type in the name of the directory to store your project, e.g.
    "my_project".
5.  If available, select the checkbox for "Create a git repository."
6.  Click the "Create Project" button.

-   simplest way to open rstudio and a project is thru your file system
    by double clicking on the `.Rproj` file in your poject folder.

### Challenge 2: Opening an RStudio project through the file system

1.  Exit RStudio.
2.  Navigate to the directory where you created a project in
    Challenge 1.
3.  Double click on the .Rproj file in that directory.

### Challenge 3 
Which of the following are valid R variable names? (Add a plus after the correct answer(s))

min_height
max.height
_age
.mass
MaxLength
min-length
2widths
celsius2kelvin


### Challenge 4

What will be the value of each variable after each statement in the
following program?

mass <- 47.5
age <- 122
mass <- mass * 2.3
age <- age - 20

### Challenge 5

Run the code from the previous challenge, and write a command to compare
`mass` to `age`. Is `mass` larger than `age`?

### Challenge 6

Install the following packages: `ggplot2`, `plyr`, `gapminder`

### Challenge 7

Start by making a vector with the numbers 1 through 26. Multiply the vector by 2, and give the resulting vector names A through Z (hint: there is a built in vector called LETTERS)

## Data Frames 
## Challenge 8
It’s good practice to also check the last few lines of your data and some in the middle. How would you do this?

Searching for ones specifically in the middle isn’t too hard, but we could ask for a few lines at random. How would you code this? HINT: look for help on the function sample: `?sample`

### Solutions: 
To check the last few lines it’s relatively simple as R already has a function for this:

```
tail(gapminder)
tail(gapminder, n = 15)
```

What about a few arbitrary rows just in case something is odd in the middle?

```
gapminder[sample(nrow(gapminder), 5), ]
```

## Challenge 9
Read the output of str(gapminder) again; this time, use what you’ve learned about factors and vectors, as well as the output of functions like colnames and dim to explain what everything that str prints out for gapminder means. If there are any parts you can’t interpret, discuss with your neighbors!

## Challenge 10

 Fix each of the following common data frame subsetting errors:

 1. Extract observations collected for the year 1957

    ```{r, eval=FALSE}
    gapminder[gapminder$year = 1957,]
    ```

 2. Extract all columns except 1 through to 4

    ```{r, eval=FALSE}
    gapminder[,-1:4]
    ```

 3. Extract the rows where the life expectancy is longer the 80 years

    ```{r, eval=FALSE}
    gapminder[gapminder$lifeExp  80]
    ```

 4. Extract the first row, and the fourth and fifth columns
   (`continent` and `lifeExp`).

    ```{r, eval=FALSE}
    gapminder[1, 4, 5]
    ```

 5. Advanced: extract rows that contain information for the years 2002
    and 2007

    ```{r, eval=FALSE}
    gapminder[gapminder$year == 2002 | 2007,]
    ```

  ## Solution to challenge 10
 
  Fix each of the following common data frame subsetting errors:
 
  1. Extract observations collected for the year 1957
 
     ```{r, eval=FALSE}
     # gapminder[gapminder$year = 1957,]
     gapminder[gapminder$year == 1957,]
     ```
 
  2. Extract all columns except 1 through to 4
 
     ```{r, eval=FALSE}
     # gapminder[,-1:4]
     gapminder[,-c(1:4)]
     ```
 
  3. Extract the rows where the life expectancy is longer than 80 years
 
     ```{r, eval=FALSE}
     # gapminder[gapminder$lifeExp  80]
     gapminder[gapminder$lifeExp  80,]
     ```
 
  4. Extract the first row, and the fourth and fifth columns
    (`continent` and `lifeExp`).
 
     ```{r, eval=FALSE}
     # gapminder[1, 4, 5]
     gapminder[1, c(4, 5)]
     ```
 
  5. Advanced: extract rows that contain information for the years 2002
     and 2007
 
      ```{r, eval=FALSE}
      # gapminder[gapminder$year == 2002 | 2007,]
      gapminder[gapminder$year == 2002 | gapminder$year == 2007,]
      gapminder[gapminder$year %in% c(2002, 2007),]
      ```

 ## Challenge 11

 1. Why does `gapminder[1:20]` return an error? How does it differ from `gapminder[1:20, ]`?


 2. Create a new `data.frame` called `gapminder_small` that only contains rows 1 through 9
 and 19 through 23. You can do this in one or two steps.

  ## Solution to challenge 11
 
  1.  `gapminder` is a data.frame so needs to be subsetted on two dimensions. `gapminder[1:20, ]` subsets the data to give the first 20 rows and all columns.
 
  2. 
 
  ```{r}
  gapminder_small <- gapminder[c(1:9, 19:23),]
  ```
