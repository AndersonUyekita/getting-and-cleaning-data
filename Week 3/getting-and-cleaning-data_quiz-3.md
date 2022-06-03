`Quiz 3` Getting and Cleaning Data
================

-   👨🏻‍💻 Author: Anderson H Uyekita
-   📚 Specialization: <a
    href="https://www.coursera.org/specializations/data-science-foundations-r"
    target="_blank" rel="noopener">Data Science: Foundations using R
    Specialization</a>
-   📖 Course:
    <a href="https://www.coursera.org/learn/data-cleaning" target="_blank"
    rel="noopener">Getting and Cleaning Data</a>
    -   🧑‍🏫 Instructor: Jeffrey Leek
-   📆 Week 3
    -   🚦 Start: 2022/05/23
    -   🏁 Finish: 2022/05/23
-   🌎 Rpubs: [Interactive
    Document](https://rpubs.com/AndersonUyekita/quiz-3_getting-and-cleaning-data)

------------------------------------------------------------------------

``` r
# Checking if the subfolder already exists.
if (!dir.exists("data")) {
    
    # Creating a subfolder to store the data.
    dir.create(path = "./data")
}
```

## Question 1

``` r
# Downloading the American Community Survey file.
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv",
                     destfile = "./data/acs.csv")

# Downloading the code book.
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf",
                     destfile = "./data/code_book.pdf",
                     mode = "wb")

# Loading CSV file into R object.
acs <- utils::read.csv(file = "./data/acs.csv")
```

The American Community Survey Dataset.

``` r
# First rows of ACS and first columns.

# Let's see how it is
    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        acs %>% select(c(1:5)) %>%
            head(5) %>%
            kableExtra::kbl() %>%
            kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        DT::datatable(acs)
    }
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
RT
</th>
<th style="text-align:right;">
SERIALNO
</th>
<th style="text-align:right;">
DIVISION
</th>
<th style="text-align:right;">
PUMA
</th>
<th style="text-align:right;">
REGION
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
H
</td>
<td style="text-align:right;">
186
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
700
</td>
<td style="text-align:right;">
4
</td>
</tr>
<tr>
<td style="text-align:left;">
H
</td>
<td style="text-align:right;">
306
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
700
</td>
<td style="text-align:right;">
4
</td>
</tr>
<tr>
<td style="text-align:left;">
H
</td>
<td style="text-align:right;">
395
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
100
</td>
<td style="text-align:right;">
4
</td>
</tr>
<tr>
<td style="text-align:left;">
H
</td>
<td style="text-align:right;">
506
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
700
</td>
<td style="text-align:right;">
4
</td>
</tr>
<tr>
<td style="text-align:left;">
H
</td>
<td style="text-align:right;">
835
</td>
<td style="text-align:right;">
8
</td>
<td style="text-align:right;">
800
</td>
<td style="text-align:right;">
4
</td>
</tr>
</tbody>
</table>

Dimensions of ACS dataset:

``` r
# Number of observations and Variables
dim(acs)
```

    ## [1] 6496  188

Following the question instruction, I will only display the first 3
values.

Based on the `code book` provided:

-   *households on greater than 10 acres*, means: ACR == 3
-   *sold more than $10,000 worth of agriculture products*, means: AGS
    == 6

``` r
# According to the statement.
agricultureLogical <- acs$ACR == 3 & acs$AGS == 6

# Performing the given expression:
head(which(agricultureLogical), 3)
```

    ## [1] 125 238 262

## Question 2

``` r
# Loading the JPEG package.
library(jpeg)

# Downloading the KPEG file.
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fjeff.jpg",
                     destfile = "./data/image_file.jpeg", mode = "wb")

# Loading the JPEG file. Following the instruction to set NATIVE as TRUE.
image <- jpeg::readJPEG(source = "./data/image_file.jpeg",
                        native = TRUE)

# Answering the quantiles 30% and 80%.
c(quantile(x = image, 0.3), quantile(x = image, 0.8))
```

    ##       30%       80% 
    ## -15259150 -10575416

My answer is a bit different, as warned by the question instruction.

## Question 3

``` r
# Downloading the GDP data.
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FGDP.csv",
                     destfile = "./data/gdp.csv")

# Downloading the Educational data.
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FEDSTATS_Country.csv",
                     destfile = "./data/education.csv")

# Loading Education data.
df_education <- utils::read.csv(file = "./data/education.csv")

