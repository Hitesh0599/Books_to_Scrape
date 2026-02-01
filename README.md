# Books_to_Scrape
Fault-Tolerant Web Data Ingestion Pipeline
Production-grade web scraping and data ingestion system implementing stateful processing, checkpointing, pagination handling, idempotent execution, and multi-layer storage.

Key Features
1. Stateful & Resumable Ingestion
•	Persists pipeline state using an external log file
•	Supports safe resume after crashes or interruptions
•	Skips already completed genres and pages
2. Partitioned Workload Design
•	Each genre processed as an independent data partition
•	Fresh browser session per genre
•	Failure in one partition does not affect others
3. Page-Level Checkpointing
•	Tracks last successful page per genre
•	Implements offset-based resume logic
•	Ensures exactly-once ingestion across reruns
4. Pagination-Aware Scraping
•	Dynamically detects and iterates across pages
•	Logs progress after each successful page
•	Prevents duplicate or missing records
5. Semantic DOM Extraction
•	Uses robust CSS selectors only
•	Avoids brittle absolute paths and XPath
•	Maintains scraping stability across layout changes
6. Structured Data Normalization
•	Extracts and normalizes:
o	Title
o	Price
o	Rating
o	Availability
o	Inventory
o	Description
•	Converts unstructured HTML into analytics-ready schema
7. Multi-Layer Storage Architecture
Layer	Purpose
Genre files	Raw partitioned ingestion
Consolidated file	Master analytics dataset
Log file	Pipeline state & recovery
End-to-End Pipeline Flow
Read Genre List  
→ Check Log File  
→ Start Browser  
→ Navigate to Genre  
→ Resume from Last Page  
→ Scrape Page  
→ Save Data  
→ Update Log  
→ Repeat  
→ Consolidate  
→ Final Dataset
This is a production-style ETL web ingestion system, not ad-hoc scraping
