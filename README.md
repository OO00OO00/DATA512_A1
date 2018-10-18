***************************
DESCRIPTION:
The notebook, "hcds-a1-data-curation.ipynb", attempts to reproduce the methods used to create the plot by Thompson on Wikipedia traffic between January 1st, 2008 and September 1st, 2017:
	https://wiki.communitydata.cc/upload/4/48/En-wikipedia_traffic_200801-201709_thompson.png

The underlying Wikipedia traffic data is downloaded directly from two Wikimedia APIs as json objects: Wikimedia Legacy API (using data between 2007-12-01 and 2016-08-01, incl.) & Wikimedia Pageviews API (using data between 2015-07-01 and 2018-09-01, incl.). From the Legacy API, the traffic data is collected from desktop and mobile users. From the Pageviews API, the traffic data is collected from desktop, mobile app, and mobile web users. In total, 5 json objects are created at the end of the data acquisition phase.

The json objects are transformed into separate pandas dataframes and appended to a final dataframe (called wikipedia_traffic) having a common date range among all datasets. All json objects and the wikipedia_traffic dataframe are exported.

Lastly, the Thompson plot is reproduced and displayed in the notebook.	

***************************
COMMENTS:
- This notebook doesn't exactly reproduce the Thompson plot because it includes an additional year of data. 

- This reproduction shows that the Thompson plot omitted two months of Legacy API data: 2007-12 & 2016-08. Presumably, Thompson excluded these months because the traffic data was about an order of magnitude smaller than the recent trend up until those selected months. If these months were included, the reproduced Thompson plot would have jarring spikes for Legacy API data that distract from the overall trends.

- A key difference between the two Wikimedia APIs is in their handling of spider/bot traffic. The Legacy API makes no distinction between organic user traffic and spider/bot traffic; however starting on 2015-05, the Pageviews API eliminated spider/bot traffic from its views metric.

***************************
ATTRIBUTIONS:
Relevant API documentation:
	Wikimedia Legacy Pagecounts API, https://wikitech.wikimedia.org/wiki/Analytics/AQS/Legacy_Pagecounts
	Wikimedia Pageviews API, https://wikitech.wikimedia.org/wiki/Analytics/AQS/Pageviews

URL of Wikimedia Foundation REST API terms of use:
	https://www.mediawiki.org/wiki/REST_API#Terms_and_conditions

The Wikimedia API data is made available via the Creative Commons Share-alike license.
	
***************************
SCHEMA OF en-wikipedia_traffic_200801-201809.csv

Column					|	Value			|	Data Type
-----------------------------------------------------------
year					|	year, YYYY		|	integer
month					|	month, MM		|	integer
pagecount_all_views		|	traffic volume	|	integer
pagecount_desktop_views	|	traffic volume	|	integer
pagecount_mobile_views	|	traffic volume	|	integer
pageview_all_views		|	traffic volume	|	integer
pageview_desktop_views	|	traffic volume	|	integer
pageview_mobile_views	|	traffic volume	|	integer