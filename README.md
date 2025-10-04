# [SQL] What drives global music ranking and customer purchasing? - Music & E-commerce Analytics

<img width="1300" height="918" alt="image" src="https://github.com/user-attachments/assets/8c92c4b4-a417-47a8-b8d3-4a6d25c6d529" />

## Table of Contents
I. [📌 Introduction](#I.-Introduction)

II. [📂 Dataset](#II.-Dataset)

III. [🧠 Main Process](#III.-Main-Process)

IV. [📊 Exploring the Dataset](#IV.-Exploring-the-Dataset)

V. [🔎 Final Conclusion](#V.-Conclusion)

## I. Introduction
🎉 Overview:

This project integrates two domains—global music ranking data and e-commerce transactions—to uncover insights into user behavior, product performance, and music popularity trends.

From the music domain, the project analyzes artists, songs, and their ranking over time to identify patterns in popularity and engagement. From the e-commerce domain, it evaluates buyer profiles, cross-border purchasing behavior, product categories, and order performance, allowing for a deeper understanding of customer segmentation and revenue drivers.

The project applies SQL for data extraction and transformation and Power BI for visualization, enabling interactive dashboards that reveal:

* Top artists and songs by rank trends.

* Sales performance across product categories.

* Cross-border vs. domestic customer behaviors.

* Gender-based customer purchasing insights.

Ultimately, the project demonstrates how data analytics can bridge entertainment trends and consumer purchasing patterns, providing actionable business intelligence.

🏹 Objective:

The main objective is to:

✔️ Understand which artists have the most songs in the global Top 10.

✔️ Evaluate customer lifetime metrics such as total orders, total spending, and purchase frequency.

✔️ Identify top-performing cross-border products.

✔️ Measure customer retention via average time between first and second purchases.

Through these analyses, the project provides a holistic view of how popularity, purchasing patterns, and customer engagement can be quantified and optimized using data.

👤 Who is this project for?

This project is designed for:

✔️ Sales & Marketing Teams

✔️ Supply Chain & Inventory Managers

✔️ Business Analysts & Decision-makers

## II. Dataset

The dataset consists of six tables:

| Table              | Description                                                                          |
| ------------------ | ------------------------------------------------------------------------------------ |
| `artists`          | Contains artist IDs and names.                                                       |
| `songs`            | Links songs to their respective artists.                                             |
| `global_song_rank` | Stores daily song ranks globally.                                                    |
| `my_order_trans`   | Records all transaction details (order ID, customer ID, price, quantity, GMV, etc.). |
| `dim_product`      | Product dimension table with product name and category.                              |
| `my_buyer_profile` | Buyer demographic data (e.g., gender).                                               |

Domains covered:

  🎵 Music Analytics — understanding artist and song performance.

  🛒 E-commerce Analytics — analyzing purchase behavior and product sales.

## III. Main Process

1️⃣ Data Cleaning & Preprocessing
* Ensured session and transaction data integrity
* Filtered out incomplete or irrelevant records

2️⃣ Exploratory Data Analysis (EDA)
* Analyzed bounce rates, page views, and transactions
* Identified key e-commerce actions and trends

3️⃣ SQL Analysis
* Used window functions, joins, and aggregations to extract insights
* Created queries for session behavior and revenue analysis

## IV. Exploring the Dataset
### Query 01: Write a query to determine the top 5 artists whose songs appear in the Top 10 of the global_song_rank table the most.

Assumptions:

* If two artists' songs have the same number of appearances, the artists should have the same rank. 

* The rank number should be continuous (1, 2, 2, 3, 4, 5) and not skipped (1, 2, 2, 4, 5).

* We start by calculating the main financial metrics grouped by both region and item type.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:3b4e18a8577143fa83e12bbe764e2b62)
* SQL code

<img width="900" height="541" alt="image" src="https://github.com/user-attachments/assets/dba4a1f2-aa1a-4cfb-809e-0e6e02930251" />

* Query results

<img width="900" height="447" alt="image" src="https://github.com/user-attachments/assets/aa8388b6-e994-4612-b368-1aea4c3006e6" />

→ Identified artists like Bad Bunny and Ed Sheeran dominating the global Top 10 chart.

### Query 02: Find the lifetime total orders, total spent (GMV), unique items bought, earliest purchase date, last purchased date, average amount spent per order (AOV) and average purchase price (APP) for the following buyer IDs and their purchased products’ categories: 1076216361964070, 3190859517651870, 3754202390878020.

Note:

* total orders: count distinct - order_id

* unique items bought: count distinct - product_id

* average amount spent per order: total GMV / total order

* average purchase price: total price/ total order.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:af55cea750ed431ba63dc840a247ceed)
* SQL code

<img width="900" height="439" alt="image" src="https://github.com/user-attachments/assets/8b1cd193-dea4-43bc-be14-93318b41d349" />

* Query results

<img width="900" height="365" alt="image" src="https://github.com/user-attachments/assets/a7c6c3df-ccc4-4fb9-b821-598e18e62de0" />

→ Calculated total orders, GMV, unique items, AOV, and APP per customer.

### Query 03: Find out the top 10 cross border items with the highest quantity sold. The output includes minimum selling price, total spent (gmv) and total orders.

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:0fe8285b5e0a47bc9c5ee0ce97283ce0)
* SQL code

<img width="900" height="632" alt="image" src="https://github.com/user-attachments/assets/1c639bb8-535d-4dac-9fc4-878655d164a5" />

* Query results

<img width="900" height="555" alt="image" src="https://github.com/user-attachments/assets/a554ed3e-6768-43ca-9ff7-1f2d444a83d1" />

→ Highlighted high-demand international items with strong GMV performance.

### Query 04: Find the average time (in day unit) between customer’s first and second checkout (for example avg. time is 3.4 day which is calculated for average metric of all customer base).

[Link to code](https://console.cloud.google.com/bigquery?sq=322729696559:a377e7a3472349698212f9941724d306)
* SQL code

<img width="900" height="498" alt="image" src="https://github.com/user-attachments/assets/bd06c8e0-3446-489a-b1a0-ff39bd0dbd5c" />

* Query results

<img width="900" height="260" alt="image" src="https://github.com/user-attachments/assets/6530d5ba-2fbd-4931-8fa9-7e552a73abcc" />

→ Found the average return interval between first and second purchases (e.g., 3.4 days).

## V. Conclusion
✔️ Music domain: A small group of artists consistently dominate the Top 10, reflecting strong brand power and global popularity.

✔️ E-commerce domain: Customers show recurring purchasing patterns, with measurable differences between cross-border and domestic orders.

✔️ Customer retention: The average interval between first and second purchases provides actionable insight into engagement and remarketing strategies.

✔️ Analytical takeaway: Using SQL in BigQuery enables deep, business-driven insights that can later be visualized in Power BI dashboards to support data-informed decisions.


