`Quiz 4` Getting and Cleaning Data
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
-   📆 Week 4
    -   Start: 2022/05/23
    -   Finish: 2022/05/24
-   🌎 Rpubs: [Interactive
    Document](https://rpubs.com/AndersonUyekita/quiz-4_getting-and-cleaning-data)

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
# Downloading the file "The American Community Survey".
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv",
                     destfile = "./data/acs.csv",
                     mode = "wb")

# Downloading the code book.
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf",
                     destfile = "./data/code_book.pdf",
                     mode = "wb")
```

Importing the downloaded file into R Object.

``` r
# Loading the ACS data.
acs <- utils::read.csv(file = "./data/acs.csv")

# Performing the given expression.
strsplit(x = colnames(acs), "wgtp")[123]
```

    ## [[1]]
    ## [1] ""   "15"

## Question 2

``` r
# Downloading the GDP data.
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FGDP.csv",
                     destfile = "./data/gdp.csv")

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

``` r
# Data Cleaning
df_gdp_tidy <- df_gdp %>%
    mutate(US.dollars. = sub(pattern = " ", replacement = "", x = US.dollars.)) %>%
    mutate(US.dollars. = gsub(pattern = ",", replacement = "", x = US.dollars.)) %>%
    mutate(gdp = as.numeric(US.dollars.)) %>%
    mutate(ranking = as.numeric(Ranking)) %>%
    select(-c(X.1, X.2, X.3, X.4, X.5, X.6)) %>%
    na.omit() %>%
    rename("CountryName" = Economy)
```

After the data manipulation, I have calculated the GDP average as
follows:

``` r
# Calculating the GDP Average
mean(df_gdp_tidy$gdp, na.rm = TRUE)
```

    ## [1] 377652.4

## Question 3

The pattern used to filter countries that start with “United” is:
`^United`.

``` r
# Readings: https://r4ds.had.co.nz/strings.html
#    ^ to match the start of the string.
#
# Solution 1:
grep(pattern = "^United", x = df_gdp_tidy$CountryName)
```

    ## [1]  1  6 32

``` r
# Solution 2:
df_gdp_tidy %>% filter(grepl(pattern = "^United", x = CountryName))
```

    ##     X Ranking          CountryName US.dollars.      gdp ranking
    ## 1 USA       1        United States   16244600  16244600       1
    ## 2 GBR       6       United Kingdom    2471784   2471784       6
    ## 3 ARE      32 United Arab Emirates     348595    348595      32

Both solutions have the same 3 countries, which starts with the United.

