HAR-analysis
================
by Maurício Collaça
on 2017-01-27

HAR data set analysis
---------------------

The purpose of this project is to collect, tidy, filter, average and produce a new tidy data set from the HAR data set according to the requirements of the [Getting and Cleaning Data Course](https://www.coursera.org/learn/data-cleaning/home) of the [Data Science Specialization](https://www.coursera.org/specializations/jhu-data-science) from [John Hopkins University](https://www.jhu.edu/).

These requirements are:

> 1.  Merges the training and the test sets to create one data set.
> 2.  Extracts only the measurements on the mean and standard deviation for each measurement.
> 3.  Uses descriptive activity names to name the activities in the data set
> 4.  Appropriately labels the data set with descriptive variable names.
> 5.  From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

The data set used in this project is from the University of California Irvine (UCI) Machine Learning Repository: Human Activity Recognition Using Smartphones Data Set Version 1.0. The data set represents data collected from 30 subjects performing activities of daily living (ADL) while carrying a waist-mounted Samsung Galaxy S smartphone with embedded accelerometer and gyroscope inertial sensors. The original documentation is available [here](http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphones).

The data set for this project is available at [Cloudfront](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip) and [UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00240/UCI%20HAR%20Dataset.zip).

HAR-analysis repository
-----------------------

The [HAR-analysis](https://github.com/mauriciocramos/HAR-analysis) repository includes the following files:

-   [README.md](https://github.com/mauriciocramos/HAR-analysis/blob/master/README.md) - This README file.

-   [run\_analysis.R](https://github.com/mauriciocramos/HAR-analysis/blob/master/run_analysis.R) - R script to perform the data downloading, tidying, filtering and averaging required by the project.

-   [CodeBook.md](https://github.com/mauriciocramos/HAR-analysis/blob/master/CodeBook.md) - Code book that describes all the variables and summaries calculated, along with units, any transformations and work performed to clean up, tidy, process and display of the data and any other relevant information.

-   [HAR-utils.R](https://github.com/mauriciocramos/HAR-analysis/blob/master/HAR-utils.R) - R script containing file reading helper functions developed to encapsulate code and improve the reusability and the readability of the [run\_analysis.R](https://github.com/mauriciocramos/HAR-analysis/blob/master/run_analysis.R). It's not necessary to read the `HAR-utils.R` source code in order to understand the `run_analysis.R`. The `run_analysis.R` script automatically loads the `HAR-utils.R` script.

-   [averages.txt](https://github.com/mauriciocramos/HAR-analysis/blob/master/averages.txt) - A tidy data set output from `run_analysis.R`, containing the the average of each mean and standard deviation variable for each activity and each subject.

Installation, running and evaluation instructions
-------------------------------------------------

These are the installation, running and evaluation instructions for the project. Please read and follow them carefully to ensure you have everything running properly and after that, read the [CodeBook.md](https://github.com/mauriciocramos/HAR-analysis/blob/master/CodeBook.md) for deeper explanations and final evaluation.

1.  If you still haven't done it, install R available at [The R Foundation](https://www.r-project.org/). This project used R version 3.3.2 (2016-10-31).
2.  Optionally, you may use RStudio Desktop as well, available at [RStudio](https://www.rstudio.com/). This project used RStudio Desktop version 1.0.136.
3.  If you still haven't done it, install additional R packages `{dplyr}` and `{tidyr}`. The easiest way to do that is via R (menu Packages &gt; Install Package(s)...) or RStudio (menu Tools &gt; Install packages...). This project used `{dplyr}` version 0.5.0 and `{tidr}` version 0.6.1.
4.  Download both [run\_analysis.R](https://raw.githubusercontent.com/mauriciocramos/HAR-analysis/master/run_analysis.R) and [HAR-utils.R](https://raw.githubusercontent.com/mauriciocramos/HAR-analysis/master/HAR-utils.R) in some local working directory.
5.  Open `R` or `RStudio`
6.  Go to the directory where the scripts were download, for instance, `setwd("your-directory-here")`
7.  Run the command: `source("run_analysis.R")`. At this point the script will download and uncompress `Dataset.zip` for your convenience, start the data processing and display the results. If you experience unexpected problems during this automated download you may do it manually by downloading the `Dataset.zip` from [Cloudfront](https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip) or [UCI](http://archive.ics.uci.edu/ml/machine-learning-databases/00240/UCI%20HAR%20Dataset.zip) into your local working directory, then restart the script that will take care from the uncompressing point on.
8.  The script will display a series of messages and summary results for each project requirement in the R/Rstudio Console, guiding you for your evaluation:

``` r
source("run_analysis.R")
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

    ## Plese wait.  Reading files...

    ## ...done

    ## 1. Merges the training and the test sets to create one data set.

    ## 'data.frame':    5777739 obs. of  4 variables:
    ##  $ subject : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ activity: int  5 5 5 5 5 5 5 5 5 5 ...
    ##  $ feature : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ value   : num  0.289 0.278 0.28 0.279 0.277 ...

    ## 2. Extracts only the measurements on the mean and standard deviation for each measurement.

    ## 'data.frame':    813621 obs. of  4 variables:
    ##  $ subject : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ activity: int  5 5 5 5 5 5 5 5 5 5 ...
    ##  $ feature : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ value   : num  0.289 0.278 0.28 0.279 0.277 ...

    ## 3. Uses descriptive activity names to name the activities in the data set

    ## 'data.frame':    813621 obs. of  4 variables:
    ##  $ subject : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ activity: chr  "STANDING" "STANDING" "STANDING" "STANDING" ...
    ##  $ feature : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ value   : num  0.289 0.278 0.28 0.279 0.277 ...

    ## 4. Appropriately labels the data set with descriptive variable names.

    ## 'data.frame':    813621 obs. of  4 variables:
    ##  $ subject : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ activity: chr  "STANDING" "STANDING" "STANDING" "STANDING" ...
    ##  $ feature : chr  "tBodyAcc-mean()-X" "tBodyAcc-mean()-X" "tBodyAcc-mean()-X" "tBodyAcc-mean()-X" ...
    ##  $ value   : num  0.289 0.278 0.28 0.279 0.277 ...

    ## 5. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject.

    ## 'data.frame':    14220 obs. of  4 variables:
    ##  $ subject : int  1 1 1 1 1 1 1 1 1 1 ...
    ##  $ activity: chr  "LAYING" "LAYING" "LAYING" "LAYING" ...
    ##  $ feature : chr  "fBodyAcc-mean()-X" "fBodyAcc-mean()-Y" "fBodyAcc-mean()-Z" "fBodyAcc-meanFreq()-X" ...
    ##  $ average : num  -0.9391 -0.8671 -0.8827 -0.1588 0.0975 ...

1.  The final output data set file `averages.txt` is summarized in the Console, saved in you local working directory and also opened in detail in window `View()` for your convenience by the script itself. You may check it out again by either looking into your local working directory or issuing the R command `View(read.table("averages.txt", header = TRUE, stringsAsFactors = FALSE))` to view it in an R/RStudio window.

I hope you enjoy it!

Acknowledgment
--------------

Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz. A Public Domain Dataset for Human Activity Recognition Using Smartphones. 21th European Symposium on Artificial Neural Networks, Computational Intelligence and Machine Learning, ESANN 2013. Bruges, Belgium 24-26 April 2013.
