Cyclistic
================
Diego
2023-10-16

<div style="text-align: center;">

# <span style="color:#0495a4;">Cyclistic Bike Share Case Study</span>

## <span style="color:#0495a4;">R programming</span>

<img src="cyclistic_bike_share.png"/>

</div>

### <span style="color:#0495a4">Table of Contents</span>

- [1. Introduction](#introduction)
  - [1.1 Company Summary](#companysummary)
- [2. Ask](#ask)
  - [2.1 Business Task](#businesstask)
  - [2.2 Stakeholders](#stakeholders)
- [3. Prepare](#prepare)
  - [3.1 Data Used](#dataused)
  - [3.2 Data Check](#datacheck)
  - [3.3 Data Summary](#datasummary)
  - [3.4 Data Limitations & Integrity](#datalimitationsandintegrity)
- [4. Process](#process)
  - [4.1 Tool Choice](#toolchoice)
  - [4.2 Data Cleaning](#datacleaning)
- [5. Analyze](#analyze)
  - [5.1 Data Manipulation](#datamanipulation)
  - [5.2 Data Trends](#datatrends)
- [6. Share](#share)
  - [6.1 Data visualization](#datavisualization)
- [7. Act](#act)
  - [7.1 Conclusion & Recommendation](#conclusionandrecommendation)

## <span style="color:#0495a4">1. Introduction</span>

This analysis is part of a Capstone Project for the Google Data
Analytics Certificate program (Cyclistic). It will use the software
RStudio and R programming language to complete the project, and for
sharing the results, this notebook markdown, and a Slide presentation
will be created.

The project will be completed by using the 6 Data Analytics stages:

- **Ask:** Identify the business task and determine the key
  stakeholders.
- **Prepare:** Collect the data, identify how it’s organized, determine
  the credibility of the data.
- **Process:** Select the tool for data cleaning, check for errors and
  document the cleaning process.
- **Analyze:** Organize and format the data, aggregate the data so that
  it’s useful, perform calculations and identify trends and
  relationships.
- **Share:** Use design thinking principles and data-driven storytelling
  approach, present the findings with effective visualization. Ensure
  the analysis has answered the business task.
- **Act:** Share the final conclusion and the recommendations.

#### <span style="color:#0495a4">1.1 Company Summary</span>

Cyclistic, a bike-share program in Chicago, started in 2016 and has
since grown to operate a fleet of 5,824 bikes across 692 geotracked
stations. Cyclistic offers flexible pricing plans, including single-ride
passes, full-day passes, and annual memberships. The annual members have
been found to be more profitable than casual riders, and the company
aims to increase the number of annual members.

To achieve this goal, Cyclistic’s marketing team, led by Moreno, plans
to convert casual riders into annual members. Moreno believes that
casual riders, who are already aware of Cyclistic, can be persuaded to
become members. The team intends to analyze historical bike trip data to
understand the differences between annual members and casual riders, why
casual riders might choose a membership, and how digital media can be
used to enhance their marketing strategies. This data-driven approach
will help Cyclistic develop effective marketing strategies for achieving
their goal.

## <span style="color:#0495a4">2. Ask</span>

- <span style="color: gray;">Guiding questions</span>

  - **What is the problem you are trying to solve?**
  - **How can your insights drive business decisions?**

- <span style="color: gray;">Key tasks</span>

  - **Identify the business task**
  - **Consider key stakeholders**

- <span style="color: gray;">Deliverable</span>

  - **A clear statement of the business task**

#### <span style="color:#0495a4">2.1 Business Task</span>

**How do annual members and casual riders use Cyclistic bikes
differently?**

By completing the business task Cyclistic marketing team will be able to
achieve it’s business goal of design marketing strategies aimed at
converting casual riders into annual members.

#### <span style="color:#0495a4">2.2 Stakeholders</span>

- Cyclistic: A bike-share program that features more than 5,800 bicycles
  and 600 docking stations. Cyclistic sets itself apart by also offering
  reclining bikes, hand tricycles, and cargo bikes, making bike-share
  more inclusive to people with disabilities and riders who can’t use a
  standard two-wheeled bike. The majority of riders opt for traditional
  bikes; about 8% of riders use the assistive options. Cyclistic users
  are more likely to ride for leisure, but about 30% use them to commute
  to work each day.
- Lily Moreno: The director of marketing. Moreno is responsible for the
  development of campaigns and initiatives to promote the bike-share
  program. These may include email, social media, and other channels.
- Cyclistic marketing analytics team: A team of data analysts who are
  responsible for collecting, analyzing, and reporting data that helps
  guide Cyclistic marketing strategy.
- Cyclistic executive team: The notoriously detail-oriented executive
  team will decide whether to approve the recommended marketing program.

## <span style="color:#0495a4">3. Prepare</span>

- <span style="color: gray;">Guiding questions</span>

  - **Where is your data located?**
  - **How is the data organized?**
  - **Are there issues with bias or credibility in this data? Does your
    data ROCCC(reliable, original, comprehensive, current and cited)?**
  - **How are you addressing licensing, privacy, security, and
    accessibility?**
  - **How did you verify the data’s integrity?**
  - **How does it help you answer your question?**
  - **Are there any problems with the data?**

- <span style="color: gray;">Key tasks</span>

  - **Download data and store it appropriately.**
  - **Identify how it’s organized.**
  - **Sort and filter the data.**
  - **Determine the credibility of the data.**

- <span style="color: gray;">Deliverable</span>

  - **A description of all data sources used**

#### <span style="color:#0495a4">3.1 Data Used</span>

The data used for this project is located at this [Data
Source](https://divvy-tripdata.s3.amazonaws.com/index.html) and has been
made available by Motivate International Inc. under this
[License](https://divvybikes.com/data-license-agreement). There are
various compressed files in .zip format, with variations based on the
year of the information.

For this analysis it will be used the past 12 months of data files from
08/2022 to 07/2023. Below is the list of downloaded files.

- **202208-divvy-tripdata.zip**
- **202209-divvy-tripdata.zip**
- **202210-divvy-tripdata.zip**
- **202211-divvy-tripdata.zip**
- **202212-divvy-tripdata.zip**
- **202301-divvy-tripdata.zip**
- **202302-divvy-tripdata.zip**
- **202303-divvy-tripdata.zip**
- **202304-divvy-tripdata.zip**
- **202305-divvy-tripdata.zip**
- **202306-divvy-tripdata.zip**
- **202307-divvy-tripdata.zip**

The extracted files are in .csv (comma-separated values) format,
organized by month, starting from August 2022 and ending in July 2023,
totaling 12 CSV files. To check these files, the R programming language
will be used.

``` r
# Install the 'tidyverse' package, a collection of R packages for data manipulation and visualization.
install.packages("tidyverse", repos = "https://cran.rstudio.com/")
```

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/vl/1wy31mz11vgfjtq8g4t2slzc0000gn/T//RtmpxfyvIe/downloaded_packages

``` r
# Install the 'data.table' package, a high-performance data manipulation package.
install.packages("data.table", repos = "https://cran.rstudio.com/")
```

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/vl/1wy31mz11vgfjtq8g4t2slzc0000gn/T//RtmpxfyvIe/downloaded_packages

``` r
# Install the 'osmdata' package for working with OpenStreetMap data.
install.packages("osmdata", repos = "https://cran.rstudio.com/")
```

    ## 
    ## The downloaded binary packages are in
    ##  /var/folders/vl/1wy31mz11vgfjtq8g4t2slzc0000gn/T//RtmpxfyvIe/downloaded_packages

``` r
# Load packages into R environment.
library("tidyverse")
```

    ## ── Attaching core tidyverse packages ──────────────────────── tidyverse 2.0.0 ──
    ## ✔ dplyr     1.1.3     ✔ readr     2.1.4
    ## ✔ forcats   1.0.0     ✔ stringr   1.5.0
    ## ✔ ggplot2   3.4.3     ✔ tibble    3.2.1
    ## ✔ lubridate 1.9.2     ✔ tidyr     1.3.0
    ## ✔ purrr     1.0.2     
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()
    ## ℹ Use the conflicted package (<http://conflicted.r-lib.org/>) to force all conflicts to become errors

``` r
library("data.table")
```

    ## 
    ## Attaching package: 'data.table'
    ## 
    ## The following objects are masked from 'package:lubridate':
    ## 
    ##     hour, isoweek, mday, minute, month, quarter, second, wday, week,
    ##     yday, year
    ## 
    ## The following objects are masked from 'package:dplyr':
    ## 
    ##     between, first, last
    ## 
    ## The following object is masked from 'package:purrr':
    ## 
    ##     transpose

``` r
library("osmdata")
```

    ## Data (c) OpenStreetMap contributors, ODbL 1.0. https://www.openstreetmap.org/copyright

``` r
# Load additional packages for data manipulation and analysis.
library("dplyr")
library("lubridate")
library("janitor")
```

    ## 
    ## Attaching package: 'janitor'
    ## 
    ## The following objects are masked from 'package:stats':
    ## 
    ##     chisq.test, fisher.test

``` r
# Load 'ggplot2' for data visualization.
library("ggplot2")

# Load 'ggmap' for integrating Google Maps with R.
library("ggmap")
```

    ## The legacy packages maptools, rgdal, and rgeos, underpinning the sp package,
    ## which was just loaded, were retired in October 2023.
    ## Please refer to R-spatial evolution reports for details, especially
    ## https://r-spatial.org/r/2023/05/15/evolution4.html.
    ## It may be desirable to make the sf package available;
    ## package maintainers should consider adding sf to Suggests:.
    ## ℹ Google's Terms of Service: <https://mapsplatform.google.com>
    ## ℹ Please cite ggmap if you use it! Use `citation("ggmap")` for details.

``` r
# Create data frames from each CSV file.
df_202208 <- fread("202208-divvy-tripdata.csv")
df_202209 <- fread("202209-divvy-publictripdata.csv")
df_202210 <- fread("202210-divvy-tripdata.csv")
df_202211 <- fread("202211-divvy-tripdata.csv")
df_202212 <- fread("202212-divvy-tripdata.csv")
df_202301 <- fread("202301-divvy-tripdata.csv")
df_202302 <- fread("202302-divvy-tripdata.csv")
df_202303 <- fread("202303-divvy-tripdata.csv")
df_202304 <- fread("202304-divvy-tripdata.csv")
df_202305 <- fread("202305-divvy-tripdata.csv")
df_202306 <- fread("202306-divvy-tripdata.csv")
df_202307 <- fread("202307-divvy-tripdata.csv")
```

#### <span style="color:#0495a4">3.2 Data Check</span>

To gain an initial understanding of the data, use the str() function,
which provides a concise summary. Subsequently, the goal is to
consolidate all the data frames into a single unified data frame. To
achieve this, it is imperative that all data frames share identical
column names and data types.

Once the data has been merged into one comprehensive data frame, the
next crucial step is to identify duplicates, NA (Not Available), NaN
(Not-A-Number), and empty values.

``` r
str(df_202307)
```

    ## Classes 'data.table' and 'data.frame':   767650 obs. of  13 variables:
    ##  $ ride_id           : chr  "9340B064F0AEE130" "D1460EE3CE0D8AF8" "DF41BE31B895A25E" "9624A293749EF703" ...
    ##  $ rideable_type     : chr  "electric_bike" "classic_bike" "classic_bike" "electric_bike" ...
    ##  $ started_at        : POSIXct, format: "2023-07-23 20:06:14" "2023-07-23 17:05:07" ...
    ##  $ ended_at          : POSIXct, format: "2023-07-23 20:22:44" "2023-07-23 17:18:37" ...
    ##  $ start_station_name: chr  "Kedzie Ave & 110th St" "Western Ave & Walton St" "Western Ave & Walton St" "Racine Ave & Randolph St" ...
    ##  $ start_station_id  : chr  "20204" "KA1504000103" "KA1504000103" "13155" ...
    ##  $ end_station_name  : chr  "Public Rack - Racine Ave & 109th Pl" "Milwaukee Ave & Grand Ave" "Damen Ave & Pierce Ave" "Clinton St & Madison St" ...
    ##  $ end_station_id    : chr  "877" "13033" "TA1305000041" "TA1305000032" ...
    ##  $ start_lat         : num  41.7 41.9 41.9 41.9 42 ...
    ##  $ start_lng         : num  -87.7 -87.7 -87.7 -87.7 -87.7 ...
    ##  $ end_lat           : num  41.7 41.9 41.9 41.9 42 ...
    ##  $ end_lng           : num  -87.7 -87.6 -87.7 -87.6 -87.6 ...
    ##  $ member_casual     : chr  "member" "member" "member" "member" ...
    ##  - attr(*, ".internal.selfref")=<externalptr>

``` r
# Create a list of data frames.
list_of_dfs <- list(
  df_202208, df_202209, df_202210, df_202211, df_202212, df_202301, df_202302,
  df_202303, df_202304, df_202305, df_202306, df_202307
)

# Compare data frames columns and return "TRUE" if they can be bound together 
# or "FALSE" along with a list indicating where the columns are different.
compare_df_cols_same(list_of_dfs)
```

    ## [1] TRUE

``` r
# Joining all data frames in one.
data <- rbindlist(list_of_dfs)

# Check for NA values.
colSums(is.na(data))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##                  0                  0                  0                  0 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0               6102               6102 
    ##      member_casual 
    ##                  0

``` r
# Check for NAN values.
colSums(sapply(data, is.nan))
```

    ##            ride_id      rideable_type         started_at           ended_at 
    ##                  0                  0                  0                  0 
    ## start_station_name   start_station_id   end_station_name     end_station_id 
    ##                  0                  0                  0                  0 
    ##          start_lat          start_lng            end_lat            end_lng 
    ##                  0                  0                  0                  0 
    ##      member_casual 
    ##                  0

``` r
# Check for empty values in the data, exclude columns "started_at" and "ended_at".
# It will be possible to check for empty values in these columns further.
colSums(data[, !c("started_at", "ended_at")] == "")
```

    ##            ride_id      rideable_type start_station_name   start_station_id 
    ##                  0                  0             868772             868904 
    ##   end_station_name     end_station_id          start_lat          start_lng 
    ##             925008             925149                  0                  0 
    ##            end_lat            end_lng      member_casual 
    ##                 NA                 NA                  0

``` r
# Check for duplicates in the only possible column that must not have it.
sum(duplicated(data$ride_id))
```

    ## [1] 0

#### <span style="color:#0495a4">3.3 Data Summary</span>

``` r
summary(data)
```

    ##    ride_id          rideable_type        started_at                    
    ##  Length:5723606     Length:5723606     Min.   :2022-08-01 00:00:00.00  
    ##  Class :character   Class :character   1st Qu.:2022-09-28 13:56:43.50  
    ##  Mode  :character   Mode  :character   Median :2023-02-16 13:53:51.50  
    ##                                        Mean   :2023-02-01 23:55:22.17  
    ##                                        3rd Qu.:2023-06-03 07:41:37.00  
    ##                                        Max.   :2023-07-31 23:59:56.00  
    ##                                                                        
    ##     ended_at                      start_station_name start_station_id  
    ##  Min.   :2022-08-01 00:05:00.00   Length:5723606     Length:5723606    
    ##  1st Qu.:2022-09-28 14:12:20.25   Class :character   Class :character  
    ##  Median :2023-02-16 14:04:56.50   Mode  :character   Mode  :character  
    ##  Mean   :2023-02-02 00:13:43.58                                        
    ##  3rd Qu.:2023-06-03 08:00:15.00                                        
    ##  Max.   :2023-08-12 04:53:41.00                                        
    ##                                                                        
    ##  end_station_name   end_station_id       start_lat       start_lng     
    ##  Length:5723606     Length:5723606     Min.   :41.64   Min.   :-87.92  
    ##  Class :character   Class :character   1st Qu.:41.88   1st Qu.:-87.66  
    ##  Mode  :character   Mode  :character   Median :41.90   Median :-87.64  
    ##                                        Mean   :41.90   Mean   :-87.65  
    ##                                        3rd Qu.:41.93   3rd Qu.:-87.63  
    ##                                        Max.   :42.07   Max.   :-87.52  
    ##                                                                        
    ##     end_lat         end_lng       member_casual     
    ##  Min.   : 0.00   Min.   :-88.16   Length:5723606    
    ##  1st Qu.:41.88   1st Qu.:-87.66   Class :character  
    ##  Median :41.90   Median :-87.64   Mode  :character  
    ##  Mean   :41.90   Mean   :-87.65                     
    ##  3rd Qu.:41.93   3rd Qu.:-87.63                     
    ##  Max.   :42.18   Max.   :  0.00                     
    ##  NA's   :6102    NA's   :6102

- From the last step “Data Check”:

  - NA values: Columns “end_lat” and “end_lng” missing values showed
    above indicate an error.

  - NAN values: None.

  - Empty cells: Columns “start_station_name”, “start_station_id”,
    “end_station_name” and “end_station_id” can affect data integrity.

  - Duplicates: None.

There is no metadata available, however, it is possible to identify its
content by the name of the columns. Using the summary() and the str()
function used before, it shows that there are over 4 million rows and 13
columns with the following names:

- **ride_id** \#Ride id - unique
- **rideable_type** \#Bike type - Classic, Docked, Electric
- **started_at** \#Ride start day and time
- **ended_at** \#Ride end day and time
- **start_station_name** \#Ride start station name
- **start_station_id** \#Ride start station id
- **end_station_name** \#Ride end station name
- **end_station_id** \#Ride end station id
- **start_lat** \#Ride start latitude
- **start_lng** \#Ride start longitute
- **end_lat** \#Ride end latitude
- **end_lng** \#Ride end longitute
- **member_casual** \#Rider type - Member or Casual

#### <span style="color:#0495a4">3.4 Data Limitations & Integrity</span>

1.  There is enough data to compare casual riders and members, a
    complete year, 12 months.
2.  While the data source contains historical data dating back to 2013,
    this analysis assumes that previous habits are unlikely to return
    after the COVID-19 pandemic. Additionally, the older files lack the
    same information, and any potentially valuable data is only
    available for members.
3.  Missing values and errors will be deleted before analysis.

## <span style="color:#0495a4">4. Process</span>

- <span style="color: gray;">Guiding questions</span>

  - **What tools are you choosing and why?**
  - **Have you ensured your data’s integrity?**
  - **What steps have you taken to ensure that your data is clean?**
  - **How can you verify that your data is clean and ready to analyze?**
  - **Have you documented your cleaning process so you can review and
    share those results?**

- <span style="color: gray;">Key tasks</span>

  - **Check the data for errors.**
  - **Choose your tools.**
  - **Transform the data so you can work with it effectively.**
  - **Document the cleaning process.**

- <span style="color: gray;">Deliverable</span>

  - **Documentation of any cleaning or manipulation of data**

#### <span style="color:#0495a4">4.1 Tool Choice</span>

The data will be processed, analyzed and visualized using the R
programming language.

#### <span style="color:#0495a4">4.2 Data Cleaning</span>

First, it is necessary to remove missing values, and errors in latitude
and longitude. Next, additional columns will be created for further
analysis. Finally, the data set will be cleaned and prepared for
analysis.

``` r
# Remove NA and empty values.
data <- na.omit(data)
data <- data %>% filter(if_all(starts_with("start_station_name"):ends_with("end_lng"), ~ . != ""))

# Get the bounding box coordinates for Chicago.
chicago_bb <- getbb("Chicago")

# Filter the data frame to include only rows within the Chicago bounding box.
data <- data %>%
  filter(
    start_lat >= chicago_bb[[2]] &
    start_lat <= chicago_bb[[4]] &
    start_lng >= chicago_bb[[1]] &
    start_lng <= chicago_bb[[3]] &
    end_lat >= chicago_bb[[2]] &
    end_lat <= chicago_bb[[4]] &
    end_lng >= chicago_bb[[1]] &
    end_lng <= chicago_bb[[3]]
  )

# Create useful variables for further analysis.
data <- data %>%
  mutate(
    date = as.Date(started_at),
    day_of_week = weekdays(date),
    month = months(date),
    ride_time_secs = as.numeric(difftime(ended_at, started_at, units = "secs")),
    period = case_when(
      hour(started_at) >= 5 & hour(started_at) < 11 ~ 'Morning',
      hour(started_at) >= 11 & hour(started_at) < 14 ~ 'Lunch',
      hour(started_at) >= 14 & hour(started_at) < 18 ~ 'Afternoon',
      hour(started_at) >= 18 & hour(started_at) < 22 ~ 'Evening',
      hour(started_at) >= 22 | hour(started_at) < 5 ~ 'Night'),
    season = case_when(
      month(date) %in% c(12, 1, 2) ~ 'Winter',
      month(date) %in% c(3, 4, 5) ~ 'Spring',
      month(date) %in% c(6, 7, 8) ~ 'Summer',
      month(date) %in% c(9, 10, 11) ~ 'Autumn')
  )

# Data Check
summary(data)
```

    ##    ride_id          rideable_type        started_at                    
    ##  Length:4308997     Length:4308997     Min.   :2022-08-01 00:00:07.00  
    ##  Class :character   Class :character   1st Qu.:2022-09-27 16:09:17.00  
    ##  Mode  :character   Mode  :character   Median :2023-02-15 08:14:46.00  
    ##                                        Mean   :2023-02-01 08:12:32.14  
    ##                                        3rd Qu.:2023-06-02 12:49:26.00  
    ##                                        Max.   :2023-07-31 23:59:15.00  
    ##     ended_at                      start_station_name start_station_id  
    ##  Min.   :2022-08-01 00:05:44.00   Length:4308997     Length:4308997    
    ##  1st Qu.:2022-09-27 16:21:35.00   Class :character   Class :character  
    ##  Median :2023-02-15 08:24:13.00   Mode  :character   Mode  :character  
    ##  Mean   :2023-02-01 08:28:24.11                                        
    ##  3rd Qu.:2023-06-02 13:08:02.00                                        
    ##  Max.   :2023-08-01 20:40:50.00                                        
    ##  end_station_name   end_station_id       start_lat       start_lng     
    ##  Length:4308997     Length:4308997     Min.   :41.65   Min.   :-87.84  
    ##  Class :character   Class :character   1st Qu.:41.88   1st Qu.:-87.66  
    ##  Mode  :character   Mode  :character   Median :41.90   Median :-87.64  
    ##                                        Mean   :41.90   Mean   :-87.64  
    ##                                        3rd Qu.:41.93   3rd Qu.:-87.63  
    ##                                        Max.   :42.02   Max.   :-87.53  
    ##     end_lat         end_lng       member_casual           date           
    ##  Min.   :41.65   Min.   :-87.84   Length:4308997     Min.   :2022-08-01  
    ##  1st Qu.:41.88   1st Qu.:-87.66   Class :character   1st Qu.:2022-09-27  
    ##  Median :41.90   Median :-87.64   Mode  :character   Median :2023-02-15  
    ##  Mean   :41.90   Mean   :-87.64                      Mean   :2023-01-31  
    ##  3rd Qu.:41.93   3rd Qu.:-87.63                      3rd Qu.:2023-06-02  
    ##  Max.   :42.02   Max.   :-87.53                      Max.   :2023-07-31  
    ##  day_of_week           month           ride_time_secs      period         
    ##  Length:4308997     Length:4308997     Min.   :-10122   Length:4308997    
    ##  Class :character   Class :character   1st Qu.:   340   Class :character  
    ##  Mode  :character   Mode  :character   Median :   593   Mode  :character  
    ##                                        Mean   :   952                     
    ##                                        3rd Qu.:  1056                     
    ##                                        Max.   :728178                     
    ##     season         
    ##  Length:4308997    
    ##  Class :character  
    ##  Mode  :character  
    ##                    
    ##                    
    ## 

Based on the summary provided, there appear to be anomalies in the
‘ride_time_secs’ column. The minimum value should be greater than zero;
any negative or “0” value is not a valid ride. While there is an
exceptionally high maximum value, it may have occurred when the user
returned the bike on a different day.

``` r
# Clean bad data.
data <- data %>% filter(ride_time_secs > 0)

# Create a clean data frame ready for analysis.
data_v2 <- data %>% select(-c(started_at, ended_at, start_station_id, end_station_id))

# Export the new data frame as a CSV file.
write.csv(data_v2, file = "cyclistic_202208_202307.csv")
```

- **Data Cleaning & Manipulation Process:**

  - **Deletions:**

    - Rows with NA values in the “end_lat” and “end_lng” columns. These
      rides may be considered errors; as a hypothesis, the bikes might
      have been taken for maintenance.
    - Rows with empty cells will be deleted to guarantee data integrity.
    - Rows with latitudes and longitudes outside of Chicago.
    - Rows with ride_time_secs \<= 0. These represent invalid rides with
      negative or zero values.
    - Columns “started_at”, “ended_at”, “start_station_id”,
      “end_station_id”. These columns will no longer be necessary.

  - **Additions:**

    - Date, Day of Week and Month Calculation:

      - date: Calculated by extracting the complete date from the
        started_at column.

      - day_of_week: Calculated by extracting the weekday from date
        column (e.g., “Monday”).

      - month: Calculated by extracting the month from date column
        (e.g., “January”).

    - Ride Time:

      - ride_time_secs: Calculated as the numeric difference in seconds
        between ‘ended_at’ and ‘started_at’.

    - Period Classification:

      - period: This column is determined based on the time of day in
        the started_at column. Rides are categorized into different
        periods, including “Morning,” “Lunch,” “Afternoon,” “Evening,”
        and “Night,” based on the time of day.
        - Morning: from 5 to 11
        - Lunch: from 11 to 14
        - Afternoon: from 14 to 18
        - Evening: from 18 to 22
        - Night: from 22 to 5

    - Season Classification:

      - season: This column categorizes rides into different seasons
        based on the month in the “started_at” column. The following
        seasons are used:
        - Winter: Rides occurring in December, January, or February.
        - Spring: Rides occurring in March, April, or May.
        - Summer: Rides occurring in June, July, or August.
        - Autumn: Rides occurring in September, October, or November.

  - **Creation:**

    - New clean and ready for analysis data frame “data_v2”.
    - Exported CSV file “cyclistic_202208_202307.csv” from “data_V2”.

## <span style="color:#0495a4">5. Analyze</span>

- <span style="color: gray;">Guiding questions</span>

  - **How should you organize your data to perform analysis on it?**
  - **Has your data been properly formatted?**
  - **What surprises did you discover in the data?**
  - **What trends or relationships did you find in the data?**
  - **How will these insights help answer your business questions?**

- <span style="color: gray;">Key tasks</span>

  - **Aggregate your data so it’s useful and accessible.**
  - **Organize and format your data.**
  - **Perform calculations.**
  - **Identify trends and relationships.**

- <span style="color: gray;">Deliverable</span>

  - **A summary of your analysis**

#### <span style="color:#0495a4">5.1 Data Manipulation</span>

In the initial step of the analysis, a descriptive examination is
performed for the two distinct rider types: casual and member.

The following statistical formulas and metrics are employed to describe
the data frame:

- **Count (N):** The count formula is used to determine the total number
  of observations within each rider type group.

- **Minimum (Min):** By employing the minimum formula, the analysis
  identifies the smallest observed value for a particular variable.

- **Maximum (Max):** The maximum formula is utilized to find the largest
  observed value, providing insights into the upper boundaries of a
  particular variable.

- **Mean (Average):** The mean formula calculates the average value of
  the variable within each group. It offers an estimation of the central
  tendency or typical value for the variable in each group.

- **Median (Midpoint):** The median formula computes the middle value
  when data is sorted. It serves as a measure of central tendency that
  is less influenced by extreme values, representing the “typical” value
  for the variable in each group.

- **Standard Deviation (SD):** The standard deviation formula quantifies
  the dispersion of the variable within each group. A smaller standard
  deviation implies that data points are closer to the mean, whereas a
  larger standard deviation suggests greater variability.

``` r
summary_total <- 
  data_v2 %>%
  group_by(member_casual) %>%
  summarise(
    count = n(),                   
    min = hms::as_hms(min(ride_time_secs)),
    max = hms::as_hms(max(ride_time_secs)), 
    mean = hms::as_hms(mean(ride_time_secs)),   
    median = hms::as_hms(median(ride_time_secs)),
    sd = hms::as_hms(sd(ride_time_secs))        
  )

summary_total
```

    ## # A tibble: 2 × 7
    ##   member_casual   count min    max       mean          median sd           
    ##   <chr>           <int> <time> <time>    <time>        <time> <time>       
    ## 1 casual        1595997 00'01" 202:16:18 22'21.184391" 12'43" 47'50.006052"
    ## 2 member        2712633 00'01"  24:57:52 12'03.147822" 08'37" 20'08.588970"

The ride time average is influenced by outliers, as indicated by the
maximum values and significant standard deviation. Therefore, in
analyses where the data is affected by extreme values, it is advisable
to use the median instead of the mean.

``` r
summary_period <- data_v2 %>%
  mutate(period = factor(period, levels = c("Morning", "Lunch", "Afternoon", "Evening", "Night"))) %>%
  group_by(member_casual, period) %>%
  summarise(
    count = n(), 
    median = hms::as_hms(median(ride_time_secs)))
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
summary_period %>% pivot_wider(names_from = member_casual, values_from = c(count, median))
```

    ## # A tibble: 5 × 5
    ##   period    count_casual count_member median_casual median_member
    ##   <fct>            <int>        <int> <time>        <time>       
    ## 1 Morning         245626       673591 10'11"        08'04"       
    ## 2 Lunch           294646       421903 15'10"        08'12"       
    ## 3 Afternoon       536353       869526 14'00"        09'06"       
    ## 4 Evening         363253       588053 12'13"        08'59"       
    ## 5 Night           156119       159560 10'43"        08'28"

Among the various periods of bike usage, the noticeable difference
between users is in the ‘Morning’ period, which is predominantly active
among members while not even top 3 for casual users. In terms of median
ride durations, the ‘Lunch’ period boasts the longest rides for casual
riders, while members have a more uniform length of rides across
different periods. These statistics suggest that casual users may have a
more tourist/leisure-oriented usage pattern, while members appear to
have a usage pattern that aligns more with daily work routines. To
confirm this pattern, it is essential to observe this behavior during
different days, months, and seasons to gain a comprehensive
understanding.

``` r
summary_weekday <- data_v2 %>%
  mutate(day_of_week = factor(day_of_week, levels = c("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"))) %>%
  group_by(member_casual, day_of_week) %>%
  summarise(
    count = n(), 
    median = hms::as_hms(median(ride_time_secs)))
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
summary_weekday %>% pivot_wider(names_from = member_casual, values_from = c(count, median))
```

    ## # A tibble: 7 × 5
    ##   day_of_week count_casual count_member median_casual median_member
    ##   <fct>              <int>        <int> <time>        <time>       
    ## 1 Monday            190106       390508 12'09"        08'13"       
    ## 2 Tuesday           186853       429304 11'21"        08'22"       
    ## 3 Wednesday         191358       436341 11'01"        08'26"       
    ## 4 Thursday          210591       436569 11'19"        08'30"       
    ## 5 Friday            242379       388869 12'35"        08'32"       
    ## 6 Saturday          325803       340758 14'55"        09'33"       
    ## 7 Sunday            248907       290284 14'43"        09'17"

``` r
summary_monthly <- data_v2 %>%
  mutate(month = factor(month, levels = c("January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"))) %>%
  group_by(member_casual, month) %>%
  summarise(
    count = n(), 
    median = hms::as_hms(median(ride_time_secs)))
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
summary_monthly %>% pivot_wider(names_from = member_casual, values_from = c(count, median))
```

    ## # A tibble: 12 × 5
    ##    month     count_casual count_member median_casual median_member
    ##    <fct>            <int>        <int> <time>        <time>       
    ##  1 January          29240       117796 08'14"        07'05.0"     
    ##  2 February         32338       115968 09'16"        07'12.5"     
    ##  3 March            46228       152641 09'13"        07'16.0"     
    ##  4 April           109179       212020 12'16"        08'09.0"     
    ##  5 May             175523       284336 13'57"        09'04.0"     
    ##  6 June            218389       313158 13'47"        09'25.0"     
    ##  7 July            243672       326883 14'21"        09'36.0"     
    ##  8 August          268189       333125 13'44"        09'39.0"     
    ##  9 September       219084       311913 12'50"        09'10.0"     
    ## 10 October         150028       260782 11'44"        08'16.0"     
    ## 11 November         72847       180749 09'59"        07'44.0"     
    ## 12 December         31280       103262 08'38"        07'21.0"

``` r
summary_season <- data_v2 %>%
  mutate(season = factor(season, levels = c("Winter", "Spring", "Summer", "Autumn"))) %>%
  group_by(member_casual, season) %>%
  summarise(
    count = n(), 
    median = hms::as_hms(median(ride_time_secs)))
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
summary_season %>% pivot_wider(names_from = member_casual, values_from = c(count, median))
```

    ## # A tibble: 4 × 5
    ##   season count_casual count_member median_casual median_member
    ##   <fct>         <int>        <int> <time>        <time>       
    ## 1 Winter        92858       337026 08'42"        07'13"       
    ## 2 Spring       330930       648997 12'36"        08'18"       
    ## 3 Summer       730250       973166 13'57"        09'34"       
    ## 4 Autumn       441959       753444 11'56"        08'29"

It is now necessary to understand how users utilize each type of
available ride differently.

``` r
summary_ride_type <- data_v2 %>%
  mutate(rideable_type = factor(rideable_type, levels = c("classic_bike", "electric_bike", "docked_bike"))) %>%
  group_by(member_casual, rideable_type) %>%
  summarise(
    count = n(), 
    median = hms::as_hms(median(ride_time_secs))) %>%
  mutate(rideable_type = recode(rideable_type, "classic_bike" = "Classic", "electric_bike" = "Electric", "docked_bike" = "Docked"))
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
summary_ride_type %>% pivot_wider(names_from = member_casual, values_from = c(count, median))
```

    ## # A tibble: 3 × 5
    ##   rideable_type count_casual count_member median_casual median_member
    ##   <fct>                <int>        <int> <time>        <time>       
    ## 1 Classic             782927      1680623 14'00"        09'03"       
    ## 2 Electric            688107      1032010 10'16"        08'02"       
    ## 3 Docked              124963           NA 26'47"           NA

In the table provided above, a comprehensive summary of ride types,
including ‘Classic,’ ‘Electric,’ and ‘Docked,’ is presented. The data
reveals that riders exhibit a preference for ‘Classic’ and ‘Electric’
types, with ‘Classic’ being the most favored option among them. Notably,
‘Docked’ types are only used by casual riders and appear to be less
frequently utilized, however, they have the longest duration of usage.

Finally, which stations are most used by users.

``` r
top10station_casual <- data_v2 %>%
  filter(member_casual == "casual") %>%
  count(start_station_name) %>%
  arrange(desc(n)) %>%
  head(10)
  
top10station_casual
```

    ##                     start_station_name     n
    ##  1:            Streeter Dr & Grand Ave 47048
    ##  2:  DuSable Lake Shore Dr & Monroe St 28465
    ##  3:              Michigan Ave & Oak St 21493
    ##  4:                    Millennium Park 20902
    ##  5: DuSable Lake Shore Dr & North Blvd 19342
    ##  6:                     Shedd Aquarium 17791
    ##  7:                Theater on the Lake 15421
    ##  8:                     Dusable Harbor 13004
    ##  9:              Wells St & Concord Ln 12666
    ## 10:         Indiana Ave & Roosevelt Rd 11482

``` r
top10station_member <- data_v2 %>%
  filter(member_casual == "member") %>%
  count(start_station_name) %>%
  arrange(desc(n)) %>%
  head(10)
  
top10station_member
```

    ##               start_station_name     n
    ##  1:     Kingsbury St & Kinzie St 23417
    ##  2:            Clark St & Elm St 22140
    ##  3: Clinton St & Washington Blvd 21573
    ##  4:        Wells St & Concord Ln 19418
    ##  5:     Loomis St & Lexington St 19389
    ##  6:     University Ave & 57th St 18595
    ##  7:          Ellis Ave & 60th St 18222
    ##  8:      Clinton St & Madison St 17892
    ##  9:            Wells St & Elm St 17640
    ## 10:          Canal St & Adams St 16647

The top 10 stations by users shows that they use different stations.
Casual riders, in particular, utilize the station at Streeter Dr & Grand
Ave nearly twice as often as the second most-used station by them.

#### <span style="color:#0495a4">5.2 Data Trends</span>

- Ride Frequency:

  - Members tend to have a higher frequency of rides compared to casual
    riders.

- Ride Duration:

  - Casual riders generally have longer ride durations than members.

- Usage Patterns by Time of Day:

  - The noticeable difference between users is in the ‘Morning’ period,
    which is predominantly active among members while not even top 3 for
    casual users. Median ride durations for casual riders are longest
    during the ‘Lunch’ period, while members exhibit more consistent
    ride durations across different time periods.

- Weekday vs. Weekend Usage:

  - Casual riders have a higher ride frequency on weekends, while
    members ride more frequently on weekdays. Interestingly, both casual
    riders and members have longer ride durations on weekends, which
    suggests that weekends might be a preferred time for more leisure
    bike trips for both groups.

- Seasonal Trends:

  - Summer and autumn are the most popular seasons for bike rides, with
    casual riders having a significantly higher number of rides in the
    summer compared to other seasons. This could indicate that casual
    riders are more inclined to use bikes during vacation seasons.

- Ride Types:

  - ‘Classic’ and ‘Electric’ ride types are favored by riders, with
    ‘Classic’ being the most popular choice. ‘Docked’ ride types are
    only used by casual riders and have the longest ride durations. In
    contrast, members mainly opt for ‘Classic’ rides, which tend to have
    shorter durations. This suggests that members may prefer shorter,
    more efficient rides for their daily routines, while casual riders
    may use ‘Docked’ bikes for longer, leisurely trips.

- Top 10 Stations:

  - It’s worth noting that the top 10 stations used by members and
    casual riders are different, indicating distinct preferences or
    usage patterns for station selection among these two groups.

## <span style="color:#0495a4">6. Share</span>

- <span style="color: gray;">Guiding questions</span>

  - **Were you able to answer the question of how annual members and
    casual riders use Cyclistic bikes differently?**
  - **What story does your data tell?**
  - **How do your findings relate to your original question?**
  - **Who is your audience? What is the best way to communicate with
    them?**
  - **Can data visualization help you share your findings?**
  - **Is your presentation accessible to your audience?**

- <span style="color: gray;">Key tasks</span>

  - **Determine the best way to share your findings.**
  - **Create effective data visualizations.**
  - **Present your findings.**
  - **Ensure your work is accessible.**

- <span style="color: gray;">Deliverable</span>

  - **Supporting visualizations and key findings**

#### <span style="color:#0495a4">6.1 Data Visualization</span>

The analysis will be shared through R charts in this notebook, and a
[Slide](https://docs.google.com/presentation/d/16PGlooftPqG9YiZdCjrvKjSWGLFqJoU9JX-dlVo-BfM/present?rm=minimal)
presentation.

The first plot displays a daily breakdown of the number of rides per
user, illustrating that only a few days saw casual users utilize the
bike share system more frequently than members. Seasonal patterns reveal
distinct usage trends, with summer showing the highest activity for
members averaging just over 10,000 daily rides and casual users around
7,500 daily rides. During winter, member usage remains relatively
steady, slightly above 3,000 daily rides, while casual users decrease to
around 1,000 daily rides.

``` r
summary_date <- data_v2 %>%
  group_by(member_casual, date) %>%
  summarise(count = n())
```

    ## `summarise()` has grouped output by 'member_casual'. You can override using the
    ## `.groups` argument.

``` r
summer_period <- data.frame(
  start_date = as.Date(c("2022-08-01", "2023-06-01")),
  mid_date = as.Date(c("2022-08-15", "2023-07-01")),
  end_date = as.Date(c("2022-08-31", "2023-07-31"))
)

num_rides_day <- ggplot(summary_date) +
  geom_area(aes(x = date, y = count, fill = member_casual), position = "identity", alpha = 0.6) +
  geom_smooth(aes(x = date, y = count, color = member_casual), method = "loess", span = 0.1, se = FALSE, size = 1.2) +
  geom_rect(data = summer_period, aes(xmin = start_date, xmax = end_date, ymin = -Inf, ymax = Inf), alpha = 0.1) +
  geom_text(data = summer_period, aes(x = mid_date, y = 0, label = "Summer"), vjust = -1) +
  scale_fill_viridis_d() +
  scale_color_viridis_d() +
  labs(title = "Total Number of Rides per Day by User", x = NULL, y = NULL, fill = NULL, color = NULL, caption = "August 2022 - July 2023") +
  theme_minimal() +
  theme(plot.title = element_text(hjust = 0.5))
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

``` r
ggsave(filename = "num_rides_day.png", plot = num_rides_day)
```

    ## Saving 7 x 5 in image
    ## `geom_smooth()` using formula = 'y ~ x'

``` r
num_rides_day
```

    ## `geom_smooth()` using formula = 'y ~ x'

![](Cyclistic_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

Looking at the median duration of rides per month, casual riders exhibit
a higher value with significant variance during hot seasons, while
members maintain a steady usage pattern, similar to routine patterns.

``` r
dur_rides_month <- ggplot(summary_monthly) +
  geom_line(aes(x = month, y = median, color = member_casual, group = member_casual, linetype = member_casual), size = 1.5) +
  geom_rect(aes(xmin = "March", xmax = "November", ymin = -Inf, ymax = Inf), alpha = 0.01) +
  geom_text(x = "July", y = 0, label = "Duration of casual users peaks during 'hot' months", hjust = 0.5, vjust = -1) +
  geom_text(data = summary_monthly %>% filter(month == "January", member_casual == "casual"), aes(x = "January", y = median, label = median), hjust = 0.5, vjust = -2, nudge_x = 0.1) +
  geom_text(data = summary_monthly %>% filter(month == "July", member_casual == "casual"), aes(x = "July", y = median, label = median), hjust = 0.5, vjust = -2, nudge_x = 0.1) +
  scale_color_viridis_d() +
  labs(title = "Median Duration of Rides per Month by User", x = NULL, y = NULL, linetype = NULL, color = NULL, caption = "August 2022 - July 2023") +
  scale_linetype_manual(values = c("longdash", "solid")) +
  scale_y_time(limits = c(hms::as_hms(0), hms::as_hms(20*60))) +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1), plot.title = element_text(hjust = 0.5))

ggsave(filename = "dur_rides_month.png", plot = dur_rides_month)
```

    ## Saving 7 x 5 in image

``` r
dur_rides_month
```

![](Cyclistic_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

The number of rides per weekday demonstrates an inverse pattern between
users. Casual riders tend to use the service more frequently on
weekends, while members show higher usage during the week. This
difference indicates distinct usage patterns, possibly related to
tourist and work routines. The peak usage times also vary, with casual
riders favoring the afternoon and evening, while members predominantly
ride in the morning and afternoon.

``` r
summary_period_of_day <- data_v2 %>%
  mutate(day_of_week = factor(day_of_week, levels = c("Sunday", "Saturday", "Friday", "Thursday", "Wednesday", "Tuesday", "Monday"))) %>%
  mutate(period = factor(period, levels = c("Night", "Evening", "Afternoon", "Lunch", "Morning"))) %>%
  group_by(member_casual, day_of_week, period) %>%
  summarise(count = n())
```

    ## `summarise()` has grouped output by 'member_casual', 'day_of_week'. You can
    ## override using the `.groups` argument.

``` r
num_rides_weekday_period <- ggplot(summary_period_of_day) +
  geom_col(aes(x = day_of_week, y = count, fill = period), position = "stack") +
  scale_fill_viridis_d() +
  labs(title = "Total Number of Rides per Weekday and Period of Day by User", x = NULL, y = NULL, fill = NULL, caption = "August 2022 - July 2023") +
  theme_minimal() +
  theme(axis.text.x = element_text(angle = 45, hjust = 1), plot.title = element_text(hjust = 0.5)) +
  facet_wrap(~member_casual, labeller = labeller(member_casual = c("casual" = "Casual", "member" = "Member"))) +
  coord_flip()

ggsave(filename = "num_rides_weekday_period.png", plot = num_rides_weekday_period)
```

    ## Saving 7 x 5 in image

``` r
num_rides_weekday_period
```

![](Cyclistic_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->

There are three types of rides available: Classic, Electric, and Docked.
Docked rides are exclusively used by casual riders, accounting for only
8% of their choices. Classic rides are the preferred option for both
user groups, with members choosing Classic 62% of the time.

``` r
summary_ride_type <- summary_ride_type %>%
  mutate(percentage = count / sum(count)) %>%
  arrange(member_casual, percentage)

num_ridetype <- ggplot(summary_ride_type) +
  geom_bar(aes(x = "", y = percentage, fill = rideable_type), stat = "identity", color = "black") +
  geom_text(aes(x = 1.6, y = percentage, label = paste0(round(percentage*100), "%")), color = "black", position = position_stack(vjust = 0.5)) +
  coord_polar(theta = "y") +
  scale_fill_viridis_d() +
  labs(title = "Ride Type Distribution by User", fill = NULL, caption = "August 2022 - July 2023") +
  theme_void() +
  theme(plot.title = element_text(hjust = 0.5)) +
  facet_wrap(~ member_casual, labeller = labeller(member_casual = c("casual" = "Casual", "member" = "Member")))

ggsave(filename = "num_ridetype.png", plot = num_ridetype)
```

    ## Saving 7 x 5 in image

``` r
num_ridetype
```

![](Cyclistic_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

Concerning ride duration, classic rides are also favored over electric
rides by both user groups. However, docked rides are used for twice the
duration that casual riders spend on classic rides. While members
maintain a relatively consistent ride duration across seasons, casual
users have significantly shorter rides during winter.

``` r
summary_ride_type_season <- data_v2 %>% 
  mutate(rideable_type = factor(rideable_type, levels = c("classic_bike", "electric_bike", "docked_bike"))) %>%
  group_by(member_casual, season, rideable_type) %>%
  summarise(median = hms::as_hms(median(ride_time_secs))) %>%
  mutate(rideable_type = recode(rideable_type, "classic_bike" = "Classic", "electric_bike" = "Electric", "docked_bike" = "Docked"))
```

    ## `summarise()` has grouped output by 'member_casual', 'season'. You can override
    ## using the `.groups` argument.

``` r
dur_ride_type <- ggplot(summary_ride_type_season) +
  geom_col(aes(x = season, y = median, fill = rideable_type), position = "dodge") +
  geom_text(data = summary_ride_type_season %>% filter(rideable_type %in% c("Classic", "Docked"), member_casual == "casual"), aes(x = season, y = median, label = substr(median, 4, 8)), vjust = -0.5) +
  scale_fill_viridis_d() +
  scale_y_time(limits = c(hms::as_hms(0), hms::as_hms(30*60))) +
  labs(title = "Median Duration of Rides per Season and Ride Type by User", fill = NULL, x = NULL, y = NULL, caption = "August 2022 - July 2023") +
  theme_minimal() +
  theme(plot.title = element_text(hjust = 0.5)) +
  facet_wrap(~member_casual, labeller = labeller(member_casual = c("casual" = "Casual", "member" = "Member")))

ggsave(filename = "dur_ride_type.png", plot = dur_ride_type)
```

    ## Saving 7 x 5 in image

``` r
dur_ride_type
```

![](Cyclistic_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

Upon examining the top 10 stations where users commence their rides, it
becomes evident that a tourist pattern prevails among casual riders, as
they tend to favor stations situated closer to the coastline of Chicago.
Conversely, members exhibit a preference for inner-city stations,
aligning with a work-related behavior. Additionally, there is one
station (Streeter Dr & Grand Ave) that stands out with double the usage
compared to others among casual users, while members distribute their
usage more evenly across all stations.

``` r
top10station_casual_density <- top10station_casual %>% left_join(data_v2 %>% filter(member_casual == "casual"), by = "start_station_name")

top10station_member_density <- top10station_member %>% left_join(data_v2 %>% filter(member_casual == "member"), by = "start_station_name")

map <- get_stamenmap(bbox = c(
  min(top10station_member_density$start_lng),
  min(top10station_member_density$start_lat),
  max(top10station_member_density$start_lng),
  max(top10station_member_density$start_lat)
), maptype = "terrain")
```

    ## ℹ Map tiles by Stamen Design, under CC BY 3.0. Data by OpenStreetMap, under ODbL.

``` r
top10stations <- bind_rows(top10station_casual_density %>% distinct(start_station_name, .keep_all = TRUE), top10station_member_density %>% distinct(start_station_name, .keep_all = TRUE)) 

top_station_locations <- ggmap(map) +
  geom_point(data = top10stations, aes(x = start_lng, y = start_lat, color = member_casual, size = n), alpha = 0.8) +
  scale_size(range = c(.1, 20), name="Density") +
  scale_color_viridis_d() +
  labs(title = "Top 10 Start Stations Locations by User", color = "User Type", x = NULL, y = NULL, caption = "August 2022 - July 2023") +
  theme_minimal() +
  theme(plot.title = element_text(hjust = 0.5))

ggsave(filename = "top_station_locations.png", plot = top_station_locations)
```

    ## Saving 7 x 5 in image

``` r
top_station_locations
```

![](Cyclistic_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

## <span style="color:#0495a4">7. Act</span>

- <span style="color: gray;">Guiding questions</span>

  - **What is your final conclusion based on your analysis?**
  - **How could your team and business apply your insights?**
  - **What next steps would you or your stakeholders take based on your
    findings?**
  - **Is there additional data you could use to expand on your
    findings?**

- <span style="color: gray;">Key tasks</span>

  - **Create your portfolio.**
  - **Add your case study.**
  - **Practice presenting your case study to a friend or family
    member.**

- <span style="color: gray;">Deliverable</span>

  - **Your top three recommendations based on your analysis**

#### <span style="color:#0495a4">7.1 Conclusion & Recommendation</span>

In the analysis of the bike share company’s user behavior, significant
insights have emerged regarding casual users. These individuals tend to
exhibit leisure and tourist-oriented behaviors, utilizing the bike
system for extended durations, primarily during weekends and the hot
seasons, notably in the summer. Of particular importance, casual users
are the only users of docked bikes, even though this ride type
constitutes only 8% of their total rides, it delivers the longest
durations of rides, twice compared to other types. Additionally, casual
users display a preference for stations located near Chicago’s
picturesque coastline. Armed with these insights, it was developed a
tailored marketing campaign with three strategic recommendations to
convert these casual users into annual members.

    1. Seasonal Membership Promotions:
    -   Target casual users' preference for leisure and tourist behavior during the hot season, especially in summer. Create special seasonal promotions that make annual memberships more appealing during this time. For instance, Cyclistic could offer discounted annual memberships during the summer months, along with additional perks such as free helmets, guided tours, or access to exclusive events. Highlight the benefits of an annual membership, such as unlimited access and convenience, which can enhance their leisurely bike rides along the coastline.

    2. Docked Bike Experience Enhancement:
    -   Since casual users show a preference for docked bikes using this type longer than others, focus on improving their experience with this type. Highlight the longer ride durations and convenience of docked bikes compared to classic and electric ones. Consider launching marketing campaigns that educate casual users about the advantages of docked bikes, such as stability, comfort, and their suitability for leisurely rides. Offer special promotions or discounts for annual memberships, with a focus on the use of docked bikes, and create digital media content that showcases scenic routes along the coastline that are best enjoyed with docked bikes.

    3. Weekend Getaway Packages:
    -   Recognizing that casual users often ride on weekends, design packages that encourage them to become annual members. Develop special weekend getaway packages that include an annual membership, a list of popular weekend destinations along the coastline, and discounts at partner businesses (e.g., restaurants, ice cream shops, or museums). The social media marketing campaign should use the area range of preferred stations near the coastline and commence around lunchtime, because casual users increase their activity after morning period. The campaign's focal point should be effectively showcase the exceptional experiences offered by the annual membership through these weekend packages.