# First rows os Education Data.
    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        df_education %>%
            select(c(1:6)) %>%
            head() %>%
            kableExtra::kbl() %>%
            kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        DT::datatable(df_education)
    }
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
CountryCode
</th>
<th style="text-align:left;">
Long.Name
</th>
<th style="text-align:left;">
Income.Group
</th>
<th style="text-align:left;">
Region
</th>
<th style="text-align:left;">
Lending.category
</th>
<th style="text-align:left;">
Other.groups
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
ABW
</td>
<td style="text-align:left;">
Aruba
</td>
<td style="text-align:left;">
High income: nonOECD
</td>
<td style="text-align:left;">
Latin America & Caribbean
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
</tr>
<tr>
<td style="text-align:left;">
ADO
</td>
<td style="text-align:left;">
Principality of Andorra
</td>
<td style="text-align:left;">
High income: nonOECD
</td>
<td style="text-align:left;">
Europe & Central Asia
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
</tr>
<tr>
<td style="text-align:left;">
AFG
</td>
<td style="text-align:left;">
Islamic State of Afghanistan
</td>
<td style="text-align:left;">
Low income
</td>
<td style="text-align:left;">
South Asia
</td>
<td style="text-align:left;">
IDA
</td>
<td style="text-align:left;">
HIPC
</td>
</tr>
<tr>
<td style="text-align:left;">
AGO
</td>
<td style="text-align:left;">
People’s Republic of Angola
</td>
<td style="text-align:left;">
Lower middle income
</td>
<td style="text-align:left;">
Sub-Saharan Africa
</td>
<td style="text-align:left;">
IDA
</td>
<td style="text-align:left;">
</td>
</tr>
<tr>
<td style="text-align:left;">
ALB
</td>
<td style="text-align:left;">
Republic of Albania
</td>
<td style="text-align:left;">
Upper middle income
</td>
<td style="text-align:left;">
Europe & Central Asia
</td>
<td style="text-align:left;">
IBRD
</td>
<td style="text-align:left;">
</td>
</tr>
<tr>
<td style="text-align:left;">
ARE
</td>
<td style="text-align:left;">
United Arab Emirates
</td>
<td style="text-align:left;">
High income: nonOECD
</td>
<td style="text-align:left;">
Middle East & North Africa
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
</tr>
</tbody>
</table>

``` r
# Loading GDP data.
df_gdp <- utils::read.csv(file = "./data/gdp.csv",
                          skip = 3,                   # The first rows of this database is blank
                          header = TRUE)              # Forcing the read.csv readh the first rows as header.

# First rows of GDP data.

    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        df_gdp %>%
            head() %>%
            kableExtra::kbl() %>%
            kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        DT::datatable(df_gdp)
    }
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
X
</th>
<th style="text-align:left;">
Ranking
</th>
<th style="text-align:left;">
X.1
</th>
<th style="text-align:left;">
Economy
</th>
<th style="text-align:left;">
US.dollars.
</th>
<th style="text-align:left;">
X.2
</th>
<th style="text-align:left;">
X.3
</th>
<th style="text-align:left;">
X.4
</th>
<th style="text-align:left;">
X.5
</th>
<th style="text-align:left;">
X.6
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
USA
</td>
<td style="text-align:left;">
1
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
United States
</td>
<td style="text-align:left;">
16,244,600
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
CHN
</td>
<td style="text-align:left;">
2
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
China
</td>
<td style="text-align:left;">
8,227,103
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
JPN
</td>
<td style="text-align:left;">
3
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
Japan
</td>
<td style="text-align:left;">
5,959,718
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
DEU
</td>
<td style="text-align:left;">
4
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
Germany
</td>
<td style="text-align:left;">
3,428,131
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
</tr>
<tr>
<td style="text-align:left;">
FRA
</td>
<td style="text-align:left;">
5
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
France
</td>
<td style="text-align:left;">
2,612,878
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
<td style="text-align:left;">
NA
</td>
</tr>
</tbody>
</table>

We need to match those databases on the `country shortcode`. For this
reason, we need to be sure if this `country shortcode` is present in
both datasets. The GDP database is not cleaned.

As you can see, we do not have columns with identical names neither GDP
columns with numeric.

``` r
# DATA CLEANING: Fixing the GDP to be number and removing comas.
df_gdp <- df_gdp %>%
    mutate(US.dollars. = sub(pattern = " ", replacement = "", x = US.dollars.)) %>%
    mutate(US.dollars. = gsub(pattern = ",", replacement = "", x = US.dollars.)) %>%
    mutate(US.dollars. = as.numeric(US.dollars.)) %>%
    mutate(Ranking = as.numeric(Ranking))