## Question 4

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
<th style="text-align:left;">
Currency.Unit
</th>
<th style="text-align:left;">
Latest.population.census
</th>
<th style="text-align:left;">
Latest.household.survey
</th>
<th style="text-align:left;">
Special.Notes
</th>
<th style="text-align:left;">
National.accounts.base.year
</th>
<th style="text-align:right;">
National.accounts.reference.year
</th>
<th style="text-align:right;">
System.of.National.Accounts
</th>
<th style="text-align:left;">
SNA.price.valuation
</th>
<th style="text-align:left;">
Alternative.conversion.factor
</th>
<th style="text-align:right;">
PPP.survey.year
</th>
<th style="text-align:left;">
Balance.of.Payments.Manual.in.use
</th>
<th style="text-align:left;">
External.debt.Reporting.status
</th>
<th style="text-align:left;">
System.of.trade
</th>
<th style="text-align:left;">
Government.Accounting.concept
</th>
<th style="text-align:left;">
IMF.data.dissemination.standard
</th>
<th style="text-align:left;">
Source.of.most.recent.Income.and.expenditure.data
</th>
<th style="text-align:left;">
Vital.registration.complete
</th>
<th style="text-align:left;">
Latest.agricultural.census
</th>
<th style="text-align:right;">
Latest.industrial.data
</th>
<th style="text-align:right;">
Latest.trade.data
</th>
<th style="text-align:right;">
Latest.water.withdrawal.data
</th>
<th style="text-align:left;">
X2.alpha.code
</th>
<th style="text-align:left;">
WB.2.code
</th>
<th style="text-align:left;">
Table.Name
</th>
<th style="text-align:left;">
Short.Name
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
<td style="text-align:left;">
Aruban florin
</td>
<td style="text-align:left;">
2000
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
1995
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
Special
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
2008
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
AW
</td>
<td style="text-align:left;">
AW
</td>
<td style="text-align:left;">
Aruba
</td>
<td style="text-align:left;">
Aruba
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
<td style="text-align:left;">
Euro
</td>
<td style="text-align:left;">
Register based
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
General
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
Yes
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
2006
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
AD
</td>
<td style="text-align:left;">
AD
</td>
<td style="text-align:left;">
Andorra
</td>
<td style="text-align:left;">
Andorra
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
<td style="text-align:left;">
Afghan afghani
</td>
<td style="text-align:left;">
1979
</td>
<td style="text-align:left;">
MICS, 2003
</td>
<td style="text-align:left;">
Fiscal year end: March 20; reporting period for national accounts data:
FY.
</td>
<td style="text-align:left;">
2002/2003
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
VAB
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
Actual
</td>
<td style="text-align:left;">
General
</td>
<td style="text-align:left;">
Consolidated
</td>
<td style="text-align:left;">
GDDS
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
2008
</td>
<td style="text-align:right;">
2000
</td>
<td style="text-align:left;">
AF
</td>
<td style="text-align:left;">
AF
</td>
<td style="text-align:left;">
Afghanistan
</td>
<td style="text-align:left;">
Afghanistan
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
<td style="text-align:left;">
Angolan kwanza
</td>
<td style="text-align:left;">
1970
</td>
<td style="text-align:left;">
MICS, 2001, MIS, 2006/07
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
1997
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
VAP
</td>
<td style="text-align:left;">
1991-96
</td>
<td style="text-align:right;">
2005
</td>
<td style="text-align:left;">
BPM5
</td>
<td style="text-align:left;">
Actual
</td>
<td style="text-align:left;">
Special
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
GDDS
</td>
<td style="text-align:left;">
IHS, 2000
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
1964-65
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
1991
</td>
<td style="text-align:right;">
2000
</td>
<td style="text-align:left;">
AO
</td>
<td style="text-align:left;">
AO
</td>
<td style="text-align:left;">
Angola
</td>
<td style="text-align:left;">
Angola
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
<td style="text-align:left;">
Albanian lek
</td>
<td style="text-align:left;">
2001
</td>
<td style="text-align:left;">
MICS, 2005
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
1996
</td>
<td style="text-align:right;">
1993
</td>
<td style="text-align:left;">
VAB
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
2005
</td>
<td style="text-align:left;">
BPM5
</td>
<td style="text-align:left;">
Actual
</td>
<td style="text-align:left;">
General
</td>
<td style="text-align:left;">
Consolidated
</td>
<td style="text-align:left;">
GDDS
</td>
<td style="text-align:left;">
LSMS, 2005
</td>
<td style="text-align:left;">
Yes
</td>
<td style="text-align:left;">
1998
</td>
<td style="text-align:right;">
2005
</td>
<td style="text-align:right;">
2008
</td>
<td style="text-align:right;">
2000
</td>
<td style="text-align:left;">
AL
</td>
<td style="text-align:left;">
AL
</td>
<td style="text-align:left;">
Albania
</td>
<td style="text-align:left;">
Albania
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
<td style="text-align:left;">
U.A.E. dirham
</td>
<td style="text-align:left;">
2005
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
1995
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
VAB
</td>
<td style="text-align:left;">
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:left;">
BPM4
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
General
</td>
<td style="text-align:left;">
Consolidated
</td>
<td style="text-align:left;">
GDDS
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
</td>
<td style="text-align:left;">
1998
</td>
<td style="text-align:right;">
NA
</td>
<td style="text-align:right;">
2008
</td>
<td style="text-align:right;">
2005
</td>
<td style="text-align:left;">
AE
</td>
<td style="text-align:left;">
AE
</td>
<td style="text-align:left;">
United Arab Emirates
</td>
<td style="text-align:left;">
United Arab Emirates
</td>
</tr>
</tbody>
</table>

``` r
# Loading GDP data.
df_gdp <- utils::read.csv(file = "./data/gdp.csv",
                          skip = 3,                   # The first rows of this database is blank
                          header = TRUE)              # Forcing the read.csv readh the first rows as header.

# CLEANING
df_gdp <- df_gdp %>%
    mutate(US.dollars. = sub(pattern = " ", replacement = "", x = US.dollars.)) %>%
    mutate(US.dollars. = gsub(pattern = ",", replacement = "", x = US.dollars.)) %>%
    mutate(US.dollars. = as.numeric(US.dollars.)) %>%
    mutate(Ranking = as.numeric(Ranking))

# CLEANING
df_gdp_tidy <- df_gdp %>%
    select(-c(X.1, X.2, X.3, X.4, X.5, X.6)) %>%
    rename(country_shortcode = X, ranking = Ranking, country = Economy, gdp = US.dollars.) %>%
    mutate(gdp = as.numeric(gdp)) %>%
    na.omit() %>%
    filter(ranking %in% 1:190)

# CLEANING
df_education_tidy <- df_education %>%
    rename(country_shortcode = CountryCode)

# Merging
df_gdp_edu <- merge(x = df_education_tidy, y = df_gdp_tidy) 
```

In the `Special.Notes` column, it is possible to track when the Fiscal
Year ends. I have used the expression “June 30” to find all the
countries with their fiscal year ending on this date.

