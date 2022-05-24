# `Week 4` [Getting and Cleaning Data]

#### Tags

-   Specialization: Data Science: Foundations using R Specialization
-   Course: Getting and Cleaning Data
    -   Instructor: Jeff Leek
    -   URL: <https://www.coursera.org/learn/data-cleaning>
    -   From: 23/05/2022
    -   To: 24/05/2022

------------------------------------------------------------------------

#### Deliverables

-   :computer: Swirl: Dates and Times with Lubridate
-   [:pencil: Quiz](./getting_and_cleaning_data_quiz_4.md)
-   [:rocket: Course Project](https://github.com/AndersonUyekita/getting_and_cleaning_data_course_project)

------------------------------------------------------------------------

This week the videos have covered:

* Editing Text Variables
* Regular Expressions I
* Regular Expressions II
* Working with Dates
* Data Resources


## Notations

| Function                                                                     | Description                                                        |
|:-------------------------------------|:---------------------------------|
| `base::tolower(x = "HELLO world")`                                           | Converts any capitalized string into minimized.                    |
| `base::strsplit(x = "Hello.World", split = "\\.")`                           | Split a string based on a pattern.                                 |
| `base::sub(x = "Hello-World", pattern = "-", replacement = " ")`             | Substitute a pattern by a replacement. It will only work one time. |
| `base::gsub(x = "H-e-l-l-o World", pattern = "-", replacement = "")`         | Everytime the gsub finds the pattern, it will be replaced.         |
| `base::grep(x = c("apple", "banana", "melon", "apple"), pattern = "apple")`  | Returns the position                                               |
| `base::grepl(x = c("apple", "banana", "melon", "apple"), pattern = "apple")` | Returns a vector this TRUE and FALSE                               |
