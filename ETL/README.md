# ETL Data Analytics and Reporting

## Why do we need ETL ?
- Organization face problems like gathering data from multiple resources and data formats
- move data to one or more data stores
- Destinations and souce data store using diffeent formats
- Need to clean and shape data before laoding into destination

## What is ETL?
- ETL stands for Extract, Transform, Load
- Extract : the data from business systems , 
- Transform : apply business rules to transform data like fitering, aggregation, sorting, joining, cleaning, validating
- LOad : LOad into storage to aanlyse ( DataWarehouse, DataLake, DataVault)
- It is used for business intelligence & Analytics by making the proces  more reliable, accurate, detailed and efficient.
- Example : CRM system (curtomer data) + sales ssytem ( sales data) ===> Analyse customer that buy reguraly
- IN modern ETL all three E, T , L processes are run in parallel to save time

## What is data extraction?
In data extraction, extract, transform, and load (ETL) tools extract or copy raw data from multiple sources and store it in a staging area. A staging area (or landing zone) is an intermediate storage area for temporarily storing extracted data. Data staging areas are often transient, meaning their contents are erased after data extraction is complete. However, the staging area might also retain a data archive for troubleshooting purposes.

How frequently the system sends data from the data source to the target data store depends on the underlying change data capture mechanism. Data extraction commonly happens in one of the three following ways.

- Update notification
In update notification, the source system notifies you when a data record changes. You can then run the extraction process for that change. Most databases and web applications provide update mechanisms to support this data integration method.

- Incremental extraction
Some data sources can't provide update notifications but can identify and extract data that has been modified over a given time period. In this case, the system checks for changes at periodic intervals, such as once a week, once a month, or at the end of a campaign. You only need to extract data that has changed.

- Full extraction
Some systems can't identify data changes or give notifications, so reloading all data is the only option. This extraction method requires you to keep a copy of the last extract to check which records are new. Because this approach involves high data transfer volumes, we recommend you use it only for small tables.

## What is data transformation?
In data transformation, extract, transform, and load (ETL) tools transform and consolidate the raw data in the staging area to prepare it for the target data warehouse. The data transformation phase can involve the following types of data changes.

### Basic data transformation
Basic transformations improve data quality by removing errors, emptying data fields, or simplifying data. Examples of these transformations follow.

- Data cleansing
Data cleansing removes errors and maps source data to the target data format. For example, you can map empty data fields to the number 0, map the data value “Parent” to “P,” or map “Child” to “C.”

- Data deduplication
Deduplication in data cleansing identifies and removes duplicate records.

- Data format revision
Format revision converts data, such as character sets, measurement units, and date/time values, into a consistent format. For example, a food company might have different recipe databases with ingredients measured in kilograms and pounds. ETL will convert everything to pounds.

### Advanced data transformation
Advanced transformations use business rules to optimize the data for easier analysis. Examples of these transformations follow.

- Derivation
Derivation applies business rules to your data to calculate new values from existing values. For example, you can convert revenue to profit by subtracting expenses or calculating the total cost of a purchase by multiplying the price of each item by the number of items ordered.

- Joining
In data preparation, joining links the same data from different data sources. For example, you can find the total purchase cost of one item by adding the purchase value from different vendors and storing only the final total in the target system.

- Splitting
You can divide a column or data attribute into multiple columns in the target system. For example, if the data source saves the customer name as “Jane John Doe,” you can split it into a first, middle, and last name.

- Summarization
Summarization improves data quality by reducing a large number of data values into a smaller dataset. For example, customer order invoice values can have many different small amounts. You can summarize the data by adding them up over a given period to build a customer lifetime value (CLV) metric.

- Encryption
You can protect sensitive data to comply with data laws or data privacy by adding encryption before the data streams to the target database.

## What is data loading?
In data loading, extract transform, and load (ETL) tools move the transformed data from the staging area into the target data warehouse. For most organizations that use ETL, the process is automated, well defined, continual, and batch driven. Two methods for loading data follow.

- Full load
In full load, the entire data from the source is transformed and moved to the data warehouse. The full load usually takes place the first time you load data from a source system into the data warehouse.

- Incremental load 
In incremental load, the ETL tool loads the delta (or difference) between target and source systems at regular intervals. It stores the last extract date so that only records added after this date are loaded. There are two ways to implement incremental load.