``` r
# Printing the countries with the fiscal year ending on 30 June (end of June).
    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        df_gdp_edu %>%
            select(country, Special.Notes) %>%
            filter(grepl(pattern = "June 30", x = Special.Notes)) %>%
            kableExtra::kbl() %>% kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        df_gdp_edu %>%
            select(country, Special.Notes) %>%
            filter(grepl(pattern = "June 30", x = Special.Notes)) %>%
            DT::datatable()
    }
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:left;">
country
</th>
<th style="text-align:left;">
Special.Notes
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:left;">
Australia
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
FY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Bangladesh
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
FY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Botswana
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
FY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Egypt, Arab Rep. 
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
FY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Gambia, The
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
CY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Kenya
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
CY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Kuwait
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
CY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Pakistan
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
FY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Puerto Rico
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
FY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Sierra Leone
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
CY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Sweden
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
CY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Uganda
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
FY.
</td>
</tr>
<tr>
<td style="text-align:left;">
Zimbabwe
</td>
<td style="text-align:left;">
Fiscal year end: June 30; reporting period for national accounts data:
CY.
</td>
</tr>
</tbody>
</table>

Counting the number of countries.

``` r
# Filtering and counting the countries with fiscal year ending on June.
df_gdp_edu %>%
    select(country, Special.Notes) %>%
    filter(grepl(pattern = "June 30", x = Special.Notes)) %>%
    nrow()
```

    ## [1] 13

## Question 5

Executing the given code:

``` r
# Loading the quantmod package
library(quantmod)

# Gathering data from Amazon.
amzn = getSymbols("AMZN",auto.assign=FALSE)

# Gathering the dates from each data.
sampleTimes = index(amzn)
```

I have converted it into a tibble dataframe to be able to use the
tidyverse package.

``` r
# Converting the amzn object into Tibble.
data_q5 <- as_tibble(amzn)

# Adding the date column.
data_q5['date'] <- sampleTimes

# Filtering data only from 2012.
data_q5_2012 <- data_q5 %>%
    filter(date >= "2012-01-01" & date <= "2012-12-31")

# Showing the data gathered.
    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        data_q5_2012 %>%
            head() %>%
            kableExtra::kbl() %>%
            kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        DT::datatable(data_q5_2012)
    }
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:right;">
AMZN.Open
</th>
<th style="text-align:right;">
AMZN.High
</th>
<th style="text-align:right;">
AMZN.Low
</th>
<th style="text-align:right;">
AMZN.Close
</th>
<th style="text-align:right;">
AMZN.Volume
</th>
<th style="text-align:right;">
AMZN.Adjusted
</th>
<th style="text-align:left;">
date
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
175.89
</td>
<td style="text-align:right;">
179.48
</td>
<td style="text-align:right;">
175.55
</td>
<td style="text-align:right;">
179.03
</td>
<td style="text-align:right;">
5110800
</td>
<td style="text-align:right;">
179.03
</td>
<td style="text-align:left;">
2012-01-03
</td>
</tr>
<tr>
<td style="text-align:right;">
179.21
</td>
<td style="text-align:right;">
180.50
</td>
<td style="text-align:right;">
176.07
</td>
<td style="text-align:right;">
177.51
</td>
<td style="text-align:right;">
4205200
</td>
<td style="text-align:right;">
177.51
</td>
<td style="text-align:left;">
2012-01-04
</td>
</tr>
<tr>
<td style="text-align:right;">
175.94
</td>
<td style="text-align:right;">
178.25
</td>
<td style="text-align:right;">
174.05
</td>
<td style="text-align:right;">
177.61
</td>
<td style="text-align:right;">
3809100
</td>
<td style="text-align:right;">
177.61
</td>
<td style="text-align:left;">
2012-01-05
</td>
</tr>
<tr>
<td style="text-align:right;">
178.07
</td>
<td style="text-align:right;">
184.65
</td>
<td style="text-align:right;">
177.50
</td>
<td style="text-align:right;">
182.61
</td>
<td style="text-align:right;">
7008400
</td>
<td style="text-align:right;">
182.61
</td>
<td style="text-align:left;">
2012-01-06
</td>
</tr>
<tr>
<td style="text-align:right;">
182.76
</td>
<td style="text-align:right;">
184.37
</td>
<td style="text-align:right;">
177.00
</td>
<td style="text-align:right;">
178.56
</td>
<td style="text-align:right;">
5056900
</td>
<td style="text-align:right;">
178.56
</td>
<td style="text-align:left;">
2012-01-09
</td>
</tr>
<tr>
<td style="text-align:right;">
181.10
</td>
<td style="text-align:right;">
182.40
</td>
<td style="text-align:right;">
177.10
</td>
<td style="text-align:right;">
179.34
</td>
<td style="text-align:right;">
3985800
</td>
<td style="text-align:right;">
179.34
</td>
<td style="text-align:left;">
2012-01-10
</td>
</tr>
</tbody>
</table>

