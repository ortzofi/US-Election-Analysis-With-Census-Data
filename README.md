# US-Election-Analysis-With-Census-Data
Elections in the US are held for government officials at the federal, state, and local level. Depending on the level, elections take place every two, four, or six years. The two major political parties are the Democratic Party and the Republican Party. American election results have significant implications for the US and the whole world.

This project focuses on analyzing the 2020 presidential election and predicting voting behavior in the State of New York. Voting behavior in the US is affected by ethnicity, region, income, education, and many more factors. For this purpose, we train several regression models that would predict the share of vote each major party would receive. As an extra, we will try to forecast voting behavior in other states using the most successful model.

<img width="1236" alt="NY Map Photo" src="https://user-images.githubusercontent.com/96059174/201495914-c2d41d2a-b41c-459e-9afa-728cf5b58874.png">

## Data
Our model will draw on the US census data for the State of New York. Nonetheless, this analysis can be replicated with any state (even all of the US) and any geographical entity supported by the Census Bureau.

While most similar works include a statewide or countywide analysis, here we focus on smaller geographic entities - census tracts. Census tracts are small statistical subdivisions of a county that average about 4,000 inhabitants. They are subdivided only into block groups and census block. You can read more about geographic entities in the US here.

To create the dataset, I used the 2016-2020 American Community Survey data that I had taken from the US Census Bureau using their API. Then, I merged it with the 2020 election results by census block groups dataset that was published by Harvard University. The creation of the dataset is documented in the Data Preparation notebook.

## So why is a tract-level analysis important?
The analysis of voting behavior of citizens, often takes up a huge amount of time by political parties in an attempt to realize where the support base for that party stands. As such, there are two main usecases:

1) Political campaigns: Census tracts are smaller than counties or congressional districs. Analyzing them can therefore help political candidates target more accurate geographies. For instance: identifying more competitive tracts inside "swing districts" where candidates should allocate more resources in order to guarantee victory.

2) Redistricting: States have to redraw the boundaries of congressional and state legislative districts. It happens every 10 years, after the decennial census, to reflect the changes in population. States gain or lose seats in Congress based on the census. Practically, this is often a political process in which district lines can be redrawn to favor one party over the other and protect incumbent elected officials. The intentional distortion of a map of political districts to give one party an advantage is called gerrymandering. This project is relevant because mapmakers use similar tools and predictions for gerrymandering. Others use such tools and analyses to challenge redrawn maps as illegal gerrymanders in court.
