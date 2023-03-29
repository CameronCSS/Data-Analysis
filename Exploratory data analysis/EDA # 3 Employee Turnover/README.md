<a name="readme-top"></a>

<div align="center">
  
# **EDA Project # 3: Employee Turnover**

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

<img src="https://user-images.githubusercontent.com/121735588/225486760-222e0dd7-672c-497f-9476-71417de041e0.png"  width="600">

<br>

----
## How do we answer this question?

I found a dataset on Kaggle ["IBM HR Analytics Employee Attrition & Performance"](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset?select=WA_Fn-UseC_-HR-Employee-Attrition.csv)

The dataset contains employee info and Satisfaction survey results. Let's see what Insights we can pull from the data.


# Data Clean / Prep in Excel

:arrow_forward: After we pull the data into Excel I see several things I want to fix before we pull things into Tableau.

First lets change all the survey results. (1 ='Low', 2 = 'Medium', 3 = 'High', 4 = 'Very High')
<br>
Education, PerformanceRating, and WorkLifeBalance need to be fixed separately, because their 1-4 values are unique.

We can do this pretty easily using the built in 'Find and Replace' tool in Excel.

<img src="https://user-images.githubusercontent.com/121735588/228674720-e8ad16eb-dc9d-4f7f-ac6a-6aed5198bd6d.JPG"  width="600">

<br>

While doing this I already noticeed that Performance Rating has everyone rated Excellent or Outstanding. 
<br>
The data may be incorrect, or this variable may be worth ignoring.

<br>
:heavy_minus_sign:

We should also remove Duplicates from the data. I probably should have done this before altering data... but its ok. as long as we remember to do it before trying to visualize our data and find insights.

<img src="https://user-images.githubusercontent.com/121735588/228676590-e8c26605-114b-496e-baa9-8e625e0aadac.png"  width="400">

I noticed while cleaning the data that EmployeeNumber is a unique identifier... and we are missing some values in this column. We may be missing data.

<br>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Data Prep

### The number one thing to keep top of mind while cleaning data is how you want to visualize the data. Would numbers make more sense? Would descriptive words be better? Do you need to put a certain group into buckets???

For instance. I put both the Age and the Monthly Income into buckets. There were so many unique values that viewing the data like that would be very messy and hard to understand.


:arrow_down: Formula I used to put Age into buckets. :arrow_down:
<br>

###### _You could also create a value table and use Vlookup to do this. I will show both ways_
```
=IF( A2 > 50, "50+", IF( A2 > 45, "45-50", IF( A2 > 40, "40-45", IF(A2 > 35, "35-40", IF(A2 > 30, "30-35", IF(A2 > 25, "25-30", IF(A2 > 20, "20-25", "Invalid")))))))
```

:arrow_right_hook: Resulting Ages in Buckets

<img src="https://user-images.githubusercontent.com/121735588/228682983-930f1173-82fd-4175-b5b6-f62dcc9665a4.png"  width="100">

###### _Here is the formula for income brackets_ :arrow_down:
```
=IF(T2 > 20000, "20000+", IF(T2 > 17500, "17500-20000", IF(T2 > 15000, "15000-17500", IF(T2 > 12500, "12500-15000", IF(T2 > 10000, "10000-12500", IF(T2 > 7500, "7500-10000", IF(T2 > 5000, "5000-7500", IF(T2 > 4000, "4000-5000", IF(T2 > 3000, "3000-4000", IF(T2 > 2000, "2000-3000", IF(T2 > 1000, "1000-2000", "Invalid")))))))))))
```

Here is the value table I used for Vlookup to create our income brackets.
<br> 


<img src="https://user-images.githubusercontent.com/121735588/228689189-b423fb59-e327-4ee2-add6-43019a933f81.png"  width="200">

###### _Feel free to use either formulas or VLOOKUP method. Depending on the Data a formula MAY be easier to use._

:arrow_right_hook: Resulting Income in Buckets

<img src="https://user-images.githubusercontent.com/121735588/228685154-25173bf1-da03-49c0-91f3-89141b47efd9.png"  width="200">


## Two important things to remember!!

:one: Remember to Save your new Data as a COPY or a entire new file name. Its good practice to avoid writing over the original data.

:two: Since we are taking this data into another program it is also good practice to take your formula results and 'Paste as Values'  
This will save you from any performance issues or other headaches in the future.
<br>
###### *(IF this data is updated live you will need to leave formulas, or document your formulas so you can adjust new data accordingly)*

<p align="right">(<a href="#readme-top">back to top</a>)</p>

# Import to Tableau

Now that we have clean / prepared Data lets bring it into Tableau and start looking through it.

WIP


<p align="right">(<a href="#readme-top">back to top</a>)</p>

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
