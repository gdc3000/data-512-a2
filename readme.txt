Exploring Bias in Data through the Wikipedia ORES API
Author: Geoff Coyner

Overview
This project was an attempt to understand bias on Wikipedia by looking at Wikipedia article quality by country for articles related to politicians. This readme walks through how this analysis was conducted including the steps in gathering the data or explains where this information can be found in the github repo. At the end of this readme is a reflection outlining findings from the analysis. 

All data used is publicly available through the Wikimedia foundation APIs or through the Population Research Bureau. An addition goal of this project is to practice and show-case open scientific research best practices.

Getting Started
These instructions will get you up and running and explain the project, data and relevant files in more detail. The outputs of the data processing step is included in the repo and the final analysis results can be seen in the Jupyter notebook in the repo (each file in the repo is described in more detail below. The entire workflow from data acquisition, processing and acquisition can be reproduced through the included Jupyter notebook.

Before attempting to reproduce this work, please ensure that Jupyter notebooks is installed on local machine or accessible online and Python v3.6 is installed where appropriate.

Contents of this repo
This repo contains the following files:
	• 1 Jupyter notebook file called "hcds_a2_bias" outlining in detail the steps of data acquisition, processing and analysis. At the conclusion of the analysis step, tables showing the top 10 countries and bottom 10 countries in terms of: (1) proportion of politician articles per capita and (2) proportion of high quality politician articles to total count of politician articles.
	• 1 .csv file called "final_data_a2" showing the output of the data acquisition and processing steps. This file shows all relevant data used in the analysis step in one table. The columns of this table are: country, article_name, revision_id, article_quality, population.
	• 1 Readme file
	• 1 License file

Relevant Documentation and Source Data
This project is based on  publicly available data about politician related articles, the ORES API and the Population Reference Bureau. This is described in more detail below.

A table containing the politician articles extracted from wikipedia is made available under the 
CC-BY-SA 4.0 license by Oliver Keyes: https://figshare.com/articles/Untitled_Item/5513449.

Information about the ORES API which is used to rate article quality is here: https://www.mediawiki.org/wiki/ORES

The population data is made available in csv format here and represents population estimates from mid-2015 (or slightly early in some cases): http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14.

Additional documentation about the primary sources of the population data is described here: http://www.prb.org/DataFinder/About/International-Data-in-DataFinder.aspx.

Limitations of the data
Some countries are found in the population reference bureau data and not in the Wikipedia article data and vice versa. These non-overlapping countries are excluded from the final analysis. Articles where a valid ORES quality score was not available are also excluded from this analysis, although the impact of this limitation is very minimal (only 2 articles seem to be affected).

Licenses
This project is licensed under the MIT License. See the license file for more details. 

The Wikimedia Foundation makes their data available under a Creative Commons Attribute-ShareAlike License.

The Population Reference Bureau makes their data available with a copyright notice.

Python and python standard library packages are available under a modified GPL-compatible license. The python package requests is available under an Apache license, version 2.0. The pandas package is available under the 3-clause BSD license. NumPy is licensed under the BSD license.

Reflections on the project
The results of this project surprised me somewhat. One observation is that when looking at the proportion of high quality articles by population, the overall population of the country appears to be a huge driver of how countries rank. For example, China and India show up towards the bottom of the list, whereas Nauru is at the top. This intuitively makes sense since each country has only a small number of prominent, national leaders regardless of population. On the other hand, one bias this suggests is that articles about local politicians on Wikipedia might be underrepresented even if these figures represent a large population. 

When looking at the proportion of high-quality politician articles as a proportion of all articles, one pattern I observe is that no English speaking countries are represented amongst the bottom 10 ranked countries. For example, Belgium and Switzerland each have over 400 articles, with zero "high quality" articles. This may reflect their highest quality articles being in French (or German or Dutch) instead of English. Perhaps this suggests that highest quality articles about politicians in many countries have not been translated completely to English. I was not surprised to countries like North Korea, Saudi Arabia and United States on the top 10 list, since these countries are frequently the focus of western media. This suggests a unsurprising "home bias" in terms of which articles English-speaking editors choose to write.

In addition to raising my awareness about biases on wikiped, this project also helped develop my technical skills, specifically my comfort with Python. Scraping web data with Python isn't something I've practiced a whole lot and this assignment was helpful with this. It also stretched me in terms of quickly manipulating data using pandas dataframes.

This project also raised questions related to machine learning in general. The wikipedia ORES API is more transparent than most machine learning APIs in the sense that it provides percentage estimates associated with each quality level. On the other hand, it still very hard to tell how various features were weighted in assessing a specific article's quality. Looking at the top 10 and bottom 10 results of each was a great example of a "gut check" that it might be smart to perform when using someone else's machine learning model. This is especially true when the results will be used to make consequential decisions or presented to a skeptical or non-technical audience, since it can be very difficult to perform a follow-up "explanatory" analysis if problems or questions arise.
