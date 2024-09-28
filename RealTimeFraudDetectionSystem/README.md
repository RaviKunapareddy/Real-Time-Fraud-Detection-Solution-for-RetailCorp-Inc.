# **Real-Time Fraud Detection Solution for RetailCorp Inc.**
With the rising number of fraud cases, RetailCorp Inc. aims to ensure a secure and enjoyable shopping experience for its customers. 
This project builds a real-time fraud detection system using Kafka, Spark, and NoSQL databases to identify and mitigate fraudulent 
activities swiftly.

![Fraud Detection System](https://github.com/user-attachments/assets/bdc01d82-0a37-437c-9ffb-d1004a1c124e)

## **Key Features**

- **Fraud Detection**: Classifies transactions as fraudulent or genuine using predefined rules and real-time analytics.
- **Real-Time Customer Updates**: Continuously updates customer information to assist in fraud prevention and customer support.

## **Project Components**

### **1. Data Sources**
- **Card Member Data**: Stored in AWS RDS to keep customer and transaction details updated.
- **Historical Transactions**: Available as a CSV file to provide a baseline for fraud detection rules.
- **Real-Time Transactions**: Streamed from POS (Point of Sale) systems to Kafka for immediate analysis.

### **2. Data Processing Workflow**
- **Load Historical Transactions**: Ingests data into a NoSQL database for analysis.
- **Ingest AWS RDS Data**: Loads data into Hadoop for efficient processing and analysis.
- **Create Lookup Table**: A quick-access table with UCL (Upper Control Limit), last transaction details, and credit scores for each customer.
- **Real-Time Transaction Processing**: Uses validation rules to identify potential fraud, such as analyzing spending limits and geographic inconsistencies.

### **3. Validation Rules Examples**
- **Upper Control Limit (UCL)**: Calculated using the moving average and standard deviation of the customer's last 10 transactions. 
  For example, if a customer’s average spend is $100, sudden transactions above $200 could trigger alerts.
- **Credit Score Check**: Transactions are automatically declined if the customer’s credit score is below 200.
- **ZIP Code Distance Check**: Detects improbable travel distances between consecutive transactions. 
  For instance, transactions in New York and then immediately in Los Angeles would raise flags.

## **Tasks and Deliverables**

### **Key Tasks**
1. **Load Transaction History into NoSQL**: Establishes a baseline for transaction analysis.
2. **Ingest AWS RDS Data into Hadoop**: Combines current customer data with historical data for comprehensive analysis.
3. **Create Lookup Table**: Facilitates quick validation of real-time transactions.
4. **Ingest Real-Time Data from Kafka**: Streams transactions for on-the-spot validation.
5. **Update Transactions and Lookup Table**: Ensures records stay up-to-date, maintaining the accuracy of fraud detection.

### **Deliverables**
- **Python Script (`spark-streaming.py`)**: Contains the logic to process incoming data streams.
- **PDF Documentation (`CodeLogic.pdf`)**: Provides an in-depth explanation of the code logic and system architecture.
- **Output Files**: 
  - `Console-output file`: Summarizes the input tables and processing steps.
  - `Timebased-KPI.zip`: Contains JSON files of time-based KPIs for performance analysis.
  - `Country-and-timebased-KPI.zip`: Contains JSON files with KPIs segmented by country and time.

## **Validation Results**
- **Historical Transactions**: 53,292 records processed.
- **AWS RDS Data**: 999 customer records loaded.
- **Final Transaction Count**: Over 59,000 transactions analyzed in real time.

### **Example of Usage:**
- A customer makes a series of transactions rapidly in different locations. The system uses location data, past transaction patterns, 
  and credit scores to determine if these transactions are legitimate or fraudulent, alerting the necessary parties in seconds.

## **Conclusion**
This real-time fraud detection system provides a robust solution for monitoring and validating transactions instantly, enhancing 
both security and customer experience at RetailCorp Inc.
