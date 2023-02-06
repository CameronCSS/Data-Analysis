<a name="readme-top"></a>
<div align="center">

![image](https://user-images.githubusercontent.com/121735588/216799897-0faa63e3-daa7-4091-8ec5-4a639239cb64.png)

   <sub><a href="#Contact">:wavy_dash: Contact Info :wavy_dash:</a></sub>
<br>
    <br>
     <a href="https://github.com/CameronCSS/Data-Analysis/blob/main/Power-BI-Dashboards/README.md"><strong>« Back to Power BI dashboards</strong></a>
  </p>
</div>

<br>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
    <ul>
    <li><a href="#Preparing">Preparing the Database</a></li>
    <li><a href="#Identify">Identify Data Needs</a></li>
    <li><a href="#Cleaning">Data Cleaning</a></li>
    <li><a href="#Transform">Data Transform/Import</a></li>
    <li><a href="#Creating">Creating the Dashboard</a></li>
    <li><a href="#Publish">Final touches and Publish</a></li>
    <li><a href="#Finished">Finish / Publish to Power BI services</a></li>
    <li><a href="#Contact">Contact</a></li>
    <li><a href="#Contact">Resume</a></li>
    </ul>
</details>


<br>

## Adventure Works Sample Database

AdventureWorks<sup>*</sup> is a sample relational database used to demonstrate features of Microsoft SQL Server. 
<br><em><sub><a href="https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver15&tabs=ssms">*Adventureworks database</a> was initially released in 2004 and has since been updated to provide a more complex and representative sample database.</sub></em>
<br>
<br>The database includes data for a fictional bicycle manufacturer called 'Adventure Works Cycles' and includes data such as sales, production, purchasing, and human resources information.
<br>
<br>
:construction: We will be using the 'Adventure Works database' in a simulated business scenario to create a dashboard to present to a fictional manager.
<br>
<br><em><sup>If you would to skip the breakdown you can download the report here.</sup></em>
<sup>  :arrow_right:
<a href="https://github.com/CameronCSS/Data-Analysis/raw/main/Power-BI-Dashboards/AdventureWorks/Sales%20report.pbix" target="_blank">Download Sales Report .pbix</a></sup>

##

<a name="Preparing"></a>
### Preparing the Database
----
:one::heavy_minus_sign: First we restore the .bak file and bring the database into Microsoft SQL Server.
<br>
<br>:two::heavy_minus_sign: Next we do a Test query to make sure our data loaded and looks ok. :arrow_heading_down:
```sql
-- Test query to check our data
SELECT TOP 5 *
FROM AdventureWorksDW2019.dbo.DimCustomer;
```
<details>
    <summary>View Our test query data</summary> 
 
| FirstName | MiddleName | LastName | NameStyle | BirthDate | MaritalStatus | Suffix | Gender | EmailAddress | YearlyIncome | TotalChildren |
|-----------|------------|----------|----------|----------|--------------|--------|--------|-------------|-------------|--------------|
| Jon       | V          | Yang     | 0        | 1971-10-06 | M            | NULL   | M      | jon24@adventure-works.com | 90000.00   | 2            |
| Eugene    | L          | Huang    | 0        | 1976-05-10 | S            | NULL   | M      | eugene10@adventure-works.com | 60000.00   | 3            |
| Ruben     | NULL       | Torres   | 0        | 1971-02-09 | M            | NULL   | M      | ruben35@adventure-works.com | 60000.00   | 3            |
| Christy   | NULL       | Zhu      | 0        | 1973-08-14 | S            | NULL   | F      | christy12@adventure-works.com | 70000.00   | 0            |
| Elizabeth | NULL       | Johnson  | 0        | 1979-08-05 | S            | NULL   | F      | elizabeth5@adventure-works.com | 80000.00   | 5            |
 
</details>

<a name="Identify"></a>
### Identify Data Needs
----

:three::heavy_minus_sign: We need to closely review our Manager's email to understand the specific sales data he requires in order to create an effective dashboard.
<br>
<br>

<details>
  <summary>View Manager's Email</summary>
  
![manager email](https://user-images.githubusercontent.com/121735588/216856570-f1cda79f-b9d7-42fa-8f5a-1702d5295d21.png)

  
</details>

:four::heavy_minus_sign: Next we need to examine our database and identify what tables we will need to make our dashboard.
<br> &nbsp; &nbsp;<em><sub>Our database has several Fact tables, and several Dimension tables. We will need to think carefully about which tables we need to key the data together.</sub></em>

<details>
  <summary>View Database tables</summary>
  <em><sup><sub>*We may discover we need more tables as we start building our report</sub></sup></em>

![image](https://user-images.githubusercontent.com/121735588/216800539-d909e635-e2da-4fbb-bf58-623b1fd06403.png)

</details>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<a name="Cleaning"></a>
### Data Cleaning
----

:five::heavy_minus_sign: Now we need to start Querying our tables and figure out what data needs to be Cleaned/Transformed for our report.
- Data cleaning may involve removing duplicates, correcting misspelled text, filling in missing values, 
  transforming data into a consistent format, and removing outliers, unwanted data or invalid data.
<details>
  <summary>View Cleaning Examples</summary>
<em><sup><sub>*This is only a sample of the overall cleaning process</sub></sup></em>
<br>:heavy_minus_sign:
  
![image](https://user-images.githubusercontent.com/121735588/216801679-7ca5d1c0-3a29-49e2-ad35-f11c1a466b4f.png)

:heavy_minus_sign:
  
![image](https://user-images.githubusercontent.com/121735588/216802184-e85f979c-e03b-4c08-ab3d-aaf683e996b4.png)

:heavy_minus_sign:

![image](https://user-images.githubusercontent.com/121735588/216802576-d7bc3feb-9fd0-4568-af43-706d49764ad2.png)

:heavy_minus_sign:
  
![image](https://user-images.githubusercontent.com/121735588/216802892-003bd488-6c6a-4bf6-8499-4f6a0b545660.png)
  
:heavy_minus_sign:

</details>

<a name="Transform"></a>
### Data Transform/Import
----

:six::heavy_minus_sign: There are various methods to transfer cleaned data from SQL to Power BI, depending on your data infrastructure and requirements. 
<details>
  <summary>View Data Import Methods</summary>
<br>&nbsp; &nbsp; One approach is to export the cleaning query results as a CSV file and import it into Power BI. Another option is to use DirectQuery to connect Power BI directly to the SQL database, providing real-time data retrieval. 
<br>
<br>
  
![image](https://user-images.githubusercontent.com/121735588/216803739-717e4a33-f655-42e6-9f18-52f2749f13da.png)

<br>You could also set up scheduled procedures in SQL to update the tables and utilize Power BI Dataflows to automate the data import process, avoiding the need for manual imports.
<br>
<br>

![image](https://user-images.githubusercontent.com/121735588/216803685-2657b4b8-bce1-4375-b3f0-c653bb2b93b7.png)

<br>
  This all depends on your needs and how your Data storage/data pipeline is set up.
  <br>
  :heavy_minus_sign:

</details>
  <br>
:heavy_exclamation_mark: I have decided to save the results of our cleaning queries as CSV and import the data into Power BI.
<br>
<br>
:seven::heavy_minus_sign: When we add the Data to Power BI it is a good idea to 'Transform Data' and double check that your data formats are correct.
<br>
<br>
<details>
  <summary>View Data Transform/Format</summary>
  <br> :heavy_minus_sign:
  
![image](https://user-images.githubusercontent.com/121735588/216804055-f746011c-9422-440d-8647-d131dd3c988c.png)

<br>
:heavy_minus_sign:

![image](https://user-images.githubusercontent.com/121735588/216804031-7f27b57e-493f-47cf-af2f-3200df388492.png)

:heavy_minus_sign:

</details>

:eight::heavy_minus_sign: Before we start building our dashboard we need to make sure all the Data Relations are set up correctly.
<details>
  <summary>View Data Relationships</summary>
  
  ![image](https://user-images.githubusercontent.com/121735588/216849187-54e79ef8-e23b-4d90-a271-ab2ebf1e39e4.png)

  </details>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<a name="Creating"></a>
### Creating the Dashboard
----
  
  :nine::heavy_minus_sign: Next we start building the dashboard and adding data we want to view, while keeping our end goal in mind.
  <details>
  <summary>View First Draft of our Dashboard</summary>
  <br>
  
![image](https://user-images.githubusercontent.com/121735588/216849675-ae3216bc-cb6f-4393-81e1-7bf38f0aa4a0.png)

  </details>
  
 :keycap_ten::heavy_minus_sign: The general guideline for dashboard design is to keep the number of visuals to a minimum, typically no more than 6-7. The reason for this is to avoid overwhelming the user with too much information, and to ensure that each visualization effectively communicates its message.
 
 <br> Our current dashboard already utilized 6 visuals, let's create another page to provide additional space for a more detailed analysis of the data.
 <br>
 
 ![image](https://user-images.githubusercontent.com/121735588/216849917-09e9b04a-3412-41f4-919a-e204be219bf8.png)

 :one::one::heavy_minus_sign: Next we need to build out our other pages and finalize our overall design.
 
 <details>
 <summary>View First Draft of our other Page</summary>
  <br>
  :heavy_minus_sign:
  
 ![image](https://user-images.githubusercontent.com/121735588/216850801-bfdc7100-8de2-47d6-b01b-6d757e7691fa.png)

  :heavy_minus_sign:
  <br>
  </details>

<a name="Publish"></a>
### Final touches and Publish
----

:one::two::heavy_minus_sign: Before you present the data it is a good idea to go through and check for errors, and remove any unnecessary data.

:heavy_minus_sign:

:one::three::heavy_minus_sign: Finally we add some spark :sparkles: with a few navigation buttons, some color themes that look good, and organize our visuals.

:checkered_flag::checkered_flag:

<a name="Finished"></a>
### FINISHED!

## Publish to Power BI services

Now we just publish our dashboard, and send it to the appropriate parties.

 <details>
 <summary>View the final dashboard</summary>
<br>
View the <a href ="https://app.powerbi.com/reportEmbed?reportId=b0fcfc95-aa85-4802-b47f-7e0fb300a481&autoAuth=true&ctid=ac060c52-a55a-40ca-9f98-cef91bfc7881">Final Sales Report</a> on Power BI Web services. <sub><sup>*You will need to sign in to Power BI</sub></sup>
  <br>
  :heavy_minus_sign: 
  <br>
  <br>
  [Dashboard Preivew] :arrow_heading_down:
  <br>
  <br>
  
  ![image](https://user-images.githubusercontent.com/121735588/216891607-ff81e7a6-bf0b-4e6a-9531-7898513d155d.png)

  
  
</details>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

----
### View My Other Projects
    
<details>
<summary>Data Analysis / Visuals Projects</summary>
<a href="https://cameroncss.github.io/Data-Analysis/Netflix/index.html" target="new">Netflix Movies and TV Shows</a>
<br>
&nbsp; &nbsp;:arrow_right_hook: - Built out multiple sheets to display on a single visual, and created an interactive dashboard.
<br>	
<br>
<a href="https://github.com/CameronCSS/Data-Analysis/tree/main/SLC%20civilian%20complaints" target="new">SLC civilian complaints</a>
  <br>
&nbsp; &nbsp;:arrow_right_hook: - Utilized API calls to gather data from public sources. Built a local DB to use in Power BI to uncover valuable insights.
  <br>
</details>
<br>

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
<a href="https://github.com/CameronCSS/Programming-Languages/tree/main/Python%20Wage%20Calculator" target="new">Python Wage Calculator</a>

&nbsp; &nbsp;:arrow_right_hook: - Learned the power of Pandas and PyQt5 libraries. Also learned the importance of notating code for Bug fixing in the future.
</details>

----

<a name="Contact"></a> 

## Contact Me

<div style="display: flex;">
  <table style="flex: 1;">
  
||
| --- |
| <a href="mailto:CameronSeamons@gmail.com">![gmail icon](https://user-images.githubusercontent.com/121735588/216516513-1bd223b5-89d4-4d02-860e-b132c18c47d9.png):heavy_minus_sign: CameronSeamons@gmail.com |
| <a href="https://www.linkedin.com/in/cameron-css/">![linkedin](https://user-images.githubusercontent.com/121735588/215363352-ad51a5e1-0de8-48be-8ceb-28c610e5d34d.png)</a> :heavy_minus_sign: https://www.linkedin.com/in/cameron-css/|
| <a href="https://twitter.com/Cameron_CSS">![twitter logo](https://user-images.githubusercontent.com/121735588/215363444-e4b080b6-e122-49cb-8b41-601dab6e10eb.png)</a> :heavy_minus_sign: https://twitter.com/Cameron_CSS |

  </table>
  <p style="margin-left: auto;">
    <a href="https://drive.google.com/file/d/19vkbf2HjEpXpxndWYa4A6Dyt6gsnGv73/view?usp=sharing" target="_blank" rel="noopener noreferrer">
      <img src="https://user-images.githubusercontent.com/121735588/215364205-abdfc0ac-53db-4733-8d43-b57c1bafb802.png" alt="Resume button">
    </a>
  </p>
</div>

<p align="right">(<a href="#readme-top">back to top</a>)</p>
