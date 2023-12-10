<a name="readme-top"></a>

<div align="center">
  
# **EDA Project # 1: Customer Churn**

  <p align="center">
    
  <sub><a href="https://cameroncss.com/#contact">Contact Me</a></sub>
<br>
    <br>
     <a href="https://github.com/CameronCSS/PersonalProjects"><strong>« Back to Project Portfolio</strong></a>
  </p>
</div>

<br>

## **I asked CHATgpt this Question:**

  
    "I am a Data Analyst. Can you act as a fake client and give me a question you need answered. 
    Dont tell me where to get the data or how to solve it. 
    
    Just give me a question you need answered that can be solved with data."


<br>

CHATgpt's Scenario Question: :arrow_heading_down:

<img src="https://user-images.githubusercontent.com/121735588/225485787-670711e1-a9c1-44b2-90ec-b6e627f547a4.png"  width="600">


<p align="left"><a href="#results">:heavy_exclamation_mark: View Final results and skip the Breakdown</a></p>


----
## How do we answer this question?

**Since I do not have company data. I need to go find a data set that can help me answer the Question.**
I found a data set on [Kaggle](https://www.kaggle.com/datasets/blastchar/telco-customer-churn) about "Telco customer churn"


This seems like it MIGHT have the data I need.

### First I run the data through my favorite Exploratory report generator, ydata in Python

```python
import numpy as np
import pandas as pd
from ydata_profiling import ProfileReport

df = pd.read_csv("Telco.csv")
profile = ProfileReport(df,title = "Telco Customer Churn")
profile.to_file('Telco_Report.html')
```

This gives an HTML file with a detailed overview of what the data looks like... and it only takes a few seconds to run.

### First looks at the data :arrow_down:

<img src="https://user-images.githubusercontent.com/121735588/225391730-faa858ae-a5e1-4d35-8420-7c9bf34fac3c.JPG"  width="400">

First we notice there are no Null values. This is good news and might indicate the data is relatively clean. 
There are 21 columns, and over 7000 entries.

Lets take a glance at some specifics.

We can already see in our overview a few variables that may give us hints towards what customers remain customers, and who is cancelling service.
We can't draw any conclussions until we look at the data closer. but this gives an idea of a few things to look at.

<br>

:heavy_minus_sign: **Tenure:** <h6>Possible that long standing customers will continue their service.</h6>

<img src="https://user-images.githubusercontent.com/121735588/225393561-139d4008-4df4-4d58-9da4-a901211a5bd5.JPG"  width="600">

:heavy_minus_sign: **Seniors:** <h6>Age may play a factor in wanting to change their service VS sticking with what they know.</h6>

<img src="https://user-images.githubusercontent.com/121735588/225393815-da42bb01-9327-44e5-9310-c6c0bff97d05.JPG"  width="600">

:heavy_minus_sign: **Dependants:** <h6>Having dependants may put strain on the budget causing them to cancel things they dont need.</h6>

<img src="https://user-images.githubusercontent.com/121735588/225393900-68f54d60-b6e0-4505-9cfd-7300fb0c2285.JPG"  width="600">

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Further Exploring the Data

I brought the CSV into Excel to get a better look at the Data.

The first thing I noticed was almost every column used 'Yes' / 'No' Values.
This made things very confusing when looking at the data in pivot tables and charts.

:no_entry_sign: **Yes / No Problem** :heavy_exclamation_mark:

<img src="https://user-images.githubusercontent.com/121735588/225451841-4eb9fd1a-b231-4b5d-9af8-4b17e9764557.JPG"  width="200">

<img src="https://user-images.githubusercontent.com/121735588/225451847-b22e678c-14f6-4e81-90a9-393b0779010f.JPG"  width="300">

After a few **'Find and Replace'** we have better looking data.

:arrow_down: Examples :arrow_down:

<img src="https://user-images.githubusercontent.com/121735588/225458106-2f879626-dc2e-43e4-bd4d-3045a38b3e03.JPG"  width="300">

<img src="https://user-images.githubusercontent.com/121735588/225458069-24468b81-a11a-4d0a-aa86-5e8e3e949f90.JPG"  width="300">

## Visualizing the Data

I first want to test our original hypothesis questions we asked when looking at the Data overview.

Are Seniors willing to change their service?

<img src="https://user-images.githubusercontent.com/121735588/225460056-9d455c79-1e0a-4512-9c0c-adf3507a3b7e.JPG"  width="300">

The above chart is a little deceiving and hard to understand at first. It seems as if Seniors do not have many accounts and even less have cancelled.
This chart should not be used in the final presentation because it makes it a bit hard to understand the data.

THIS chart of the same data, but presented as a different Value, is a Much better way to visualize the data.

<img src="https://user-images.githubusercontent.com/121735588/225460579-5491706c-3f66-4ece-bda1-1eed254024b8.JPG"  width="300">

The new chart clearly shows that when compared to Non-Senior customers, seniors cancel at a much higher rate. Thus, disproving our intial thoughts.

## Next Hypothesis to test.

#### __ Does having dependants put strain on the budget causing customers to cancel ?__

<img src="https://user-images.githubusercontent.com/121735588/225462407-6ed4cd69-3dff-4fb1-8be3-44cbc734fa91.JPG"  height="300"> <img src="https://user-images.githubusercontent.com/121735588/225462425-76ef7204-d947-4dbd-946c-5233170d3329.JPG"  height="300">


Again, our original hypothesis is proven to be the exact opposite. 
This is just another example of why it is important to look at the data before drawing conclusions or developing biases.

## Last Hypothesis to test.

#### __ Do long standing customers want to continue their service ?__

<img src="https://user-images.githubusercontent.com/121735588/225466054-12219b26-e170-48c3-a98b-35aadc9eaa15.JPG"  height="300">

Finally one of our original Hypothesis was correct. The chart reveals a strong correlation between tenure and customer retention at Telco.


 :interrobang: So How do we keep customers??? Looking at our data we only have a few things that we can gather without obtaining more data...

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<a name="results"></a>
# Results

### Reminder what the Original Question was


CHATgpt's Scenario Question: :arrow_heading_down:

<img src="https://user-images.githubusercontent.com/121735588/225485787-670711e1-a9c1-44b2-90ec-b6e627f547a4.png"  width="600">


<br>

Finally we gather insights from the Data, and begin to develop our businsess plan of action.

:arrow_forward: The higher the Avg. cost, there is a direct relation to how many customers cancel their service.

:white_check_mark: **Possible Solution:** Work on loyalty programs that lower the cost for customers who stay, or lower all costs across the board.
 
 <img src="https://user-images.githubusercontent.com/121735588/225481912-5faacc67-9305-4805-b845-b341ab600c0c.JPG"  height="300">
 
:arrow_forward: The data also suggests that customers do not like the method of collecting Electronic Checks.

:white_check_mark: **Possible Solution:** Streamline the process to avoid frustration, Stop Accepting Electronic checks.

<img src="https://user-images.githubusercontent.com/121735588/225480494-4fad47c4-dd2d-4e96-a240-763180aac01b.JPG"  height="300">
 
:arrow_forward: Customers are not satisfied with Fiber internet service. DSL, by contrast, has a staying power of 81%.

:white_check_mark: **Possible Solution:** Look into Fiber service to see if cost is too high, maybe reliability is an issue.

<img src="https://user-images.githubusercontent.com/121735588/225484033-00734482-5759-472d-b76d-da008957e51c.JPG"  height="300">


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
