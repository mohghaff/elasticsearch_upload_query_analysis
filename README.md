Project Documentation: Elasticsearch Data Upload and Queries
Introduction
This documentation outlines the process of uploading data to Elasticsearch using API keys and performing various queries and aggregations. The project involved working with different datasets to demonstrate Elasticsearch's capabilities. The materials and code used in this project were provided by Ben Sullins in the LinkedIn Learning course "Elasticsearch Essential Training."

Prerequisites
Before proceeding, ensure you have the following prerequisites in place:

Elasticsearch cluster with API access.
Ubuntu Linux environment.
Data files to upload.
Uploading Data
Step 1: Create an API Key in Kibana
Log in to Kibana and create an API key.
Step 2: Set Variables
Set two variables for the Elasticsearch endpoint (ES_HOST) and the API key (ES_API_KEY).
Step 3: Create a Data File
Using the vi editor, create a file (e.g., reqs) and paste the following data into it:
json
Copy code
{ "index" : { "_index" : "my-test", "_id" : "1" } }
{ "col1" : "val1"}
{ "index" : { "_index" : "my-test", "_id" : "2" } }
{ "col1" : "val2"}
{ "index" : { "_index" : "my-test", "_id" : "3" } }
{ "col1" : "val3" }
Step 4: Upload Data to Elasticsearch
Use the following curl command to upload the data file to the Elasticsearch cluster and create an index:
bash
Copy code
curl -XPOST -i -k \
-H "Content-Type: application/x-ndjson" \
-H "Authorization: ApiKey $ES_API_KEY" \
$ES_HOST/_bulk --data-binary "@reqs"; echo
Working with Elasticsearch
Step 5: Log in to Kibana
Log in to the Elasticsearch cluster in the web portal.
Step 6: Access Dev Tools
Navigate to "Dev Tools" in Kibana to execute queries.
Step 7: Query Indices
Run queries to interact with Elasticsearch data. Examples:

List all indices: GET /_cat/indices?v
Retrieve data from the my-test index: GET /my-test
Retrieve a specific document from the my-test index: GET /my-test/_doc/1
Additional Data Uploads
Step 8: Upload Additional Data
Upload more data, such as the accounts.json file, using similar steps as above.
Step 9: Set Index Pattern in Kibana
In Kibana, navigate to "Management" > "Stack Management" > "Kibana" > "Data Views" and create a data view for the newly uploaded data.
Elasticsearch Data Manipulation
Step 10: Manipulate Data Structure
Modify the Elasticsearch data structure by adding mappings for specific fields, such as geographical coordinates.
Step 11: Import Log Files
Import log files (e.g., logs.jsonl) into Elasticsearch using curl commands.
Querying Elasticsearch
Step 12: Run Queries
Execute various Elasticsearch queries to retrieve and filter data. Examples include:
Retrieve all data: GET bank/_search
Find accounts in California: GET bank/_search { "query": { "match": { "state": "CA" } } }
Combine queries to find accounts in California not associated with "Techade."
Term-Level Queries
Step 13: Term-Level Queries
Perform term-level queries and range queries on Elasticsearch data. Examples include searching for exact matches and querying based on numerical ranges.
Tokenization and Analyzers
Step 14: Tokenization and Analyzers
Analyze text data using tokenization and analyzers to break down and index text for efficient searching.
Aggregations
Step 15: Aggregations
Implement Elasticsearch aggregations to obtain insights from data. Examples include counting accounts by state and calculating average balances.
Visualization (Kibana)
Step 16: Visualization in Kibana
Use Kibana to create visualizations and dashboards based on Elasticsearch data, allowing for easy data exploration and presentation.
Conclusion
This project demonstrates the process of uploading data to Elasticsearch, querying data, and leveraging Elasticsearch's features for data manipulation and visualization. Elasticsearch provides powerful tools for managing and analyzing large datasets.

