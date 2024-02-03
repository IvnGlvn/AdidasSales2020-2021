<a href="https://public.tableau.com/app/profile/ivan.galvan/viz/Adidas_Sales_Report20202021/Dashboard" target="_blank"> Click here for Tableau Visualization of the project</a>


<h2>Abstract</h2>  
In this project, my primary objective is to guide Adidas in leveraging its existing strengths to further solidify its position as a leader in sportswear. By gathering data-driven insights, my strategy focuses on identifying and enhancing areas where Adidas already excels, aiming not just to sustain but to amplify its sales performance. Through strategic analysis and actionable recommendations, the goal is to empower Adidas to capitalize on its competitive advantages, ensuring sustained leadership and growth in the sportswear industry. This summary highlights strategic opportunities for Adidas to reinforce its market leadership by adapting to shifts in consumer behaviors and leveraging its strengths. The transition towards online shopping, emerging from the Covid-19 pandemic, offers a key area for Adidas to expand its digital footprint and outpace competitors. Analysis of sales patterns reveals potential for targeted marketing strategies, focusing on optimizing sales on specific days of the week and throughout the year to maintain consumer engagement. Demographic insights suggest tailoring product lines to meet the distinct preferences of men and women, enhancing Adidas's relevance and appeal. Additionally, focusing on high-performing regions like New York, California, and Florida, and strengthening partnerships with key retailers like WestGear and Footlocker, can boost Adidas's sales and brand loyalty. This approach underscores the importance of agility and customer-centric strategies in cementing Adidas's competitive edge.

<h3>Problem Statement:</h3>

Adidas, a global leader in the sportswear industry, has collected comprehensive data on sales across various channels in the United States during the years 2020 and 2021. The company is eager to gain valuable insights from this dataset to inform strategic decisions and enhance its market position. The primary objective is to uncover trends, patterns, and key performance indicators (KPIs) that can help Adidas better understand its sales dynamics in the US market. Adidas corporate executives, Senior Management, Financial analysts and Investors are the primary stakeholders as they closely monitor the sales performance to assess the company's financial health and make investment decisions.

<h3>Project Scope:</h3>

1. **Data Collection:**

- The dataset includes sales data from Adidas stores, online platforms, and third-party retailers across the United States.
- Information spans the years 2020 and 2021, providing a comprehensive view of sales performance over this period.

2. **Key Questions to Address:**

- Identify and analyze sales trends for different product categories.
- Evaluate the impact of external factors (e.g., economic conditions, global events) on sales.
- Explore seasonality effects on sales and identify peak periods.
- Compare the performance of various sales channels, including Adidas stores, online platforms, and third-party retailers.

3. **KPI's:**

- Total Revenue
- Year-over-Year Growth
- Operating margin

4. **Recommendations and Actionable Insights:**

- Provide actionable insights and recommendations based on the analysis.
- Suggest potential areas for improvement or optimization in the sales strategy.


<h3>OUTCOMES AND SUMMARIZED INSIGHTS:</h3>
The insights summarized here are derived from the data queries presented in this document:

-There was a notable decrease in in-store sales for Adidas in 2021 compared to 2020, while online sales saw an increase in their share of total sales in 2021. This trend likely stemmed from the onset of the Covid-19 pandemic, which shifted consumer purchasing habits. Capitalizing on this trend, Adidas can enhance its online presence and digital marketing strategies, giving an edge over competitors slower to adapt to digital transformations.

-Analyzing weekly sales patterns, it was observed that Fridays were the peak sales days in 2020, accounting for 16.39% of sales. However, in 2021, there was a shift with Tuesdays (15.3%) and Thursdays (15.32%) emerging as the days with higher sales. This shift, possibly related to the increased preference for online shopping, opens up strategic considerations for the marketing team to either target lower-sales days for boosting revenue or capitalize on the already high-sales days.

-Seasonal sales trends indicated a dip towards the end of the year (November-December). The beginning of 2020 experienced higher sales, which declined towards the end of the year, likely due to the economic impact of the Covid pandemic. In contrast, 2021 showed more consistent sales throughout the year, with minor dips in February and November. This approach can maintain customer engagement even during typically slower months, setting Adidas apart from competitors who may not leverage seasonality as effectively.

