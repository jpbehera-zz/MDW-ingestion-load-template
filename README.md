# MDW-ingestion-load-template
ADF pipeline template to perform data ingestion, data transformation using Azure Databricks and loading of data into Azure Synapse Analytics using polybase

## Pipeline 1
### Lookup Activity
  ** We are leveraging lookup activity in ADF pipeline to list all the tables in Database A from source A
### Foreach Loop
  ** Using Foreach loop we are looping through all the tables that we gathered in the previous activity and running a copy command to land the data in the landing zone in ADLS Gen 2


## Pipeline 2

### Lookup Activity
 ** We are leveraging lookup activity in ADF pipeline to list all the tables in Database B from source B
### Foreach Loop
 ** Using Foreach loop we are looping through all the tables that we gathered in the previous activity and running a copy command to land the data in the landing zone in ADLS Gen 2
### Databricks Notebook
 ** Using Azure Databricks Notebook Activity we are reading data from ADLS Gen 2 (using Service principal) from all the five different files stored in separate partitions
 ** Using this activity, we are moving data from Landing zone  Raw zone  Curated zone
 ** We are using SparkSQL to perform the transformation
 ** Output of the transformation job is storing data in the curated zone in ADLS Gen 2
 ** We are storing the data in Curated zone in a partitioned structure
### Copy Data
 ** Once the data is stored in ADLS Gen 2, we are leveraging polybase to load data into Azure Synapse Analytics (DWH)

