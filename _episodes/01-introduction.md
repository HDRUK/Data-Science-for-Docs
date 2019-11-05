---
# Please do not edit this file directly; it is auto generated.
# Instead, please edit 01-introduction.md in _episodes_rmd/
source: Rmd
title: "Introduction into R"
teaching: 30
exercises: 0
questions:
- "Basics of the R language."
objectives:
- "Be able to create variables"
- "Join variables into a vector"
- "Join vectors into a tibble"
- "Perform basic tibble manipulation"
keypoints:
- "Data is structured and can be broken down into basic building blocks"
editor_options: 
  chunk_output_type: console
---

## Content

- [Preliminaries](#preliminaries)
- [Introducing the data](#introducing-the-data)
- [Files and directories](#files-and-directories)


## Preliminaries

- A working internet connection (please use the wifi)
- [Install Slack](https://slack.com/intl/en-gb/) or use the web interface
- Introduce youselves on Slack
- Check you can login to the R-Studio Server. Details on:
  - The slides
  - Here
  - In Slack
- Pair programming: buddy up
- Live coding

### Introducing the data

We would like to introduce the data that we will be using during the course. The Critical Care Health Informatics Collaborative (CC-HIC) is a UK research body that has aggregated data from thousands of critical care patients. We will be using an anonymised sample from this cohort.

The data has been pre-prepared for us today, and will be presented as two "spread sheets" or what is called a `data frame` in `R` parlance. This is the most common format for presenting data that can be described in rows and columns (so called "rectangular data").

The data given contains information in a  *1 row per patient*, and *1 column per variable*.

For a full description of the data that exists inside CC-HIC see [here](https://github.com/ropensci/cleanEHR/wiki/Data-set-1.0)

You are also encourage to bring along your own data. We can't promise to spend time on this, but there are exercises to do along the way, and you might want to try these exercises out on your own work after the course. We will be around for the day, so feel free to approach us at any time and ask us for advice for your own data.

### Files and directories

It is going to be helpful to have an understanding of how files and folders (commonly called "directories") are named on your computer because unlike your usual habit of pointing and clicking to open something, we will need to start writing things down.

- Files have a "name", and (most of the time) an "extension". They follow the `[name].[extension]` pattern. `R` scripts, use the `.R` extension:
  - my_manuscript.docx
  - video.avi
  - my_script.R
- Files are stored in directories (folders)
- Directories can also contain other directories, creating an organised tree for you to store your files.
- The "root" directory is the start of this tree.
  - On Windows the root is the highest directory level, and often takes the letter `C`. This is representated as the `C:\` drive (note the *back slash*)
  - On Mac and Linux, the root is similarly the highest directory level, and simply represented by `/` (a *forward slash*). We are using linux today, so this is the convention we will follow.
- The "path" is a set of instructions to find a file on the computer.
  - Anologus to writing a postal address in reverse:
    - Germany (most generic)
    - Berlin
    - CityCube (most specific)
  - The "path" is just the same:
    - / (check inside the root)
    - Documents/ (check for the documents folder)
    - my_script.R (check for this file)
- You can write paths in two ways:
  - The *absolute* path. A full address, starting at the root, and describing how to get from root, to the file of interest.
    -  `/Users/edward/documents/my_script.R`
  - The *relative* path. A partial address, starting at your "current location" and descibing how to get from the current location, to the file of interest.
    - Assuming I am already at `/Users/edward/`
      - `documents/my_script.R`
    - If I need to go up a level, for example to find a file in Steve's user folder, I can use `..` the "two dots". This just means "go up one folder".
      - `../steve/documents/steves_script.R`
- You can always find your current location by typing `pwd` in the console (which means "print working directory") or by typing `getwd()` in `R`.

While you get used to the notion of typing the location of files on the computer, you can use a little shortcut to help out. The `file.choose()` function will allow you to pick a file on your computer, and it will tell you the full location. For now, use the function to navigate to the course data and pick out the `demographic-data.csv` file.


```r
library(tidyverse)
```

```
## ── Attaching packages ────────────────────────────────── tidyverse 1.2.1 ──
```

```
## ✔ ggplot2 3.2.1     ✔ purrr   0.3.2
## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
## ✔ tidyr   1.0.0     ✔ stringr 1.4.0
## ✔ readr   1.3.1     ✔ forcats 0.4.0
```

```
## ── Conflicts ───────────────────────────────────── tidyverse_conflicts() ──
## ✖ dplyr::filter() masks stats::filter()
## ✖ dplyr::lag()    masks stats::lag()
```

```r
my_file <- read_csv("./data/synthetic_data_clean.csv")
```

```
## Parsed with column specification:
## cols(
##   .default = col_double(),
##   creatinine = col_character(),
##   arrival_dttm = col_datetime(format = ""),
##   discharge_dttm = col_datetime(format = ""),
##   dob = col_date(format = ""),
##   vital_status = col_character(),
##   sex = col_character(),
##   id = col_character()
## )
```

```
## See spec(...) for full column specifications.
```

now we can call the `my_file` object back and see that it contains the address to the file.


```r
View(my_file)
```

And this is what it should look like:


```
## Error in loadNamespace(name): there is no package called 'webshot'
```

Don't worry if this doesn't all make sense at this time. It only means that you are paying attension! All will become clear over the course of the day.