# DATA CLEANING: Removing unecessary columns of GDP database.
df_gdp_tidy <- df_gdp %>%
    select(-c(X.1, X.2, X.3, X.4, X.5, X.6)) %>%
    rename(country_shortcode = X, ranking = Ranking, country = Economy, gdp = US.dollars.) %>%
    mutate(gdp = as.numeric(gdp)) %>%
    na.omit() %>%
    filter(ranking %in% 1:190)

# DATA CLEANING: Using the same column name to Country.
df_education_tidy <- df_education %>%
    rename(country_shortcode = CountryCode)
```

After the cleaning process, I merged those datasets into one.

The 13th country in the ordered dataset in a crescent way:

``` r
# Merging Education and GDP databses.
df_gdp_edu <- merge(x = df_education_tidy, y = df_gdp_tidy) 

# Searching the 13th country in crescent order.
df_gdp_edu%>%
    select(country_shortcode, Long.Name, gdp) %>%
    arrange(gdp) %>%
    filter(order(gdp) == 13)
```

    ##   country_shortcode           Long.Name gdp
    ## 1               KNA St. Kitts and Nevis 767

The number of countries with GDP and Education database match.

``` r
# Counting the number of countries with match.
df_gdp_edu %>% nrow()
```

    ## [1] 189

## Question 4

Investigating the `Income.Group` variable. I just want to see what is
the “levels”.

``` r
# Classes of Income Group
unique(df_gdp_edu$Income.Group)
```

    ## [1] "High income: nonOECD" "Low income"           "Lower middle income" 
    ## [4] "Upper middle income"  "High income: OECD"

Now, I could calculate the average of each `Income.Group` level. The GDP
average of `High income: OECD` and `High income: nonOECD` from
`Income.Group` could be found below:

``` r
# Calculating the average of each Income Group Level.
df_gdp_edu %>% group_by(Income.Group) %>% 
    summarise(AVG = mean(as.numeric(ranking)))
```

    ## # A tibble: 5 × 2
    ##   Income.Group           AVG
    ##   <chr>                <dbl>
    ## 1 High income: nonOECD  91.9
    ## 2 High income: OECD     33.0
    ## 3 Low income           134. 
    ## 4 Lower middle income  108. 
    ## 5 Upper middle income   92.1

## Question 5

Let’s see the quantiles boundaries.

``` r
# Creating the groups limits.
quantile(x = as.numeric(df_gdp_edu$ranking), c(0.0, 0.2, 0.4, 0.6, 0.8, 1.0))
```

    ##    0%   20%   40%   60%   80%  100% 
    ##   1.0  38.6  76.2 113.8 152.4 190.0

Following the question instructions, I need to create a CUT. To do so, I
will create a new variable, `ranking_group`, to store these grouping
classifications.

``` r
# Adding a new column to the merged dataframe.
df_gdp_edu$ranking_group <- cut(x = df_gdp_edu$ranking, breaks = quantile(x = as.numeric(df_gdp_edu$ranking), c(0.0, 0.2, 0.4, 0.6, 0.8, 1.0)))

# Printing the results of this new column.
df_gdp_edu %>% select(country_shortcode, Long.Name,gdp,ranking_group) %>% head()
```

    ##   country_shortcode                    Long.Name    gdp ranking_group
    ## 1               ABW                        Aruba   2584     (152,190]
    ## 2               AFG Islamic State of Afghanistan  20497    (76.2,114]
    ## 3               AGO  People's Republic of Angola 114147   (38.6,76.2]
    ## 4               ALB          Republic of Albania  12648     (114,152]
    ## 5               ARE         United Arab Emirates 348595      (1,38.6]
    ## 6               ARG           Argentine Republic 475502      (1,38.6]

I have already inserted this new variable to classify each country based
on those quantiles. I need to count the number of countries in
`Lower middle income` in `Income.Group`.

``` r
df_gdp_edu %>%
    group_by(ranking_group) %>%
    filter(Income.Group == "Lower middle income") %>%
    summarise(n = n())
```

    ## # A tibble: 5 × 2
    ##   ranking_group     n
    ##   <fct>         <int>
    ## 1 (1,38.6]          5
    ## 2 (38.6,76.2]      13
    ## 3 (76.2,114]       11
    ## 4 (114,152]         9
    ## 5 (152,190]        16
