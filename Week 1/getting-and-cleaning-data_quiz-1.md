`Quiz 1` Getting and Cleaning Data
================

-   👨🏻‍💻 Author: Anderson H Uyekita
-   📚 Specialization: [Data Science: Foundations using R
    Specialization](https://www.coursera.org/specializations/data-science-foundations-r)
-   📖 Course: [Getting and Cleaning
    Data](https://www.coursera.org/learn/data-cleaning)
    -   🧑‍🏫 Instructor: Jeffrey Leek
-   📆 Week 1
    -   🚦 Start: 2022/05/20
    -   🏁 Finish: 2022/05/20

------------------------------------------------------------------------

This Quiz is part of the Getting and Cleaning Data Course.

To turn the folder more structured, I will create a subfolder to host
the dataset.

``` r
# Checking if the subfolder already exists.
if (!dir.exists("data")) {
    
    # Creating a subfolder to store the data.
    dir.create(path = "./data")
}
```

Questions 1 and 2 will share the same dataset.

``` r
# Downloading the data to Questions 1 and 2 of Quiz 1
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv",
                     destfile = "./data/survey_data_housing.csv",
                     quiet = TRUE)

# Downloading the code book Questions 1 and 2 of Quiz 1
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf",
                     destfile = "./data/code_book.pdf",
                     quiet = TRUE, mode = "wb")
```

## Question 1

``` r
# According to the code book the VAL columns is about the Property value
#
# Property value
#  bb .N/A (GQ/rental unit/vacant, not for sale only)
#  01 .Less than $ 10000
#  02 .$ 10000 - $ 14999
#  03 .$ 15000 - $ 19999
#  04 .$ 20000 - $ 24999
#  05 .$ 25000 - $ 29999
#  06 .$ 30000 - $ 34999
#  07 .$ 35000 - $ 39999
#  08 .$ 40000 - $ 49999
#  09 .$ 50000 - $ 59999
#  10 .$ 60000 - $ 69999
#  11 .$ 70000 - $ 79999
#  12 .$ 80000 - $ 89999
#  13 .$ 90000 - $ 99999
#  14 .$100000 - $124999
#  15 .$125000 - $149999
#  16 .$150000 - $174999
#  17 .$175000 - $199999
#  18 .$200000 - $249999
#  19 .$250000 - $299999
#  20 .$300000 - $399999
#  21 .$400000 - $499999
#  22 .$500000 - $749999
#  23 .$750000 - $999999
#  24 .$1000000+
#
# I need to filter VAL with value 24.

# Loading the data
data_1 <- utils::read.csv(file = "./data/survey_data_housing.csv")

# Subsetting and filtering to find properties above 1 million USD.
data_1 %>% dplyr::select(VAL) %>% filter(VAL == 24) %>% nrow()
```

    ## [1] 53

## Question 2

``` r
# Family type and employment status
#
# b .N/A (GQ/vacant/not a family)
# 1 .Married-couple family: Husband and wife in LF
# 2 .Married-couple family: Husband in labor force, wife not in LF
# 3 .Married-couple family: Husband not in LF, wife in LF
# 4 .Married-couple family: Neither husband nor wife in LF
# 5 .Other family: Male householder, no wife present, in LF
# 6 .Other family: Male householder, no wife present, not in LF
# 7 .Other family: Female householder, no husband.present, in LF
# 8 .Other family: Female householder, no husband present, not in LF 

# There are two variables into a single column: family type and employment status.
```

## Question 3

``` r
# Downloading the data to question 3 of Quiz 1
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FDATA.gov_NGAP.xlsx",
                     destfile = "./data/natural_gas.xlsx",
                     method = "curl",
                     quiet = TRUE)

# Loading the data
dat <- xlsx::read.xlsx(file = "./data/natural_gas.xlsx",
                       sheetIndex = 1,
                       rowIndex = 18:23,
                       colIndex = 7:15,
                       header = TRUE)

# Loading Kable
library(kableExtra)

# Let's see how it is
dat %>% kableExtra::kbl() %>% kableExtra::kable_styling()
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:right;">
Zip
</th>
<th style="text-align:right;">
CuCurrent
</th>
<th style="text-align:right;">
PaCurrent
</th>
<th style="text-align:right;">
PoCurrent
</th>
<th style="text-align:left;">
Contact
</th>
<th style="text-align:right;">
Ext
</th>
<th style="text-align:left;">
Fax
</th>
<th style="text-align:left;">
email
</th>
<th style="text-align:right;">
Status
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
74136
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
918-491-6998
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
918-491-6659
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
1
</td>
</tr>
<tr>
<td style="text-align:right;">
30329
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
404-321-5711
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
1
</td>
</tr>
<tr>
<td style="text-align:right;">
74136
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
918-523-2516
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
918-523-2522
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
1
</td>
</tr>
<tr>
<td style="text-align:right;">
80203
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
303-864-1919
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
1
</td>
</tr>
<tr>
<td style="text-align:right;">
80120
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:right;">
0
</td>
<td style="text-align:left;">
345-098-8890
</td>
<td style="text-align:right;">
456
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:right;">
1
</td>
</tr>
</tbody>
</table>

Calculating the expression: `sum(dat$Zip*dat$Ext,na.rm=T)`

``` r
# Printing the results.
sum(dat$Zip*dat$Ext,na.rm=T)
```

    ## [1] 36534720

## Question 4

``` r
# References
# 
# * https://urbandatapalette.com/post/2021-03-xml-dataframe-r/
# * https://blog.gtwang.org/r/r-xml-package-parsing-and-generating-xml-tutorial/

# Downloading the data to question 4 of Quiz 1
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml",
                     destfile = "./data/baltimore_restaurant.xml",
                     method = "curl",
                     quiet = TRUE)

# Parsing the XML file.
xml_baltimore_restaurant <- as_list(read_xml(x = "./data/baltimore_restaurant.xml"))

# Converting XML file into data frame.
df_baltimore_restaurant <- tibble::as_tibble(xml_baltimore_restaurant) %>%
    unnest_longer(response) %>% unnest_wider(response) %>%
    unnest(cols = names(.)) %>%
    unnest(cols = names(.)) %>%
    readr::type_convert()
```

Answer:

``` r
# Counting number of restaurant with zipcode 21231
df_baltimore_restaurant %>% filter(zipcode == 21231) %>% nrow()
```

    ## [1] 127

## Question 5

``` r
# Downloading the data to question 5 of Quiz 1
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06pid.csv",
                     destfile = "./data/housing_idaho.csv",
                     method = "curl",
                     quiet = TRUE)

