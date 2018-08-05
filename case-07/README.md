# REDCap Project Test Case 07

## TEST-CASE-07: Longitudinal, Single center, Form, Single Arm

A simple longitudinal database is formed for the Sitka Spruce Growth data in 
_Analysis of Longitudinal Data_ by Diggle, Heagerty, Liang, and Zeger. The 
features of this data base are

* Longitudinal design
* A single center
* Two forms
* A single arm

This database defines thirteen measurement events and uses a dropdown menu and
a radio buttons control to define groups.

### Files

#### Standard Files

* `test-case-07-data-dictionary.csv`
* `test-case-07-meta-data-api.csv`
* `test-case-07-project-information.csv`
* `test-case-07-README.md`
* `test-case-07-records.csv`
* `test-case-07-records-api.csv`
* `test-case-07-records-api-eav.csv`

#### Additional Files

No additional files.

### Data Generation

```{r, eval = FALSE}
library(dplyr)
library(magrittr)

Tree <-
  read.table("http://www.biostat.jhsph.edu/~fdominic/teaching/LDA/sitka.data",
             header = TRUE)

Tree <- 
  Tree %>% 
  mutate(date = as.Date("1988-01-01") + days) %>% 
  group_by(tree) %>% 
  arrange(date) %>% 
  mutate(measurement = row_number()) %>% 
  arrange(tree, date) %>% 
  mutate(redcap_event_name = sprintf("measurement_%s_arm_1", measurement))  %>% 
  mutate(ozone = ifelse(grepl("measurement_1_arm_1", redcap_event_name),
                        yes = ozone, 
                        no = NA),
         chamber = ifelse(grepl("measurement_1_arm_1", redcap_event_name),
                          yes = chamber, 
                          no = NA)) %>% 
  select(tree_id = tree, redcap_event_name, 
         chamber, ozone, date, 
         log_size = logsize)
```  
