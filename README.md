# US-Election-Analysis-With-Census-Data
Elections in the US are held for government officials at the federal, state, and local level. Depending on the level, elections take place every two, four, or six years. The two major political parties are the Democratic Party and the Republican Party. American election results have significant implications for the US and the whole world.

This project focuses on analyzing the 2020 presidential election and predicting voting behavior in the State of New York. Voting behavior in the US is affected by ethnicity, region, income, education, and many more factors. For this purpose, we train several regression models that would predict the share of vote each major party would receive. As an extra, we will try to forecast voting behavior in other states using the most successful model.

Please look at "NY_Election_Results_Visualization.html" for the interactive Folium map.

<img width="1236" alt="NY Map Photo" src="https://user-images.githubusercontent.com/96059174/201495914-c2d41d2a-b41c-459e-9afa-728cf5b58874.png">

## Data
Our model will draw on the US census data for the State of New York. Nonetheless, this analysis can be replicated with any state (even all of the US) and any geographical entity supported by the Census Bureau.

While most similar works include a statewide or countywide analysis, here we focus on smaller geographic entities - census tracts. Census tracts are small statistical subdivisions of a county that average about 4,000 inhabitants. They are subdivided only into block groups and census block. You can read more about geographic entities in the US here.

To create the dataset, I used the 2016-2020 American Community Survey data that I had taken from the US Census Bureau using their API. Then, I merged it with the 2020 election results by census block groups dataset that was published by Harvard University. The creation of the dataset is documented in the Data Preparation notebook.

## So why is a tract-level analysis important?
The analysis of voting behavior of citizens, often takes up a huge amount of time by political parties in an attempt to realize where the support base for that party stands. As such, there are two main usecases:

1) Political campaigns: Census tracts are smaller than counties or congressional districs. Analyzing them can therefore help political candidates target more accurate geographies. For instance: identifying more competitive tracts inside "swing districts" where candidates should allocate more resources in order to guarantee victory.

2) Redistricting: States have to redraw the boundaries of congressional and state legislative districts. It happens every 10 years, after the decennial census, to reflect the changes in population. States gain or lose seats in Congress based on the census. Practically, this is often a political process in which district lines can be redrawn to favor one party over the other and protect incumbent elected officials. The intentional distortion of a map of political districts to give one party an advantage is called gerrymandering. This project is relevant because mapmakers use similar tools and predictions for gerrymandering. Others use such tools and analyses to challenge redrawn maps as illegal gerrymanders in court.

## Results

Several regression models were trained and tested on the New York data. Those include linear regression, random forest regression, XGBoost, and LightGBM. The gradient boosting regression models achieved the best performance, with LightGBM outperforming XGBoost by a small margin.

Model scores:
<img width="833" alt="Screen Shot 2022-11-13 at 0 00 38" src="https://user-images.githubusercontent.com/96059174/201496220-3dfc015d-2e50-4e3d-8590-ba295029564f.png">

Feature importance:
![Feature Importance](https://user-images.githubusercontent.com/96059174/201496233-76a76b9a-2c32-4782-a0af-5f75959c11ce.png)

## Conclusion

While the model performance in New York was reasonable, we have seen that it is not really generalizable to other states. As each state has a different socio-demographic composition and voting behavior, it was rather expected that a model that had been trained on New York data would perform poorly in this task. In addition, there is a clear bias towards higher percentages of Democratic vote — probably due to the fact that New York is a blue state. For these reasons, the results on California were not good, but also not terrible; the results on Texas were horrible; and Florida was somewhere in between. Choosing blue states with a similar socio-demographic composition to New York for prediction could have yielded better results.

There is much more one can do to analyze and predict voting behavior in the US: using census data with different geographic entities, analyzing more states, or drawing on more election results from previous years and different levels (president, Senate, House of Representatives, etc.) to analyze trends and differences.
