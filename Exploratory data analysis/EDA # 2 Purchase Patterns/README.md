<a name="readme-top"></a>

<div align="center">
  
# **EDA Project # 2: Purchase Patterns**

  <p align="center">
    
  <sub><a href="https://cameroncss.com/#contact">:wavy_dash: Contact me :wavy_dash:</a></sub>
<br>
    <br>
     <a href="https://github.com/CameronCSS/Data-Analysis/tree/main/Exploratory%20data%20analysis"><strong>« Back to Exploratory Data Analysis</strong></a>
  </p>
</div>

<br>

## **I asked CHATgpt this Question:**

  
    "I am a Data Analyst. Can you act as a fake client and give me a question you need answered. 
    Dont tell me where to get the data or how to solve it. 
    
    Just give me a question you need answered that can be solved with data."


<br>


CHATgpt's Scenario Question: :arrow_heading_down:

<img src="https://user-images.githubusercontent.com/121735588/225486786-56f78f66-624e-4840-8325-33e82a949599.png"  width="600">

<br>

----
## How do we answer this question?

I found a Dataset on [Maven Analytics](https://www.mavenanalytics.io/data-playground) that contains "A year's worth of sales from a fictitious pizza place."

I believe this will be the perfect Data to explore to answer the Scenario Question.

### :arrow_forward: Loading the Data into SQL server

The data is set up in as a relational database. The best way to explore it will be through SQL.

![pizza data](https://user-images.githubusercontent.com/121735588/225492051-69dad4ef-4270-4260-8ee4-d6613c85e331.JPG)

:hash: CREATE our DATABASE and TABLES in SQL

<sub>:arrow_down: **Click to view code* </sub>

<details>
<summary>SQL code</summary>

<br>

```SQL
CREATE DATABASE pizza_sales;

USE pizza_sales;

CREATE TABLE order_details (
    order_details_id INT,
    order_id INT,
    pizza_id VARCHAR(50),
    quantity INT
);

BULK INSERT order_details
FROM 'order_details.csv'
WITH (
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n',
    FIRSTROW = 2
);

CREATE TABLE orders (
    order_id INT,
    date DATE,
    time DATETIME
);

BULK INSERT orders
FROM 'orders.csv'
WITH (
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n',
    FIRSTROW = 2
);

CREATE TABLE pizza_types (
    pizza_type_id VARCHAR(50),
    name VARCHAR(50),
    category VARCHAR(50),
	ingredients VARCHAR(100)
);

BULK INSERT pizza_types
FROM 'pizza_types.csv'
WITH (
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n',
    FIRSTROW = 2
);

CREATE TABLE pizzas (
    pizza_id VARCHAR(50),
    pizza_type_id VARCHAR(50),
    size VARCHAR(50),
	price FLOAT
);

BULK INSERT pizzas
FROM 'pizzas.csv'
WITH (
    FIELDTERMINATOR = ',',
    ROWTERMINATOR = '\n',
    FIRSTROW = 2
);
```

</details>


Lets double check our data to make sure it took

```SQL
SELECT TOP 5 * FROM pizzas;
```

### Results :arrow_heading_down:

![pizza check data](https://user-images.githubusercontent.com/121735588/225496103-a6514ef0-c49c-45ec-ae72-84351d9f3446.JPG)


It seems our data is loaded in our SQL database. Now lets begin exploring the data to see if we can answer our question.


## Data Exploring




# WIP


----

<a name="Contact"></a> 
## <a href="https://cameroncss.com/#contact">Contact Me</a>

  </table>
  <p style="margin-left: auto;">
    <a href="https://docs.google.com/document/d/1idTVL4nRGOejqW6EkpfhsD-dNQRLzmX08y5hI3TYLns/edit?usp=sharing" target="_blank" rel="noopener noreferrer">
      <img src="https://user-images.githubusercontent.com/121735588/215364205-abdfc0ac-53db-4733-8d43-b57c1bafb802.png" alt="Resume button">
    </a>
  </p>
</div>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
