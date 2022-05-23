Getting and Cleaning Data
================
Anderson H. Uyekita
2022-05-23

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
utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2FPUMSDataDict06.pdf ",
                     destfile = "./data/code_book.pdf",
                     mode = "wb")

# Loading CSV file into R object.
acs <- utils::read.csv(file = "./data/acs.csv")
```

The American Community Survey Dataset.

Dimensions of ACS dataset:

``` r
agricultureLogical <- acs$ACR == 3 & acs$AGS == 6

head(which(agricultureLogical), 3)
```

    ## [1] 125 238 262

## Question 2

``` r
library(jpeg)

utils::download.file(url = "https://d396qusza40orc.cloudfront.net/getdata%2Fjeff.jpg",
                     destfile = "./data/image_file.jpeg", mode = "wb")



image <- jpeg::readJPEG(source = "./data/image_file.jpeg",
                        native = TRUE)

c(quantile(x = image, 0.3), quantile(x = image, 0.8))
```

    ##       30%       80% 
    ## -15258512 -10575416

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
head(df_education)
```

    ##   CountryCode                    Long.Name         Income.Group
    ## 1         ABW                        Aruba High income: nonOECD
    ## 2         ADO      Principality of Andorra High income: nonOECD
    ## 3         AFG Islamic State of Afghanistan           Low income
    ## 4         AGO  People's Republic of Angola  Lower middle income
    ## 5         ALB          Republic of Albania  Upper middle income
    ## 6         ARE         United Arab Emirates High income: nonOECD
    ##                       Region Lending.category Other.groups  Currency.Unit
    ## 1  Latin America & Caribbean                                Aruban florin
    ## 2      Europe & Central Asia                                         Euro
    ## 3                 South Asia              IDA         HIPC Afghan afghani
    ## 4         Sub-Saharan Africa              IDA              Angolan kwanza
    ## 5      Europe & Central Asia             IBRD                Albanian lek
    ## 6 Middle East & North Africa                                U.A.E. dirham
    ##   Latest.population.census  Latest.household.survey
    ## 1                     2000                         
    ## 2           Register based                         
    ## 3                     1979               MICS, 2003
    ## 4                     1970 MICS, 2001, MIS, 2006/07
    ## 5                     2001               MICS, 2005
    ## 6                     2005                         
    ##                                                                 Special.Notes
    ## 1                                                                            
    ## 2                                                                            
    ## 3 Fiscal year end: March 20; reporting period for national accounts data: FY.
    ## 4                                                                            
    ## 5                                                                            
    ## 6                                                                            
    ##   National.accounts.base.year National.accounts.reference.year
    ## 1                        1995                               NA
    ## 2                                                           NA
    ## 3                   2002/2003                               NA
    ## 4                        1997                               NA
    ## 5                                                         1996
    ## 6                        1995                               NA
    ##   System.of.National.Accounts SNA.price.valuation Alternative.conversion.factor
    ## 1                          NA                                                  
    ## 2                          NA                                                  
    ## 3                          NA                 VAB                              
    ## 4                          NA                 VAP                       1991-96
    ## 5                        1993                 VAB                              
    ## 6                          NA                 VAB                              
    ##   PPP.survey.year Balance.of.Payments.Manual.in.use
    ## 1              NA                                  
    ## 2              NA                                  
    ## 3              NA                                  
    ## 4            2005                              BPM5
    ## 5            2005                              BPM5
    ## 6              NA                              BPM4
    ##   External.debt.Reporting.status System.of.trade Government.Accounting.concept
    ## 1                                        Special                              
    ## 2                                        General                              
    ## 3                         Actual         General                  Consolidated
    ## 4                         Actual         Special                              
    ## 5                         Actual         General                  Consolidated
    ## 6                                        General                  Consolidated
    ##   IMF.data.dissemination.standard
    ## 1                                
    ## 2                                
    ## 3                            GDDS
    ## 4                            GDDS
    ## 5                            GDDS
    ## 6                            GDDS
    ##   Source.of.most.recent.Income.and.expenditure.data Vital.registration.complete
    ## 1                                                                              
    ## 2                                                                           Yes
    ## 3                                                                              
    ## 4                                         IHS, 2000                            
    ## 5                                        LSMS, 2005                         Yes
    ## 6                                                                              
    ##   Latest.agricultural.census Latest.industrial.data Latest.trade.data
    ## 1                                                NA              2008
    ## 2                                                NA              2006
    ## 3                                                NA              2008
    ## 4                    1964-65                     NA              1991
    ## 5                       1998                   2005              2008
    ## 6                       1998                     NA              2008
    ##   Latest.water.withdrawal.data X2.alpha.code WB.2.code           Table.Name
    ## 1                           NA            AW        AW                Aruba
    ## 2                           NA            AD        AD              Andorra
    ## 3                         2000            AF        AF          Afghanistan
    ## 4                         2000            AO        AO               Angola
    ## 5                         2000            AL        AL              Albania
    ## 6                         2005            AE        AE United Arab Emirates
    ##             Short.Name
    ## 1                Aruba
    ## 2              Andorra
    ## 3          Afghanistan
    ## 4               Angola
    ## 5              Albania
    ## 6 United Arab Emirates

