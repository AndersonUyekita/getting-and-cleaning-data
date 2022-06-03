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
-   🌎 Rpubs: [Interactive
    Document](https://rpubs.com/AndersonUyekita/getting-and-cleaning-data_quiz-1)

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
data_1 %>% dplyr::select(VAL) %>% dplyr::filter(VAL == 24) %>% base::nrow()
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

# Let's see how it is
    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        dat %>% kableExtra::kbl() %>% kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        DT::datatable(dat)
    }
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
base::sum(dat$Zip*dat$Ext, na.rm=T)
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
xml_baltimore_restaurant <- xml2::as_list(x = xml2::read_xml(x = "./data/baltimore_restaurant.xml"))

# Converting XML file into data frame.
df_baltimore_restaurant <- tibble::as_tibble(x = xml_baltimore_restaurant) %>%
    tidyr::unnest_longer(col = response) %>%
    tidyr::unnest_wider(col = response) %>%
    tidyr::unnest(cols = names(.)) %>%
    tidyr::unnest(cols = names(.)) %>%
    readr::type_convert()
```

``` r
# Let's see how it is
    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        df_baltimore_restaurant %>%
            head(10) %>%
            kableExtra::kbl() %>%
            kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        DT::datatable(df_baltimore_restaurant)
    }
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
name
</th>
<th style="text-align:right;">
zipcode
</th>
<th style="text-align:left;">
neighborhood
</th>
<th style="text-align:right;">
councildistrict
</th>
<th style="text-align:left;">
policedistrict
</th>
<th style="text-align:left;">
location_1
</th>
<th style="text-align:left;">
response_id
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
410
</td>
<td style="text-align:right;">
21206
</td>
<td style="text-align:left;">
Frankford
</td>
<td style="text-align:right;">
2
</td>
<td style="text-align:left;">
NORTHEASTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
1919
</td>
<td style="text-align:right;">
21231
</td>
<td style="text-align:left;">
Fells Point
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:left;">
SOUTHEASTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
SAUTE
</td>
<td style="text-align:right;">
21224
</td>
<td style="text-align:left;">
Canton
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:left;">
SOUTHEASTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
\#1 CHINESE KITCHEN
</td>
<td style="text-align:right;">
21211
</td>
<td style="text-align:left;">
Hampden
</td>
<td style="text-align:right;">
14
</td>
<td style="text-align:left;">
NORTHERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
\#1 chinese restaurant
</td>
<td style="text-align:right;">
21223
</td>
<td style="text-align:left;">
Millhill
</td>
<td style="text-align:right;">
9
</td>
<td style="text-align:left;">
SOUTHWESTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
19TH HOLE
</td>
<td style="text-align:right;">
21218
</td>
<td style="text-align:left;">
Clifton Park
</td>
<td style="text-align:right;">
14
</td>
<td style="text-align:left;">
NORTHEASTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
3 KINGS
</td>
<td style="text-align:right;">
21205
</td>
<td style="text-align:left;">
McElderry Park
</td>
<td style="text-align:right;">
13
</td>
<td style="text-align:left;">
SOUTHEASTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
3 MILES HOUSE, INC.
</td>
<td style="text-align:right;">
21211
</td>
<td style="text-align:left;">
Remington
</td>
<td style="text-align:right;">
7
</td>
<td style="text-align:left;">
NORTHERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
3 W’S TAVERN
</td>
<td style="text-align:right;">
21205
</td>
<td style="text-align:left;">
McElderry Park
</td>
<td style="text-align:right;">
13
</td>
<td style="text-align:left;">
SOUTHEASTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
<tr>
<td style="text-align:left;">
300 SOUTH ANN STREET
</td>
<td style="text-align:right;">
21231
</td>
<td style="text-align:left;">
Upper Fells Point
</td>
<td style="text-align:right;">
1
</td>
<td style="text-align:left;">
SOUTHEASTERN
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
row
</td>
</tr>
</tbody>
</table>

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
a <- DT[,mean(pwgtp15),by=SEX]
b_2 <- Sys.time()

a_3 <- Sys.time()
a <- sapply(split(DT$pwgtp15,DT$SEX),mean)
b_3 <- Sys.time()

a_4 <- Sys.time()
a <- mean(DT[DT$SEX==1,]$pwgtp15); b <- mean(DT[DT$SEX==2,]$pwgtp15)
b_4 <- Sys.time()

# Printing the results.
print(c(b_1 - a_1, b_2 - a_2, b_3 - a_3, b_4 - a_4))
```

    ## Time differences in secs
    ## [1] 0.001893997 0.006535053 0.001427889 0.013365030

**NOTE:** The time differences will lead to a wrong answer. According to
the “data.table video”, the best solution would be that use DT due to:

-   Written in C, so it is much faster;
-   Much, much faster at subsetting, grouping, and updating.

The `DT[, mean(pwgtp15),by=SEX]` in a single line group and calculate
the average; meanwhile, the other alternatives use the DT package
partially to subset, having another step to calculate the mean.
