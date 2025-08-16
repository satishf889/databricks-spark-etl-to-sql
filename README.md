# Databricks Spark ETL Pipeline

This project demonstrates an end-to-end Extract, Transform, Load (ETL) pipeline using **Apache Spark** on the **Databricks** platform. It reads raw data from a CSV file, processes it, and loads the refined data into a SQL database. This project is a solid example of cloud-based data engineering and showcases proficiency with distributed data processing.

## 🚀 Project Overview

The pipeline automates the entire process of getting raw data from a source and preparing it for a data warehouse or business intelligence application. The core components of the pipeline are:

1.  **Extract:** Reading raw data directly from a CSV file stored in Databricks File System (DBFS) or cloud storage.
2.  **Transform:** Using the power of Apache Spark to perform data cleaning, aggregation, and feature engineering.
3.  **Load:** Writing the cleaned, structured data into a SQL database for downstream consumption.

This project can serve as a template for more complex ETL jobs, providing a clean and organized approach to data engineering on a distributed platform.

## 🛠️ Technologies Used

- **Databricks:** The unified analytics platform for building data applications.
- **Apache Spark:** The distributed computing engine for processing large datasets.
- **Python:** The primary language for scripting and data manipulation.
- **SQL Database:** A relational database (e.g., PostgreSQL, MySQL, or SQL Server) to store the final, processed data.

## 📂 Project Structure

This project is designed to be run within the Databricks environment. The main components are typically organized within a Databricks Notebook.

```
.
├── notebooks/
│   └── etl_pipeline_notebook.dbc    # The main Databricks Notebook file
├── data/
│   └── sales_orders.csv             # Sample input data file
└── README.md                        # This file
```

## 📝 How to Run the Project

### **Prerequisites**

- An active **Databricks workspace**.
- A Databricks cluster configured with **Spark**.
- Access credentials for your target **SQL database**.

### **Steps**

1.  **Upload the Notebook:**

    - In your Databricks workspace, click **"Workspace"** on the left sidebar.
    - Navigate to the desired folder, right-click, and select **"Import"**.
    - Import the `etl_pipeline_notebook.dbc` file into your workspace.

2.  **Upload the Data:**

    - Go to **"Data"** \> **"Create Table"** \> **"Upload File"**.
    - Upload the `sales_orders.csv` file. Note the file path, as you will need it in the notebook (e.g., `/FileStore/tables/sales_orders.csv`).

3.  **Configure Database Connection:**

    - Open the `etl_pipeline_notebook.dbc` in your workspace.
    - Update the database connection details (host, port, username, password, and database name) in the notebook's configuration cells.
    - Ensure the required JDBC driver is installed on your cluster or accessible via Maven.

4.  **Run the Pipeline:**

    - Attach the notebook to your Spark cluster.
    - Execute the cells sequentially to run the entire ETL process. The script will:
      - Read the CSV file.
      - Perform data transformations.
      - Write the final data to the specified SQL database table.

## 🔍 Code Snippets (Illustrative)

### **Reading the Data**

```python
# Load the CSV file into a Spark DataFrame
file_path = "dbfs:/FileStore/tables/sales_orders.csv"
df_raw = spark.read.csv(file_path, header=True, inferSchema=True)
```

### **Loading into SQL Database**

```python
# Write the transformed data to the SQL database
df_transformed.write \
    .format("jdbc") \
    .option("url", jdbc_url) \
    .option("dbtable", "dbo.sales_data_processed") \
    .option("user", user) \
    .option("password", password) \
    .mode("overwrite") \
    .save()
```

By following these steps, you can successfully run this ETL pipeline and demonstrate a foundational skill set in modern data engineering.
