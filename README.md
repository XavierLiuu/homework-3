# homework 3 - Functions I

## Instructions

1. Use the `flights` dataset in the [`nycflights13`](https://cran.r-project.org/web/packages/nycflights13/index.html) package.

2. Your final document should be an `.md` file (GitHub-flavored markdown) knitted from an R Markdown file. Create a folder called `/homework` where you will add the `.md` file, and a folder called `/src` where you will  place the `.Rmd` file and any other scripts you used to create the reports.

  In answering each of the questions for the assignment please include
  - the question as a header in your R Markdown report,
  - the raw code that you used to generate any tables, and
  - the top ten rows/values/or elements of any resulting tibble, dataframe, vector, or list created in your results.

3. when you are done with your final `push` to this repo, submit the link to this repo on Canvas. (Make sure to `commit` your progress throughout the day, and `push` your progress at the end of each day.)


### Assignment items `[100 pts]`

1. `[20 pts]` __Write a function that takes a single numerical vector and returns three values, the minimum number, the median, and the maximum number of the vector.  Test your function using the month column of the flights dataset.__

2. `[10 pts]` __Explain your reasoning for choosing your function’s name in the previous question.__

3. `[30 pts]` __Write a function that categorizes a numerical variable in the flights data into four categories.__

  The function should have two arguments.  The first should represent the tibble object and the second should represent a column name in the data object.  

  The function should first limit the data to include the column name only.  Then it should categorize the column into four categories in the following manner.

  For any particular variable in the flights data that represents military time (i.e.-0 to 2400 where 1200 represents 12 in the afternoon and 2400 represents midnight), the function should classify values into four categories:
  - "Morning" for values from 5 am to 11:59 am
  - "Afternoon" for values from 12 pm to 4:59 pm
  - "Evening" for values from 5 pm to 8:59 pm
  - "Night"  for values from 9 pm to 4:59 am

  Test your function using the `dep_time` column of the flights dataset.

  _Hint: Use `mutate()` with `case_when()` to create categories.  Or alternatively you could also use_

  `data$columnname[which(data$columnname<=some_value_here)]<-"Morning"`


4. `[10 pts]` __Explain your reasoning for choosing your function’s name in the previous question.__

5. `[20 pts]` __Write a function that calculates the median of all numeric variables in the flights dataset using a `for` loop.__

  _Hint: There are several ways to subset to numeric values only.  Given that we haven't walked through the automated ways to do this yet I'll give you the first step in this answer:_

  `flights_numeric_vars<-select_if(flights, is.numeric)`

6. `[10 pts]` __Explain your reasoning for choosing your function’s name in the previous question.__ 
