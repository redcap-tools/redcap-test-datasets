# REDCap Project Test Case 20

## TEST-CASE-20: Cross-sectional, Single center, Form, Single Arm, Randomization Module

Unlike other test data sets, this data set was not designed to test general 
REDCap API usage.  It maintains a structure similar to that of Test Case 01, 
but utilizes the Randomization Module.  Use of randomization is required in 
order to test tools that assist with generating allocation tables.  The REDCap
structures used are:

* Cross sectional design
* A single center
* Forms (in this case, only one form)
* A single arm
* Randomization Module

The most notable feature of this database is that it contains one of each type 
of field supported by REDCap 6.5.0.  The intended function of this database was 
to test that the API methods written by the REDCap-Tools project are capable of
accessing and properly formatting each of the field types. It will also prove 
useful for testing the API import functionality.

### Files

#### Standard Files

* `test-case-20-data-dictionary.csv`
* `test-case-20-meta-data-api.csv`
* `test-case-20-project-information.csv`
* `test-case-20-README.md`

Since no actual records are required to assist with developing allocation 
tables, no records are provided for this test data set.

#### Additional Files

No additional files.

### Data Generation

No data generated.
