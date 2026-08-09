# Online Bookstore Data Analysis (SQL)

## Overview
This repository contains a PostgreSQL-based data analysis project for an **Online Bookstore**. The project covers database creation, schema design, CSV data ingestion, and solving 20 business queries ranging from basic filtering to advanced aggregations and table joins.

## Database Schema & ERD
The database consists of three relational tables connected via Foreign Keys (`Customer_ID`, `Book_ID`):

* **Books:** `Book_ID` (PK), `Title`, `Author`, `Genre`, `Published_Year`, `Price`, `Stock`
* **Customers:** `Customer_ID` (PK), `Name`, `Email`, `Phone`, `City`, `Country`
* **Orders:** `Order_ID` (PK), `Customer_ID` (FK), `Book_ID` (FK), `Order_Date`, `Quantity`, `Total_Amount`

```sql
-- Schema Definition
CREATE TABLE Books (
    Book_ID SERIAL PRIMARY KEY,
    Title VARCHAR(100),
    Author VARCHAR(100),
    Genre VARCHAR(50),
    Published_Year INT,
    Price NUMERIC(10, 2),
    Stock INT
);

CREATE TABLE Customers (
    Customer_ID SERIAL PRIMARY KEY,
    Name VARCHAR(100),
    Email VARCHAR(100),
    Phone VARCHAR(15),
    City VARCHAR(50),
    Country VARCHAR(150)
);

CREATE TABLE Orders (
    Order_ID SERIAL PRIMARY KEY,
    Customer_ID INT REFERENCES Customers(Customer_ID),
    Book_ID INT REFERENCES Books(Book_ID),
    Order_Date DATE,
    Quantity INT,
    Total_Amount NUMERIC(10, 2)
);
