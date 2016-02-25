# REDCap Project Test Case 01

## TEST-CASE-01: Cross-sectional, Single center, Form, Single Arm

This data set was created to serve as the basis for testing REDCap API usage.  The
structure of the database is as simple as REDCap will allow.  Specifically, it utilizes

* Cross sectional design
* A single center
* Forms (in this case, only one form)
* A single arm

The most notable feature of this database is that it contains one of each type of 
field supported by REDCap 6.5.0.  The intended function of this database was to test that 
the API methods written by the REDCap-Tools project are capable of accessing and 
properly formatting each of the field types. It will also prove useful for testing the 
API import functionality.

### Files

#### Standard Files

* `test-case-01-data-dictionary.csv`
* `test-case-01-meta-data-api.csv`
* `test-case-01-project-information.csv`
* `test-case-01-README.md`
* `test-case-01-records.csv`
* `test-case-01-records-api.csv`
* `test-case-01-records-api-eav.csv`

#### Additional Files

* `test-case-01-record-1-file_upload-redcaplogo.jpg`: The REDCap logo.  It was originally
  placed in the `file_upload` field in record 1 to allow testing of the API functions 
  with file upload fields.
* `test-case-01-record-1-signature_draw-2016-02-25-0116.png`: A sample signature from 
  a signature draw field in record 1.  It was placed in the project to allow testing of
  the API functions using signature draw fields.


### Data Generation

Data for this data base are randomly generated in R using the code below.

```
library(magrittr)
library(lubridate)

random_dates <- function(n = 100, 
                         start_date = as.numeric(as.Date("2000-01-01")), 
                         end_date = as.numeric(as.Date("2019-12-31")))
{
  runif(n, start_date, end_date) %>%
    as.Date(origin = origin)
}

random_datetimes <- function(n = 100,
                             start_datetime = as.numeric(as.POSIXct("2000-01-01")),
                             end_datetime = as.numeric(as.POSIXct("2019-12-31")),
                             format = "%Y-%m-%d %H:%M")
{
  runif(n, start_date, end_date) %>%
    as.POSIXct(origin = origin) %>%
    format(format = format)
}

set.seed(13423)

SampleData <- 
  data.frame(record_id = 1:100,
             unvalidated_text = vapply(1:100,
                                       function(x) paste0(sample(LETTERS, 15), collapse = ""),
                                       character(1)),
             date_dmy = random_dates(),
             date_mdy = random_dates(),
             date_ymd = random_dates(),
             datetime_dmyhm = random_datetimes(),
             datetime_mdyhm = random_datetimes(),
             datetime_ymdhm = random_datetimes(),
             datetime_dmyhms = random_datetimes(format = "%Y-%m-%d %H:%M:%S"),
             datetime_mdyhms = random_datetimes(format = "%Y-%m-%d %H:%M:%S"),
             datetime_ymdhms = random_datetimes(format = "%Y-%m-%d %H:%M:%S"),
             email = rep("email@domain.net", 100),
             integer = sample(1:100, 100),
             number = runif(100, 0, 100),
             phone = rep("888-555-1234", 100),
             time = random_datetimes(format = "%H:%M"),
             zip = rep("40041", 100),
             notes = vapply(1:100,
                            function(x) paste0(sample(c(LETTERS, " "), 250, replace = TRUE), collapse = ""),
                            character(1)),
             dropdown_numeric = sample(1:3, 100, replace = TRUE),
             dropdown_character = sample(letters[1:3], 100, replace = TRUE),
             dropdown_mixed = sample(c("a_1", "b_2", "c_3"), 100, replace = TRUE),
             radio_buttons = sample(1:3, 100, replace = TRUE),
             checkbox___1 = sample(0:1, 100, replace = TRUE),
             checkbox___2 = sample(0:1, 100, replace = TRUE),
             checkbox___3 = sample(0:1, 100, replace = TRUE),
             yes_no = sample(0:1, 100, replace = TRUE),
             true_false = sample(0:1, 100, replace = TRUE),
             slider = floor(runif(100, 0, 100)),
             
             stringsAsFactors = FALSE
  )
```