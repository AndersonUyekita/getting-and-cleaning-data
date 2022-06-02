# `Week 4` [Getting and Cleaning Data]

* Author: Anderson H Uyekita
* Specialization: [Data Science: Foundations using R Specialization](https://www.coursera.org/specializations/data-science-foundations-r)
* Course: [Getting and Cleaning Data](https://www.coursera.org/learn/data-cleaning)
    * Instructor: Jeffrey Leek
* Week 4
    * Start: 2022/05/23
    * Finish: 2022/05/24

------------------------------------------------------------------------

#### Assignments & Deliverables

-   :computer: Swirl: Dates and Times with Lubridate
-   [:pencil: Quiz](./getting-and-cleaning-data_quiz-4.md)
-   [:rocket: Course Project Repository](https://github.com/AndersonUyekita/getting-and-cleaning-data_course-project)

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
