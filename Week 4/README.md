# `Week 4` [Getting and Cleaning Data]

* &#x1f468;&#x1F3FB;&#x200d;&#x1f4bb; Author: Anderson H Uyekita
* &#x1f4da; Specialization: [Data Science: Foundations using R Specialization](https://www.coursera.org/specializations/data-science-foundations-r)
* &#x1f4d6; Course: [Getting and Cleaning Data](https://www.coursera.org/learn/data-cleaning)
    * &#x1F9D1;&#x200d;&#x1F3EB; Instructor: Jeffrey Leek
* &#x1F4C6; Week 4
    * &#x1F6A6; 2022/05/23
    * &#x1F3C1; 2022/05/24

***

#### Assignments & Deliverables

* &#x1F4BB; Swirl: Dates and Times with Lubridate
* [&#x1F4DD; Quiz](./getting-and-cleaning-data_quiz-4.md)
* [&#x1F680; Course Project Repository](https://github.com/AndersonUyekita/getting-and-cleaning-data_course-project)

***

Content covered this week:

* [Editing Text Variables](./slides/04_01_editingTextVariables.pdf)
* [Regular Expressions I](./slides/04_02_regularExpressions.pdf)
* [Regular Expressions II](./slides/04_03_regularExpressionsII.pdf)
* [Working with Dates](./slides/04_04_workingWithDates.pdf)
* [Data Resources](./slides/04_05_dataResources.pdf)


## Notations

| Function                                                                     | Description                                                        |
|:-------------------------------------|:---------------------------------|
| `base::tolower(x = "HELLO world")`                                           | Converts any capitalized string into minimized.                    |
| `base::strsplit(x = "Hello.World", split = "\\.")`                           | Split a string based on a pattern.                                 |
| `base::sub(x = "Hello-World", pattern = "-", replacement = " ")`             | Substitute a pattern by a replacement. It will only work one time. |
| `base::gsub(x = "H-e-l-l-o World", pattern = "-", replacement = "")`         | Everytime the gsub finds the pattern, it will be replaced.         |
| `base::grep(x = c("apple", "banana", "melon", "apple"), pattern = "apple")`  | Returns the position                                               |
| `base::grepl(x = c("apple", "banana", "melon", "apple"), pattern = "apple")` | Returns a vector this TRUE and FALSE                               |
