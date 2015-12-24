This page provides background informaiton on Tableau software.

Tableau is a complete Data Analytics platform enabling everyone to gain
insights from raw data. It makes working with data universally accessible.

Tableau clients running on Windows and Macs are used to create ".viz" files which define visualization display settings.

Tableau software consists of several separately installed components
downloaded from separate URLs.

<a href="#TableauDesktop">Tableau Desktop</a> Personal and Pro editions are licensed at $999 and $1999 per year.

http://www.tableau.com/products/reader

| Date | Component - Version | Size |
| ------ | ----------------------- | -------: |
| 2015-12-07 | TableauReader-9-2-0.dmg | 190.2 MB |
| 2015-12-01 | TableauPublic-9-2-0.dmg | 185.5 MB |
| 2015-07-20 | TableauDesktop-9.0.4.dmg | 183.7 MB |

QUESTION: You don't need to instal Public or Reader if you have Deskstop installed?

After installation on a Mac, select a client to invoke from within Finder. 
Pull down the Go menu for Applications or press Shift+command+A.

<a id=“TableauPublic”>
## Tableau Public</a>

Tableau Public is meant for individuals to show off visualizations of public data sets
(and blogging about them) in Tableau's social sharing site
https://public.tableau.com/ 
This is much like what Adobe offers.

"VIZ of the day" from the Tableau Public sharing website is highlighted on the landing page of Tableau Desktop.

https://public.tableau.com/s/resources
announce monthly webinars and provides free on-line training videos also published under
<a target="_blank" href="https://www.youtube.com/channel/UCfAoXs9ej01qqIj6ti456tg/videos">
Tableau Smith on YouTube</a>, which has more videos than on the website.

QUESTION: How about videos instead of text blogs? That would enable us to describe changes over time.

Vizzes by bloggers can be published on other sites, such as:

 * http://blog.numbersbox.com/2015/06/global-obesity-were-getting-bigger.html


<a id=“StoreData”>
## Store Data Locally</a>

0. Click Excel under "Connect ... To a file".

  On the Mac, the "Datasources" folder is shown.
  It is under the "My Tableau Repository" folder within your user's Documents folder
  created during client installation.
  
  There is a separate folder for each version of Tableau (9.2, 9.0, etc.) because 
  data structures often change with each new version.

0. Click on a version, then your locale (en_US_US).

   File types <a target="_blank" href="http://onlinehelp.tableau.com/current/pro/online/mac/en-us/help.htm#environ_filesandfolders.html">explained here</a>:

   .tds data source files (as explained <a target="_blank" href="https://community.tableau.com/external-link.jspa?url=http://kb.tableausoftware.com/articles/knowledgebase/export-data-connection">here</a>) are like shortcuts containing information needed to just connect to the data sources, such as data source type, location, and custom fields. 

   .tde extract files (explained <a target="_blank" href="http://onlinehelp.tableau.com/current/pro/online/mac/en-us/help.htm#extracting_data.html">here</a>) are a local copy of an entire data source or its subset.
   
   .tdsx Packaged Data Source files contains all the information in the Data Source (.tds) file as well as any local file data sources (Excel, Access, text, and extracts). Packaged means a single zipped file for easier sharing a data source with people who may not have access to the original data that is stored locally on your computer.

   .twbx workbook files (as explained <a target="_blank" href="https://community.tableau.com/external-link.jspa?url=http://onlinehelp.tableausoftware.com/current/pro/online/en-us/help.htm#save_savework_packagedworkbooks.html">here</a>) contain one or more worksheets, plus zero or more dashboards and stories.

   .twb is the native workbook and does not include any data, which is why you always need to post a packaged workbook.
   
0. Pull data file from a website.

0. PROTIP: Store all Excel data files locally in the same Excel folder. Store all Microsoft Office Access files in an Access folder.

<a id=“LoadData”>
## Load Data</a>

The Pro version connects to Tableau Server for web-based analytics
using a lot more different data sources under the <strong>Connect</strong> section of Desktop:

<img width="676" alt="tableau data sources" src="https://cloud.githubusercontent.com/assets/300046/11996554/90f17590-aa22-11e5-8abd-5dec3b430966.png">

