# **EDA Project # 1: Customer Churn**

## **I asked CHATgpt this Question:**

  
    "I am a Data Analyst. Can you act as a fake client and give me a question you need answered. 
    Dont tell me where to get the data or how to sovle it. 
    
    Just give me a question you need answered that can be solved with data."


<br>

CHATgpt's Scenario Question: :arrow_heading_down:

<img src="https://user-images.githubusercontent.com/121735588/225174521-c16ef880-80b2-4ad0-9b44-c3b162e3afd9.JPG"  width="600">

----
## How do we answer this question?

**Since I do not have company data. I need to go find a data set that can help me answer the Question.**
I found a data set on [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) about "Telco customer churn"


This seems like it MIGHT have the data I need.

### :arrow_forward: First I run the data through my favorite Exploratory report generator, ydata in Python

```python
import numpy as np
import pandas as pd
from ydata_profiling import ProfileReport

df = pd.read_csv("Telco.csv")
profile = ProfileReport(df,title = "Telco Customer Churn")
profile.to_file('Telco_Report.html')
```

This gives an HTML file with a detailed overview of what the data looks like... and it only takes a few seconds to run.

### :arrow_down: First looks at the data :arrow_down:

WIP


----

### View My Other Projects

 <sub>**Click arrow to view content*</sub>
 
<details>
  <summary>SQL Queries</summary>
<a href="https://github.com/CameronCSS/SQL-Queries/tree/main/8%20Week%20SQL%20Challenge%20%23%201" target="new">8 Week SQL Challenge # 1</a>
<br>
&nbsp; &nbsp;:arrow_right_hook: - Explored complex queries to clean data, compute customer figures, and organize data in unusual ways.
<br>
<br>
<a href="https://github.com/CameronCSS/SQL-Queries/tree/main/Khan%20Academy%20Advanced%20SQL" target="new">Khan Academy Advanced SQL</a>
<br>
&nbsp; &nbsp;:arrow_right_hook: - Expand SQL knowledge about combining tables with JOINs and using multiple queries at once.
<br>
<br>
<a href="https://github.com/CameronCSS/SQL-Queries/tree/main/SQLbolt%20-%20SQL%20lessons" target="new">SQLbolt - SQL lessons</a>
<br>
&nbsp; &nbsp;:arrow_right_hook: - Refreshed foundational understanding of SQL and discovered context variations among SQL-powered platforms.
<br>

</details>
    
<br>
<details>
<summary>Programming Projects / Code</summary>

  ## Python Projects
<a href="https://github.com/CameronCSS/Programming-Languages/tree/main/Python%20Wage%20Calculator" target="new">Python Wage Calculator</a>

&nbsp; &nbsp;:arrow_right_hook: - Learned the power of Pandas and PyQt5 libraries. Also learned the importance of notating code for Bug fixing in the future.

## R* Projects
<a href="https://github.com/CameronCSS/Programming-Languages/tree/main/Comparing%20Phone%20Prices%20in%20R" target="new">Comparing Phone Prices in R</a>

&nbsp; &nbsp;:arrow_right_hook: - Explored and cleaned a cell phone price dataset found on [Kaggle](https://www.kaggle.com/datasets/rkiattisak/mobile-phone-price).

<a href="https://github.com/CameronCSS/Programming-Languages/tree/main/R-Basics" target="new">R* Basics</a>

&nbsp; &nbsp;:arrow_right_hook: - Made a full breakdown detailing the basic functions and uses of the R* programming language.

## Javascript Projects
<a href="https://github.com/CameronCSS/Programming-Languages/tree/main/Javascript" target="new">Javascript Code</a>

&nbsp; &nbsp;:arrow_right_hook: - A repo full of my Javascript code. Lots of custom stuff made to work on Carrd websites.
</details>


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
