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

<p align="left"><a href="#results">:heavy_exclamation_mark: View Final results and skip the Breakdown</a></p>


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

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Data Exploring

I start running a few random SQL queries to get a feel for the data

```SQL
SELECT TOP 10 * FROM order_details
ORDER BY quantity DESC
```
Results :arrow_heading_down:

![top 10 pizza orders](https://user-images.githubusercontent.com/121735588/225793290-e646606e-5bf3-4197-a83e-d927fe3da7a4.JPG)


```SQL
SELECT TOP 10 pizza_id, COUNT(*) AS p_count
FROM order_details
GROUP BY pizza_id
ORDER BY p_count DESC
```
Results :arrow_heading_down:

![top 10 pizza count](https://user-images.githubusercontent.com/121735588/225793360-6de9005a-1379-4d3c-baee-955672c197eb.JPG)


```SQL
SELECT SUM(p_count) AS ckn_count
FROM (
    SELECT pizza_id, COUNT(*) AS p_count
    FROM order_details
    WHERE pizza_id LIKE '%ckn%'
    GROUP BY pizza_id
) subquery
```
Results :arrow_heading_down:

![ckn count](https://user-images.githubusercontent.com/121735588/225793491-8265698d-53b5-48ab-a76b-0921e8f54a96.JPG)


#### I think we found our most popular topping. We need to keep exploring the data to see if we can find any patterns or common pizza orders.

Our Queries are going to get a little more complicated now.

```SQL
SELECT TOP 5
    COALESCE(large.pizza_id, med.pizza_id, small.pizza_id) AS pizza_id,
    COALESCE(large.large_count, 0) AS large_count,
    COALESCE(med.med_count, 0) AS med_count,
    COALESCE(small.small_count, 0) AS small_count,
    (COALESCE(large.large_count, 0) + COALESCE(med.med_count, 0) + COALESCE(small.small_count, 0)) AS total_count

FROM
    (
	SELECT LEFT(pizza_id, LEN(pizza_id) - 2) AS pizza_id, COUNT(*) AS large_count
		FROM order_details
			WHERE pizza_id LIKE '%_l'
			GROUP BY LEFT(pizza_id, LEN(pizza_id) - 2)) AS large
    FULL OUTER JOIN 
    (
	SELECT LEFT(pizza_id, LEN(pizza_id) - 2) AS pizza_id, COUNT(*) AS med_count
		FROM order_details
			WHERE pizza_id LIKE '%_m'
			GROUP BY LEFT(pizza_id, LEN(pizza_id) - 2)) AS med
		ON large.pizza_id = med.pizza_id
    FULL OUTER JOIN
    (
	SELECT LEFT(pizza_id, LEN(pizza_id) - 2) AS pizza_id, COUNT(*) AS small_count
		FROM order_details
			WHERE pizza_id LIKE '%_s'
			GROUP BY LEFT(pizza_id, LEN(pizza_id) - 2)) AS small
		ON COALESCE(large.pizza_id, med.pizza_id) = small.pizza_id

ORDER BY total_count DESC;
```
Results: Top 5 Pizzas Overall :arrow_heading_down:

![top 5 overall orders](https://user-images.githubusercontent.com/121735588/225807441-f8d9965a-b5ec-4153-955c-b1eed641c830.JPG)


#### We can look at the same top 5 for Large, Medium, and Small pizzas.

TOP 5 LARGE

![top 5 large orders](https://user-images.githubusercontent.com/121735588/225807987-fc5e15a4-3407-45e2-9f80-2efac005e64c.JPG)

TOP 5 MEDIUM

![top 5 med orders](https://user-images.githubusercontent.com/121735588/225808000-cdd2e460-42e8-4738-82a8-059a8628a13c.JPG)

TOP 5 SMALL

![top 5 small orders](https://user-images.githubusercontent.com/121735588/225808003-b1cbcdcf-e25a-4d11-8b45-e9f588433997.JPG)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Lets explore some of the other tables for any insights.

```SQL
WITH DayOfWeek AS (
  SELECT order_id, DATENAME(dw, date) AS day_of_week
  FROM orders
)

SELECT day_of_week, COUNT(order_id) AS Count
FROM DayOfWeek
GROUP BY day_of_week
```
Results: :arrow_heading_down:

![Days of week count](https://user-images.githubusercontent.com/121735588/225810422-fc2e81bd-875c-42cb-9ad8-63b2dc0451ad.JPG)

<a name="results"></a>
# Results

### Reminder what the Original Question was


CHATgpt's Scenario Question: :arrow_heading_down:

<img src="https://user-images.githubusercontent.com/121735588/225486786-56f78f66-624e-4840-8325-33e82a949599.png"  width="600">

<br>

Have we discovered any Customer Trends? Possible favorite pizzas?

:arrow_forward: Saturday and Wednesday are the most popular days people order Pizza.

![Days of week count](https://user-images.githubusercontent.com/121735588/225814347-ebcedffa-ce72-437b-84a5-e93637cf4c80.JPG)


:arrow_forward: Meats are popular, Especially chicken which is the most popular pizza topping overall.

![top 5 overall orders](https://user-images.githubusercontent.com/121735588/225811880-6fae2942-5d44-46e1-89d2-9da2883241c7.JPG)

![ckn count](https://user-images.githubusercontent.com/121735588/225814266-601a87b1-2917-4135-8bf9-9878e687cb91.JPG)


:arrow_forward: The most shocking insight may be that Hawaiian is more popular than Pepperoni. I guess pineapple DOES belong on pizza.

![hawaiian vs pep](https://user-images.githubusercontent.com/121735588/225814034-a05473dd-b556-4bda-aee4-ce88f1aadc67.JPG)


### :large_blue_diamond: You can view all the SQL code I've used to explore the Database [HERE](https://github.com/CameronCSS/SQL-Queries/blob/main/EDA_2_RAW.SQL)

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
