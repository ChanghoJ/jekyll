---
name: Homework 8 Buildings in Champaign
tools: [Python, HTML, vega-lite]
image: assets/pngs/cars.png
description: This is a "showcase" project that uses vega-lite for interactive viz!
custom_js:
  - vega.min
  - vega-lite.min
  - vega-embed.min
  - justcharts
---

# Topic: Champaign Building data visualization

This project is for UIUC IS 445 Data Visualization Homework 8. 

The overall theme of the visualization is showing relationship between buildings in Champaign, Illinois that charts can adjusted by users.

Dataset used for the worked is [building_inventory.csv](https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv), dataset that contains building related data from 18th century to year 2019.

## Visualization 1: Line chart of building contructed by year

<vegachart schema-url="{{ site.baseurl }}/assets/json/line_chart.json" style="width: 100%"></vegachart>

For the first visualization, I created a line chart that showing how many buildings contructed by year. 

For encoding, I choose "Year Consturcted" column as the x-axis on the chart. Before move into encoding, I filtered 0 value on "Year Consturcted" for remove discontinuity on chart. Then, "Year Consturcted" converted to datetime in pandas before move to Altair, but seems discontinuity of the time in data returning an empty chart when I set "Year Consturcted" to Time, or "Year Consturcted:T". Therefore, I decided to treat "Year Consturcted" as an ordinal, past to present. For y-axis, I chose "Year Acquired" column to show overall quantity of building by year ("count(Year Acquired)"). 

Then, I applied filter that user can adjust range of time shown on the chart. User can choose two datetime value from dropdown box to set the time range on the chart. 
The theme of the visualization is similar with the Homework 7, but the discontinuity of time enforced me to change x value as ordinal on Altair. In consequence, the line chart becomes longer but more specific. 
Also, the interaction added for adjusting the date range by selecting dates in two dropdown boxes, which there were no such things in the Homework 7. To add the interactions, I had to create year range variable, start year variable, end year varaible, and apply them to .transform_filter for FieldRangePredicate and .add_params for users can actually choose parameter from dropdown box. I also added strokeWidth_slider variable and strokeWidth_var variable to add slider that can change the thickness of line on the line chart.

The date selection from the visualization may help users to limit their time frame to check rise and fall of constructed buildings. For the strokewidth slider, users may adjust to avoid line to covering data by line's thickness.


## Visualization 2: Bar chart of buildings in Congress District by contructed buildings

<vegachart schema-url="{{ site.baseurl }}/assets/json/bar_chart.json" style="width: 100%"></vegachart>

For the second visualization, I created a bar chart that showing how many buildings contructed by Congress District. 

For encoding, I choose "Congress Dist" column as the x-axis on the chart. Before move into encoding, again, I filtered 0 value on "Year Consturcted" for date interactivity later. Then, "Year Consturcted" converted to datetime as mentioned in previous visualization. Since Congress Districts are numbers but categorical values that referring specific areas in Champaign, I decided to treat "Congress Dist" as an nominal, or "Congress Dist:N". For y-axis, I chose "Year Constructed" column to show overall quantity of building by year ("count(Year Constructed)"). In addition, I add color scheme by "Bldg Status" to show visual quantity of "Abandoned", "In Progress", and "In Use" buildings by Congress District. 

Then, I applied filter that user can adjust range of time shown on the chart, just like the previous visualization. User can choose two datetime value from dropdown box to set the time range on the chart. 
Only parts that the visualization is bar chart and has color scheme for "Bldg Status" is similiar with the Homework 7. Unlike the bar chart from Homework 7, this bar chart showing the relatoinship between contructed buildings and Congress District unlike the previous cahrt showed building status by constructed building. Also the bar chart has color distinction within each bar to show number of buildings by status by each district. 
To add the interactions, I had to create year range variable, start year variable, end year varaible, and apply them to .transform_filter for FieldRangePredicate and .add_params for users can actually choose parameter from dropdown box, just like the previous visualization.

The date selection from the visualization may help users to change their time frame to check rise and fall of constructed buildings within Congress District, and users even can check which Congress District existed in a selected time frame. Users may also check building status as they change the time range.


## Data and Python notebook

<div class="left">
{% include elements/button.html link="https://raw.githubusercontent.com/UIUC-iSchool-DataViz/is445_data/main/building_inventory.csv" text="The Data" %}
</div>

<div class="right">
{% include elements/button.html link="https://github.com/ChanghoJ/jekyll/tree/main/python_notebooks/Workbook.ipynb" text="The Analysis" %}
</div>