-Demographically, men contributed more to Adidas Shoe sales, making up 40.2% of total sales, with a particular preference for streetwear shoes (23.2%). In comparison, women were more inclined towards purchasing Adidas Apparel, representing 19.8% of all sales. Adidas can more effectively meet customer demands. Offering a more focused range of streetwear shoes for men and expanding the apparel line for women can cater precisely to consumer needs, giving Adidas a competitive edge in understanding and satisfying market segments.

-The top three states in terms of units sold for Adidas products were New York, California, and Florida, indicating strong market presence in these regions. Adidas can concentrate its marketing and distribution efforts in these states. Customizing strategies to suit regional preferences and consumer behaviors in New York, California, and Florida can increase market penetration and brand loyalty, positioning Adidas ahead of competitors in these key markets.

-The retail partners WestGear and Footlocker generated significantly higher revenue for Adidas, highlighting their importance in the brand's retail strategy. Strengthening relationships with high-performing retailers like WestGear and Footlocker can lead to more collaborative marketing efforts and exclusive product launches, enhancing brand visibility and sales. This relationship not only boosts Adidas’s sales but also provides a competitive edge through strong retail partnerships.







<h3>Adidas queries</h3>

The following queries take into account the KPIs for this project and intend to gather insight based on said KPIs in order to address Key Questions.
```
SELECTSUM(Total\_Sales)AS Total\_Revenue FROM adidas\_us
```

<img src="./Adidas_Sales_Report/Total_Revenue (1.0).jpg"/>


- Right away I wanted to know the Total Revenue so I started with the simple SUM Query. This number could give me a little bit more information about other aspects later on.





– Created a CTE that will help get the date in a format that can be worked with, and if needed the CTE can be modified for other purposes later.
```
WITH SalesCTE AS (

SELECT

Id,

State,

City,

Product,

Units\_Sold,

Total\_Sales,

Operating\_Profit,

Operating\_Margin,

Sales\_Method,

Invoice\_Date,

YEAR(Invoice\_Date)AS Invoice\_Year,

MONTH(Invoice\_Date)AS Invoice\_Month,

DAY(Invoice\_Date)AS Invoice\_Day

FROM adidas\_us

)

SELECT\*

FROM SalesCTE
```

<img src="./Adidas_Sales_Report/Results Img/CTE (2.0).jpg"/>



- I decided to create a CTE that I can work with from the beginning because I can slowly build it up based on the progress of the project. A CTE allows me to keep the code fairly clean, while also "creating" "temporary tables" that have different information than the original one. If a project has multiple tables to work with, this simplifies queries that involve multiple joins and is less confusing if worked in the beginning.



```
WITH SalesCTE AS (

SELECT

Id,

State,

City,

Product,

Units\_Sold,

Total\_Sales,

Operating\_Profit,

Operating\_Margin,

Sales\_Method,

Invoice\_Date,

YEAR(Invoice\_Date)AS Invoice\_Year,

MONTH(Invoice\_Date)AS Invoice\_Month,

DAY(Invoice\_Date)AS Invoice\_Day

FROM adidas\_us

)
```

-- Selecting and aggregating for **2021 and 2020** (Units/Sales)
```
SELECT

Invoice\_Year,

SUM(Units\_Sold)AS TotalUnitsSold,

SUM(Total\_Sales)AS TotalSales

FROM SalesCTE

WHERE Invoice\_Year IN(2021, 2020)

GROUPBY

Invoice\_Year

ORDERBY

Invoice\_Year;
```

<img src="./Adidas_Sales_Report/Results Img/Total_Year (3.0).jpg"/>


- Following up, I wanted to know the total units sold in each year. This will allow me to later move on into revenue by year and have this piece of information that tells us about our KPIs, as well as helping us analyze trends and seasonality.



```
WITH SalesCTE AS (

SELECT

Id,

State,

City,

Product,

Units\_Sold,

Total\_Sales,

Operating\_Profit,

Operating\_Margin,

Sales\_Method,

Invoice\_Date,

YEAR(Invoice\_Date)AS Invoice\_Year,

MONTH(Invoice\_Date)AS Invoice\_Month,

DAY(Invoice\_Date)AS Invoice\_Day

FROM adidas\_us

)

SELECT

Invoice\_Year,

Sales\_Method,

SUM(Units\_Sold)AS Total\_Units\_Sold

FROM SalesCTE

GROUPBY

Invoice\_Year,

Sales\_Method

ORDERBY

Invoice\_Year,

Sales\_Method;
```