``` r
# Loading GDP data.
df_gdp <- utils::read.csv(file = "./data/gdp.csv",
                          skip = 3,                   # The first rows of this database is blank
                          header = TRUE)              # Forcing the read.csv readh the first rows as header.

# First rows of GDP data.
head(df_gdp)
```

    ##     X Ranking X.1       Economy  US.dollars. X.2 X.3 X.4 X.5 X.6
    ## 1              NA                                 NA  NA  NA  NA
    ## 2 USA       1  NA United States  16,244,600       NA  NA  NA  NA
    ## 3 CHN       2  NA         China   8,227,103       NA  NA  NA  NA
    ## 4 JPN       3  NA         Japan   5,959,718       NA  NA  NA  NA
    ## 5 DEU       4  NA       Germany   3,428,131       NA  NA  NA  NA
    ## 6 FRA       5  NA        France   2,612,878       NA  NA  NA  NA

We need to match those databases on the `country shortcode`. For this
reason, we need to be sure if this `country shortcode` is present in
both datasets. The GDP database is not cleaned.

As you can see, we do not have columns with identical names, neither GDP
columns with numeric.

``` r
#
df_gdp <- df_gdp %>%
    mutate(US.dollars. = sub(pattern = " ", replacement = "", x = US.dollars.)) %>%
    mutate(US.dollars. = gsub(pattern = ",", replacement = "", x = US.dollars.)) %>%
    mutate(US.dollars. = as.numeric(US.dollars.)) %>%
    mutate(Ranking = as.numeric(Ranking))

# 
df_gdp_tidy <- df_gdp %>%
    select(-c(X.1, X.2, X.3, X.4, X.5, X.6)) %>%
    rename(country_shortcode = X, ranking = Ranking, country = Economy, gdp = US.dollars.) %>%
    mutate(gdp = as.numeric(gdp)) %>%
    na.omit() %>%
    filter(ranking %in% 1:190)

# 
df_education_tidy <- df_education %>%
    rename(country_shortcode = CountryCode)
```

``` r
df_gdp_edu <- merge(x = df_education_tidy, y = df_gdp_tidy) 

df_gdp_edu%>%
    select(country_shortcode, Long.Name, gdp) %>%
    arrange(gdp) %>%
    filter(order(gdp) == 13)
```

    ##   country_shortcode           Long.Name gdp
    ## 1               KNA St. Kitts and Nevis 767

``` r
merge(x = df_education_tidy, y = df_gdp_tidy) %>%nrow()
```

    ## [1] 189

## Question 4

``` r
unique(df_gdp_edu$Income.Group)
```

    ## [1] "High income: nonOECD" "Low income"           "Lower middle income" 
    ## [4] "Upper middle income"  "High income: OECD"

``` r
df_gdp_edu %>% group_by(Income.Group) %>% 
    summarise(AVG = mean(as.numeric(ranking)))
```

    ## # A tibble: 5 x 2
    ##   Income.Group           AVG
    ##   <chr>                <dbl>
    ## 1 High income: nonOECD  91.9
    ## 2 High income: OECD     33.0
    ## 3 Low income           134. 
    ## 4 Lower middle income  108. 
    ## 5 Upper middle income   92.1

## Question 5

``` r
# Creating the groups limits.
quantile(x = as.numeric(df_gdp_edu$ranking), c(0.0, 0.2, 0.4, 0.6, 0.8, 1.0))
```

    ##    0%   20%   40%   60%   80%  100% 
    ##   1.0  38.6  76.2 113.8 152.4 190.0

``` r
# Adding to the merged dataframe a new column,
df_gdp_edu$ranking_group <- cut(x = df_gdp_edu$ranking, breaks = quantile(x = as.numeric(df_gdp_edu$ranking), c(0.0, 0.2, 0.4, 0.6, 0.8, 1.0)))

# 
df_gdp_edu %>% select(country_shortcode, Long.Name,gdp,ranking_group) %>% head()
```

    ##   country_shortcode                    Long.Name    gdp ranking_group
    ## 1               ABW                        Aruba   2584     (152,190]
    ## 2               AFG Islamic State of Afghanistan  20497    (76.2,114]
    ## 3               AGO  People's Republic of Angola 114147   (38.6,76.2]
    ## 4               ALB          Republic of Albania  12648     (114,152]
    ## 5               ARE         United Arab Emirates 348595      (1,38.6]
    ## 6               ARG           Argentine Republic 475502      (1,38.6]

``` r
df_gdp_edu %>%
    group_by(ranking_group) %>%
    filter(Income.Group == "Lower middle income") %>%
    summarise(n = n())
```

    ## # A tibble: 5 x 2
    ##   ranking_group     n
    ##   <fct>         <int>
    ## 1 (1,38.6]          5
    ## 2 (38.6,76.2]      13
    ## 3 (76.2,114]       11
    ## 4 (114,152]         9
    ## 5 (152,190]        16