- Streaming incremental load
If you have small data volumes, you can stream continual changes over data pipelines to the target data warehouse. When the speed of data increases to millions of events per second, you can use event stream processing to monitor and process the data streams to make more-timely decisions.

- Batch incremental load
If you have large data volumes, you can collect load data changes into batches periodically. During this set period of time, no actions can happen to either the source or target system as data is synchronized.

## ETL Vs ELT ?
Difference in when the transformation on data is done

#### Extract tranform LOad(ETL) 
- All three processes run on different engines operated separately

<img src="https://learn.microsoft.com/en-us/azure/architecture/data-guide/images/etl.png" alt="ETL" height="200" />

#### Extract LOad Transform (ELT)
- Target data store are used to transform data instead of having a different transformation engine as in ETL
Scaling the target datastaore also scales the ELT pipeline performance 
- ELT only works well when the target system is powerful enough to transform the data efficiently
- Data store reads directly from the scalable storage, instead of loading the data into its own proprietary storage. This approach skips the data copy step present in ETL, which often can be a time consuming operation for large data sets.

<img src="https://learn.microsoft.com/en-us/azure/architecture/data-guide/images/elt.png" alt="ELT" height="200" />

## ETL Tools ?
- Local ETL Tools :
  SQL or Power Query
    - Select
    - Insert
- Profesional ETL Tools :
   - Microsoft Azure Data Factory
   - Microsoft Azure Synapse pipeline
   - SQL Server integeration Services (SSIS)
   - Oracle Data Integerator
   - IBM DataStage

## ETL gives Historical context:
- ETL can be used to gather deep historical insights from an organizations data
- Enterprice can combine legacy data with data from new platform and applications , they can see older dataset alongside more recnt information to deduce patterns and insights.

## ETL provides consolidated view of data :
- helps in in-depth analysis and reporting
- ETL help data integeration by combining databases and various data into a single , unified view easy to coordinate
- This improves data quality and saves time to move and categorize data
- Helps easily anlyze, viasualize and amke sense of large datasets

## ETL provides Accurate data analysis:
- it gives accurate data that meets compliance and standards
- ETL can be used with data quality tools to clean and audit data ensuring data is trustworthy.

## ETL provides task automation:
- Data processing tasks can be automated for efficient analysis
- helps automate data migration process , and can be setup to integearte data peridicaly or even at runtime
- Helpful for data engineers to focus on innovation than data formatting and moving.

## Evolution of ETL :
- It originated with emergence of relational-databases and ETL tools attempted to convert transactional data formats to relational data formats for analysis

#### TRADIONAl ETL 
  earlier raw data was stored in transactional dbs that suported R/W but not helpful in analytics ( example for an e-commerce site it was stored as a row in spreadsheet with item, customer details, order deatils etc. in one transaction)
  Over the years the tarnsactional db got flooded with duplicate entries and it beacme near to impossible to analyse most popular product, or repeating customer etc.
    
  To overcome this ETL tools automatically converted this transactional data to relational data and stored them in form of interconnected tables 
  Analysts then used queries to identify relationship among tables and deduced paterns and trends using the data
    
#### Modern ETL:
  Data sinks can recieve & store data from multiple sources and have underlysing hardware that can scale over time.
  ETL tools today have become more sophisdticated and can work with these huge Data sinks
  ETLs today can convert data from tehir legacy format to modern data formats and store it into modern Dbs such as DataLake, DataWarehouse
    
## Control Flow && Data Flow
<img src="https://learn.microsoft.com/en-us/azure/architecture/data-guide/images/control-flow-data-flow.png" height=400>

- Control Flow : 
  Ensures orderly processing for a set of tasks using set of precedence constraints into consideration
  Each task has output : Sucess ,Failure or  completion
  Control flow execute data flow as a task
  control flow tasks Cannot run in parallel

- Data Flow :
  Data is extracted from one source, transformed and loaded in data store
  Output for one data flow task is input for next data flow task guded by control flow
  Data flow tasks can run in pararllel

## Azure data factory 
- Cloud based ETL service
- Provides data integeration service that allows :
  create & Schedule data driven workflows that help to : 
  - orchestrate data movements 
  - transforming data at scale using complex compute services such as Azure HDinsight Hadoop, Azure DataBrick, Azure SQL DB
 