<img src="./Adidas_Sales_Report/Results Img/Units_Sold_by_Method (4.0).jpg"/>

- Here I wanted to Understand a little bit more of what Sales Methods were most popular yearly. We can see that the Outlet Sales for 2020 represent 47.29% of all sales in that year compared to 31.29% in 2021. While Online Sales represented 18.83% of all sales in 2020, in 2021 this number went to 42.25%. In-Store Sales represent 33.86% of all sales in 2020, in 2021 26.45%.









4.WITH SalesCTE AS (
```
SELECT

Id,

State,

City,

Product,

Units\_Sold,

Total\_Sales,

Operating\_Profit,

Operating\_Margin,

Sales\_Method,

Invoice\_Date,

YEAR(Invoice\_Date)AS Invoice\_Year,

MONTH(Invoice\_Date)AS Invoice\_Month,

DAY(Invoice\_Date)AS Invoice\_Day

FROM adidas\_us

)

-- Selecting and aggregating by **weekday**

SELECT

DATENAME(WEEKDAY, Invoice\_Date)ASWeekday,

SUM(Units\_Sold)AS Total\_Units\_Sold,

SUM(Total\_Sales)AS Total\_Revenue

FROM SalesCTE

GROUPBY

DATENAME(WEEKDAY, Invoice\_Date)

ORDERBY

MIN(Invoice\_Date);
```

<img src="./Adidas_Sales_Report/Results Img/Total_Weekday (5.0).jpg"/>


- Here I was a little bit curious about what days sell more units, and if by any chance there was a day that had numbers that could give us insights. Here are the following %.

-Monday 13.15%--------------------------------(2021)Monday: 12.58%

-(2020)Tuesday 14.44%-----------------------------(2021)Tuesday: 15.3%

-(2020)Wednesday 14.39%------------------------(2021)Wednesday: 14.02%

-(2020)Thursday 13.58%---------------------------(2021)Thursday: 15.32%

-(2020)Friday 16.39%-------------------------------(2021)Friday: 15.15%

-(2020)Saturday 13.37%----------------------------(2021)Saturday: 13.87%

-(2020)Sunday 14.65%------------------------------(2021) Sunday: 13.74%

-We can see that there were more sales on Friday during 2020, but on 2021 there was more sales on Tuesday and Thursday. The explanation could be related to the transition from In-store/Outlet, to Online that happened in those years.




```
WITH SalesCTE AS (

SELECT

Id,

State,

City,

Product,

Units\_Sold,

Total\_Sales,

Operating\_Profit,

Operating\_Margin,

Sales\_Method,

Invoice\_Date,

YEAR(Invoice\_Date)AS Invoice\_Year,

MONTH(Invoice\_Date)AS Invoice\_Month,

DAY(Invoice\_Date)AS Invoice\_Day

FROM adidas\_us

)
```
-- Selecting and aggregating data by month
```
SELECT

Invoice\_Year,

Invoice\_Month,

SUM(Units\_Sold)AS TotalUnitsSold,

SUM(Total\_Sales)AS TotalSales

FROM SalesCTE

WHERE Invoice\_Year IN(2021, 2020)

GROUPBY

Invoice\_Year,

Invoice\_Month

ORDERBY

Invoice\_Year,

Invoice\_Month;
```

<img src="./Adidas_Sales_Report/Results Img/Total_Month (6.0).jpg"/>
<img src="./Adidas_Sales_Report/Results Img/Total_Month (6.1).jpg"/>



- I was also curious about splitting it by month because it allows us to understand how the trend works in relation to seasonality. Here are the %

-January 10.45%(2020)-----------------------8.89% (2021)

-February 8.18%(2020)-----------------------7.74% (2021)

-March 10.15%(2020)------------------------7.14% (2021)

-April 11.83%(2020)---------------------------8.01% (2021)

-May 7.7%(2020)------------------------------8.87% (2021)

-June 3.51%(2020)----------------------------8.16% (2021)

-July 8.26%(2020)------------------------------8.95% (2021)

-August 13.47%(2020)------------------------9.69% (2021)

-September 9.97%(2020)---------------------9.04% (2021)

-October 6.52%(2020)------------------------7.57% (2021)

-November 5.44%(2020)---------------------7.40% (2021)

-December4.44%(2020)-----------------------8.49% (2021)

The information gathered based on months is especially interesting in 2020 where we see in the months from January to May, where we see stability in the % of sales, but afterward we start to see big variability on the sales each month. In this case is easy to interpret that since the COVID pandemic started in the beginning of 2020, the spending was normal at the beginning of the year, but later on doubts about general economic stability could have hurt the sales. In 2021 when the sales were around 4 times larger than in 2020, the economic situation was also more stable, which could potentially explain why the sales were also stable.


```

WITH SalesCTE AS (

SELECT

Id,

State,

City,

Product,

Units\_Sold,

Total\_Sales,

Operating\_Profit,

Operating\_Margin,

Sales\_Method,

Invoice\_Date,

YEAR(Invoice\_Date)AS Invoice\_Year,

MONTH(Invoice\_Date)AS Invoice\_Month,

DAY(Invoice\_Date)AS Invoice\_Day

FROM adidas\_us

)
```
-- Its possible to see the following data only for 2020 and 2021, just adding WHERE YEAR()= in between FROM and GROUP BY, and after the FORM in the / (the difference in year didn't drive into any insights)
```
SELECT Product,SUM(Total\_Sales)\*100/(SELECTSUM(Total\_Sales)from SalesCTE)AS PCT

FROM SalesCTE

GROUPBY Product

ORDERBY PCT DESC;
```


<img src="./Adidas_Sales_Report/Results Img/PCT_by_Product (7.0).jpg"/>

- This time I'm jumping directly into what products drive the biggest revenue (% PCT) and we can see that generally speaking Men's Street Footwear drives more revenue than others, followed by Women's Apparel and Men's Athletic Footwear. This indicates that Men tend to focus more on the Shoe aspect (especially Street Footwear), and Women tend to use Adidas more as an apparel brand.





```
WITH SalesCTE AS (

SELECT

Id,

State,

City,

Product,

Units\_Sold,

Total\_Sales,

Operating\_Profit,

Operating\_Margin,

Sales\_Method,

Invoice\_Date,

YEAR(Invoice\_Date)AS Invoice\_Year,

MONTH(Invoice\_Date)AS Invoice\_Month,

DAY(Invoice\_Date)AS Invoice\_Day

FROM adidas\_us

)
```

--Added WHERE YEAR()= in between FROM and Group as well as after the "from Sales CTE" in the select to get results only from 2021 and 2020.

```
SELECTTOP 5 State,SUM(Total\_Sales)\*100/(SELECTSUM(Total\_Sales)from SalesCTE)AS PCT

FROM SalesCTE

GROUPBYState

ORDERBY PCT DESC;
```
<img src="./Adidas_Sales_Report/Results Img/PCT_by_State (8.0).jpg"/>
<img src="./Adidas_Sales_Report/Results Img/PCT_by_State (8.1).jpg"/>
<img src="./Adidas_Sales_Report/Results Img/PCT_by_State (8.2).jpg"/>

```
SELECT Retailer,

SUM(CASEWHENYEAR(Invoice\_Date)= 2020 THEN Total\_Sales ELSE 0 END)AS Total\_Revenue\_2020,

SUM(CASEWHENYEAR(Invoice\_Date)= 2021 THEN Total\_Sales ELSE 0 END)AS Total\_Revenue\_2021

FROM adidas\_us

WHEREYEAR(Invoice\_Date)IN(2020, 2021)

GROUPBY Retailer

ORDERBY Total\_Revenue\_2021 DESC;
```

<img src="./Adidas_Sales_Report/Results Img/Total_Retailer (9.0).jpg"/>

***FOR THE COMPLETE INSIGHTS AND SUMMARY REFER TO THE BEGINNING OF THIS md FILE AND TO THE TABLEU PUBLIC CHART LINKED IN THE REDME FILE***
