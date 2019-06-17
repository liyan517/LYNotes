### Table of Contents
**[Project Experiences](#Project-Experiences)**<br>
**[Database Related Questions](#Database-related-questions)**<br>


## Project Experiences

categorize my recent projects into 3 category 

### 1. department wise reporting and analysis data mart. project composed of mainly batch data etl layer. 
Business Value: empower data analysis to get insight on department operational capability and KPI. Ingest data from various application and model data in wide table/denormalized data model to service BI tool(Tableau) 
Role: Tech Lead, cover BA, help with data model, ETL pipe line design and implementation.

Side project: Dashboard portal; Eurika NLP engine for data query and visualization.
Challenge: data pipeline design for bettwe efficiency 
          data service proformance, volume is large and reporting required longer time window to analyze trend and slice and dice by multiple dimension.
          data quality and readyness check.
          
Feature: 
Possible solution:


### 2. Business driven web application. Comprised of data ingestion pipeline, application server and application web client.
Business Value: automate manual operation for compliance reporting. build system to safe guard operation process and data validation.

concurrency issues


**Overall challenges:**<br>
**Performance:**<br>

- Write: 
   * cache share dataset(reference data)
   * optimize sql for source data extraction(filter, join)
- Read:
DB setup: master and slave DB. Master handles(IUD, write, and send transaction log to slave for replication) and slave DB handle read 

   * for batch data processing, once per day.
   

## Database Related Questions
*Q1. How to handle replica lag?<br>
A. impact: is your business need required immediate read of updated data? for long term analysis -> no. <br>
why got replica lag: too many transaction for replica to keep up -> fix by scaling: data sharding.<br>
long transaction that take up server resources. fixed by application design to optimize query, control query timeout. reduce DB IO by caching slow changing data.<br>
base on business use case:<br>
strong consistancy: enforce the write transaction to be successful only if the replica catch up. and prevent read immediatly after write.<br>