# Loading the housing_idaho.csv file.
DT <- fread(file = "./data/housing_idaho.csv")

# Calculating the time elapses
a_1 <- Sys.time()
a <- tapply(DT$pwgtp15,DT$SEX,mean)
b_1 <- Sys.time()

a_2 <- Sys.time()
a < -DT[,mean(pwgtp15),by=SEX]
```

    ##        SEX    V1
    ## [1,] FALSE FALSE
    ## [2,] FALSE FALSE

``` r
b_2 <- Sys.time()

a_3 <- Sys.time()
a <- sapply(split(DT$pwgtp15,DT$SEX),mean)
b_3 <- Sys.time()

a_4 <- Sys.time()
a < -mean(DT[DT$SEX==1,]$pwgtp15); b <- mean(DT[DT$SEX==2,]$pwgtp15)
```

    ##     1     2 
    ## FALSE FALSE

``` r
b_4 <- Sys.time()

# Printing the results.
print(c(b_1 - a_1, b_2 - a_2, b_3 - a_3, b_4 - a_4))
```

    ## Time differences in secs
    ## [1] 0.002102137 0.006941080 0.001256943 0.012876987

**NOTE:** The time differences will lead to a wrong answer. According to
the “data.table video”, the best solution would be that use DT due to:

-   Written in C, so it is much faster;
-   Much, much faster at subsetting, grouping, and updating.

The `DT[, mean(pwgtp15),by=SEX]` in a single line group and calculate
the average; meanwhile, the other alternatives use the DT package
partially to subset, having another step to calculate the mean.