The number of observations in 2012:

``` r
# How many values in 2012
nrow(data_q5_2012)
```

    ## [1] 250

I have used the Lubridate package to work with a date type. In addition,
I have added a column to store the wee day.

``` r
# Ensuring to show the Week days in English.s
Sys.setlocale("LC_ALL","English")
```

    ## [1] "LC_COLLATE=English_United States.1252;LC_CTYPE=English_United States.1252;LC_MONETARY=English_United States.1252;LC_NUMERIC=C;LC_TIME=English_United States.1252"

``` r
# Adding a new column to store the wee days.
data_q5_2012_wdays <- data_q5_2012 %>%
    mutate(wday = lubridate::wday(x = lubridate::ymd(date), label=TRUE))

# Showing the data with the new column of week day.
    # CASE: github_document
    if(!knitr::is_html_output()) {
    
        # Static table using Kable Package.
        data_q5_2012_wdays %>%
            head() %>%
            kableExtra::kbl() %>%
            kableExtra::kable_styling()
    
    # CASE: hmtl_document
    } else {
    
        # Interactive table using DT package.
        DT::datatable(data_q5_2012_wdays)
    }
```

<table class="table" style="margin-left: auto; margin-right: auto;">
<thead>
<tr>
<th style="text-align:right;">
AMZN.Open
</th>
<th style="text-align:right;">
AMZN.High
</th>
<th style="text-align:right;">
AMZN.Low
</th>
<th style="text-align:right;">
AMZN.Close
</th>
<th style="text-align:right;">
AMZN.Volume
</th>
<th style="text-align:right;">
AMZN.Adjusted
</th>
<th style="text-align:left;">
date
</th>
<th style="text-align:left;">
wday
</th>
</tr>
</thead>
<tbody>
<tr>
<td style="text-align:right;">
175.89
</td>
<td style="text-align:right;">
179.48
</td>
<td style="text-align:right;">
175.55
</td>
<td style="text-align:right;">
179.03
</td>
<td style="text-align:right;">
5110800
</td>
<td style="text-align:right;">
179.03
</td>
<td style="text-align:left;">
2012-01-03
</td>
<td style="text-align:left;">
Tue
</td>
</tr>
<tr>
<td style="text-align:right;">
179.21
</td>
<td style="text-align:right;">
180.50
</td>
<td style="text-align:right;">
176.07
</td>
<td style="text-align:right;">
177.51
</td>
<td style="text-align:right;">
4205200
</td>
<td style="text-align:right;">
177.51
</td>
<td style="text-align:left;">
2012-01-04
</td>
<td style="text-align:left;">
Wed
</td>
</tr>
<tr>
<td style="text-align:right;">
175.94
</td>
<td style="text-align:right;">
178.25
</td>
<td style="text-align:right;">
174.05
</td>
<td style="text-align:right;">
177.61
</td>
<td style="text-align:right;">
3809100
</td>
<td style="text-align:right;">
177.61
</td>
<td style="text-align:left;">
2012-01-05
</td>
<td style="text-align:left;">
Thu
</td>
</tr>
<tr>
<td style="text-align:right;">
178.07
</td>
<td style="text-align:right;">
184.65
</td>
<td style="text-align:right;">
177.50
</td>
<td style="text-align:right;">
182.61
</td>
<td style="text-align:right;">
7008400
</td>
<td style="text-align:right;">
182.61
</td>
<td style="text-align:left;">
2012-01-06
</td>
<td style="text-align:left;">
Fri
</td>
</tr>
<tr>
<td style="text-align:right;">
182.76
</td>
<td style="text-align:right;">
184.37
</td>
<td style="text-align:right;">
177.00
</td>
<td style="text-align:right;">
178.56
</td>
<td style="text-align:right;">
5056900
</td>
<td style="text-align:right;">
178.56
</td>
<td style="text-align:left;">
2012-01-09
</td>
<td style="text-align:left;">
Mon
</td>
</tr>
<tr>
<td style="text-align:right;">
181.10
</td>
<td style="text-align:right;">
182.40
</td>
<td style="text-align:right;">
177.10
</td>
<td style="text-align:right;">
179.34
</td>
<td style="text-align:right;">
3985800
</td>
<td style="text-align:right;">
179.34
</td>
<td style="text-align:left;">
2012-01-10
</td>
<td style="text-align:left;">
Tue
</td>
</tr>
</tbody>
</table>

Finally, the number of Monday in 2012:

``` r
# Number of observations in 2012 on Mondays.
data_q5_2012_wdays%>%
    filter(wday == "Mon") %>%
    nrow()
```

    ## [1] 47
