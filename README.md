# Azure_Databricks-ETL_process
Fully automated ETL process for deployment in Azure Cloud


<br />Azure services: <br />
* Databricks, <br />
* Data Lake Storage Gen2, <br />
* DataFactory, <br />
* Delta Tables.<br />
  
  
<br />Tech:<br />
* Python, <br />
* Apache Spark <- PySpark.<br />
  
  
<br />Notebooks info:<br />
* Entire ETL process is configured by '.json' file containing extracted columns properties (how to read them and create star-shaped schema of database in warehouse).<br />
* Notebook 'buildDataLakeStructure' is manually evaluated - its purpose is to create DataLake structure, create template-model of star-shaped schema and generate some test files for tests and presentation of ETL process.<br />
* Notebook 'transform' is triggered by DataFactory's Pipeline, when a new file appears in 1. level layer (raw/bronze). Success of 'transform' creates cleaned file in 2. level (cleansed/silver).<br />
* Notebook 'load' is triggered by the success of 'transform' process. It takes the file from 2. level (cleansed/silver) and loads data to 3. level (curated/golden layer) updating the star-shaped model (facts and dimensions tables).<br />
* Notebook 'dashboard' contains a simple dashboard using Delta Tables.
