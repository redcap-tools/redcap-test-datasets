# redcap-test-datasets

Example datasets covering a range of scenarios to facilitate API tests.  (I'm still seeding, and need to add the other testing datasets used in [REDCapR](https://github.com/OuhscBbmc/REDCapR).) 

| Test Case | Design           | Centers | Forms/Survey | Arms    | Events | Special Traits |
|-----------|------------------|---------|--------------|---------|--------|----------------|
| 01        | Cross-Sectional  | Single  | Form         | N/A     | N/A    |                |
| 02        | Cross-Sectional  | Multi   | Form         | N/A     | N/A    |                |
| 03        | Cross-Sectional  | Single  | Survey       | N/A     | N/A    |                |
| 04        | Cross-Sectional  | Multi   | Survey       | N/A     | N/A    |                |
| 05        | Cross-Sectional  | Single  | Hybrid       | N/A     | N/A    |                |
| 06        | Cross-Sectional  | Multi   | Hybrid       | N/A     | N/A    |                |
| 07        | Longitudinal     | Single  | Form         | Single  |        |                |
| 08        | Longitudinal     | Multi   | Form         | Single  |        |                |
| 09        | Longitudinal     | Single  | Survey       | Single  |        |                |
| 10        | Longitudinal     | Multi   | Survey       | Single  |        |                |
| 11        | Longitudinal     | Single  | Hybrid       | Single  |        |                |
| 12        | Longitudinal     | Multi   | Hybrid       | Single  |        |                |
| 13        | Longitudinal     | Single  | Form         | Multi   |        |                |
| 14        | Longitudinal     | Multi   | Form         | Multi   |        |                |
| 15        | Longitudinal     | Single  | Survey       | Multi   |        |                |
| 16        | Longitudinal     | Multi   | Survey       | Multi   |        |                |
| 17        | Longitudinal     | Single  | Hybrid       | Multi   |        |                |
| 18        | Longitudinal     | Multi   | Hybrid       | Multi   |        |                |
| 19        | Cross-Sectional  | Single  | Form         | N/A     | N/A    | PHI Fields     |
| 20        | Cross-Sectional  | Single  | Form         | N/A     | N/A    | Randomization  |


## Test Case Files
Each test case, when completed, provides the files necessary to duplicate the project in 
your version of REDCap and compare results from API calls with the results returned by 
exporting data through the API.

Test case files are prefixed by `test-case-##` and each test case has the following files

* `test-case-##-data-dictionary.csv`: The data dictionary as downloaded from the REDCap User Interface
* `test-case-##-meta-data-api.csv`: The data dictionary as downloaded through the REDCap API
* `test-case-##-project-information.csv`: The project information as downloaded through the REDCap API
* `test-case-##-README.md`: A file with explanatory notes specific to the test case
* `test-case-##-records.csv`: The records file as downloaded from the REDCap User Interface
* `test-case-##-records-api.csv`: The records file as downloaded through the REDCap API
* `test-case-##-records-api-eav.csv`: The records file as download through the REDCap API with `type=eav`

For longitudinal test cases, the files also include

* `test-case-##-arms.csv`: The table of study arms as downloaded through the REDCap API
* `test-case-##-events.csv`: The table of events as downloaded through the REDCap API
* `test-case-##-form-event-mappings.csv`: The form event mappings as downloaded through the REDCap API

Some test cases may also include files that are used in testing the file upload and signature draw fields.  
These files have the format `test-case-##-record-#-[field_name]-[file_name].[ext]` and are not necessary
to duplicate the structure of the project.  They are provided solely for convenience and consistency 
of testing.  These files are documented in each test case's README.