0. Click on Excel to open your Excel data folder.
0. Drag one of the Sheets (table such as orders) to the canvas.
0. Drag another Sheet (such as Returns) to the canvas.

 Tableau automatically suggests a join type:

 <img width="400" alt="tableau joins" src="https://cloud.githubusercontent.com/assets/300046/11996601/ba10d618-aa23-11e5-8c64-44044d1fa73e.png">

0. Because data is now loaded within Tableau, hover over a heading to Rename the heading or change its type.

 <img width="207" alt="tableau heading options" src="https://cloud.githubusercontent.com/assets/300046/11996656/eca2f51a-aa24-11e5-9e3f-db7db424a206.png">

0. Click on the data type under the heading name to change it.

 <img width="130" alt="tableau data type options" src="https://cloud.githubusercontent.com/assets/300046/11996668/3f0d7fbe-aa25-11e5-8057-ef16bf34f4aa.png">

0. If a column contains multiple fields, split them into sub-columns:

 <img width="220" alt="tableau data split options" src="https://cloud.githubusercontent.com/assets/300046/11996699/ff0d9ed4-aa25-11e5-8411-c8281ace509e.png">

<a id=“Dimensions”>
## Dimensions</a>

One of the amazing features of Tableau is it enables users to create charts just by dragging and dropping.

<img alt="tableau lines separated by year" src="https://cloud.githubusercontent.com/assets/300046/11996255/69a883b2-aa1c-11e5-8ac6-19168d517124.png">




<a id=“ChartTypes”>
## Chart Types in Tableau</a>

<img width="236" align="right" alt="tableau chart types" src="https://cloud.githubusercontent.com/assets/300046/11996347/f9ffb29a-aa1d-11e5-930a-ed789c88b939.png">

Tableau provides a rich variety of chart types.

Tableau recommends a chart type based on the data set loaded when "Show Me" is clicked.

The value of various types are described in the video at https://www.youtube.com/watch?v=I_9nMSvY1FE
which displays CO2 emissions by country, per-capita by decade, over time, by income group, grouped by region.

<a id=“UI”>
## UI</a>


0. To specific options for a graph pane, click the caret at the right of the gray bar above that pane.

0. Select float.
 
<a id=“TableauDesktop”>
## Tableau Desktop</a>

Tableau Online hosts Tableau Server within Tableau’s cloud.

<img width="878" alt="tableau how it works" src="https://cloud.githubusercontent.com/assets/300046/11996251/63b57000-aa1c-11e5-83a8-b233300d863a.png">

<a id=“Videos”>
## Videos</a>
Ben Sullins (@bensullins, bensullins.com) created several video tutorials:

 1. <a target="_blank" href="https://app.pluralsight.com/library/courses/business-dashboard-fundamentals">
	Business Dashboard Fundamentals</a>
	Feb 19, 2014 - 3h 36m 42s
	provides advice about design of beautiful charts in Excel and Tableau 8.1,
	such as removing Chart Junk.

 2. <a target="_blank" href="https://app.pluralsight.com/library/courses/data-analytics-hands-on">
	Data Analytics: Hands On</a>
	Jul 15, 2015 - 5h 2m 19s
	provides an introduction to use of Excel and SQL and Tableau

 3. <a target="_blank" href="https://app.pluralsight.com/library/courses/data-analysis-fundamentals-tableau">
	Data Analysis Fundamentals with Tableau</a>
	Sep 03, 2013 - 4h 47m 43s

 4. <a target="_blank" href="https://app.pluralsight.com/library/courses/big-data-analytics-tableau">
	Big Data Analytics with Tableau</a>
	Jul 21, 2013 - 3h 44m 55s

 5. <a target="_blank" href="https://app.pluralsight.com/library/courses/enterprise-business-intelligence-tableau-server">
	Enterprise Business Intelligence with Tableau Server</a>
	Nov 13, 2013 - 1h 36m 26s

 6. <a target="_blank" href="https://app.pluralsight.com/library/courses/data-visualization-using-tableau-public">
	Data Visualizations Using Tableau Public</a>
	Sep 09, 2013 - 1h 47m 56s
