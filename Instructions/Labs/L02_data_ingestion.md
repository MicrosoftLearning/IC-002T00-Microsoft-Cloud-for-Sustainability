# Lab 02 – Data ingestion

## Overview

### Background

In the previous lab, Wide Word Importers’ company profile, facilities, and reference data such as Contractual instrument types were created to lay the Master data foundation for Emissions calculations and Reporting. In this lab - we will perform the Activity data ingestion for the Purchased Electricity of the two newly acquired Florida facilities. In addition, we will also ingest emission data related to the charging of the fleet of 50 Fabrikam Electric trucks. The built-in connectors in the Microsoft Sustainability Manager will be used to ingest the Activity data into the application.

### Learning Objectives

In this lab, you will do the following:

-   Use Microsoft Sustainability Manager connectors to ingest data
-   Use Power Query to transform the data before ingestion
-   Review the ingested data in the “Purchase Electricity Activity Data” Dataverse Table
-   The newly ingested activity data during this lab exercise will be utilized in the remaining scenarios (calculations and reporting) in the upcoming lab exercises.

### Prerequisites

-   Microsoft Sustainability manager environment is set up with sample data
-   Lab 01 organization and reference data is entered.

### Solution Focus Area

In this lab, the focus is on the “Data Ingestion” aspect of the Solution Focus Area. It follows the “Organization and Reference data Set up” and forms the basis for the emission calculations and the reporting thereafter. The Microsoft Sustainability Manager is flexible with multiple automated options to ingest data – such as the connectors as well as manual inputs. For scenarios that may require complex data transformation and/or ETL, tools like Azure Data Factory are recommended. You can explore this functionality in deeper detail on Microsoft Docs, please visit [Overview of Microsoft Cloud for Sustainability Data Import](https://docs.microsoft.com/en-us/industry/sustainability/import-data)

![](media/9d46ab408ece0a29ab85b4c6dc0ef24f.png)

### Personas and Scenarios

In this lab, Reed Flores – IT Admin for Wide World Importers utilizes the activity data Excel spreadsheets sourced by Alex Serra – Emissions Analyst. The Activity data spreadsheets contain Electricity Purchased for the year 2021 and Miles driven by the fleet of Fabrikam Electric Trucks for the calendar year 2021. Reed utilizes Microsoft Sustainability Manger’s connector functionality to import from the Excel spreadsheets, and reviews other connectors available for future purposes. Reed uses the built-in Power Query functionality to transform the data to match Microsoft Sustainability Manager’s data schema and looks for other potential issues such as case-sensitive d data fields.

![](media/5b6937348161db5693a33bc7fb0ac688.png)

In this lab exercise, we will focus on the Lab 2 scenario illustrated below:

![](media/2bf242e01418fef1793d979f53fa9c19.png)

## Exercise 1: Import Data

In this exercise, you will learn about the steps that Reed takes to ingest the spreadsheets given by Alex. Data import is a vital task to bringing large volumes of data into Microsoft Sustainability Manager. Excel is utilized in this lab; however, many pre-built connectors are available, and Partners can build custom connectors to integrate with additional data sources. You can explore this functionality in deeper detail on Microsoft Docs, please visit [Overview of data connectors](https://docs.microsoft.com/en-us/industry/sustainability/import-data-connectors).

**Important**

Please ensure you have completed the previous lab to create Reference Data. **The data import process requires all Reference Data to exist, and the process is case sensitive, so please ensure the Reference data that was added has the exact same case formatting as what is found in the lab**. Failure to do so will result in errors during the data import process

-   For our Instructor Lead Training, we suggest using In-private browsing, or a new browser profile.
-   For our Instructor Lead Training, log in to <https://make.powerapps.com> using the mcfsiaduserXX@powerplatformopenhacks.onmicrosoft.com account that has been assigned to you.
-   For our Instructor Lead Training, please use the environment selector to select the MCFSInADay_XX environment that has been assigned to you

    ![Graphical user interface, application Description automatically generated](media/3b47be57daf3ca186d756d60546e5209.png)

-   For this lab, you will be utilizing OneDrive. Please ensure that your personal one drive has been initialized by clicking the app selector button in the top left corner of the screen.

    ![Graphical user interface, text, application Description automatically generated](media/49f5149b932a8cd96ed61529b603ba92.png)

-   Select one drive from the Apps list

![Graphical user interface, application, chat or text message Description automatically generated](media/a83fb0d68538f0d1fea03f0d93e39580.png)

-   This will open a new tab with your new OneDrive. You can close this tab and return to the Power Apps maker portal.

![Graphical user interface, application Description automatically generated](media/dcbd5f617359aa9f167530a9fd2c59a9.png)

-   Open the **Sustainability Manager** Application

![Graphical user interface, application, Teams Description automatically generated](media/1a1a272bb83f2b2ba3b33875982e80ff.png)

-   You will land on the **Home** page for Microsoft Sustainability Manager

![A screenshot of a computer Description automatically generated](media/f345d83abdbc1e3b1b0525295db4c87c.png)

-   Area navigation is a common first step in each lab and exercise. You can find the area navigation menu in the bottom corner of your screen.

![Graphical user interface, application Description automatically generated](media/15edf9e58020948ebab2197ccae9456b.png)

### Task 1: Import 2021 data for “Purchased Electricity“ for Facilities

In this task, Reed imports the first excel spreadsheet provided by Alex, Purchased electricity Wide World Importers – 2021.xlsx. This brings in the Electricity Purchased by Wide World Importers facilities for the year 2021 into the Purchased electricity activity data.

1.  In the bottom left corner, change the Area to **Data**

![Graphical user interface, application, Teams Description automatically generated](media/63dc3524c7761d4ac282a040d65ba06e.png)

1.  Navigate to “**Activity data**” on the left side of the page.

![Graphical user interface, text, application, chat or text message Description automatically generated](media/1acc43c1849587d1fd0d0c6720a7ea17.png)

1.  Find Purchased electricity in the **Scope 2: Indirect emissions** section, and click **Manage**

![Graphical user interface, application Description automatically generated](media/622b7248945267f557a14843ca6486f3.png)

1.  On the “Connections” view, click **+New**

![Graphical user interface, application Description automatically generated](media/806ff899fe0e6faefce66833f4ce84bb.png)

1.  On the “New data connection” wizard:
    1.  Select **Activity data** from data type screen
    2.  Choose **Purchased electricity** from the Activity data drop down list
    3.  Click **Next** when finished

![Graphical user interface, application Description automatically generated](media/3c1120674adfa9de586530448eb8fad2.png)

1.  Take a moment to review the large list of connectors by clicking the “See all Power Query connectors” link

![Graphical user interface Description automatically generated](media/34be372f06e18ace83b2cc591b310bd8.png)

1.  Microsoft Sustainability Manager utilizes Power Query for its data ingestion connectors, there is a broad list of connectors available in Power Query. Click Cancel or the X in the top right corner to close the Power Query dialog.

![](media/ed197074f5ab4ffa0dac5af0ba6096b7.png)

1.  On the “Choose connector” page:
    1.  Select **Excel**
    2.  Click **Next**

**Note:** Notice the Adatum Utility Management connector at the bottom. Data providers and Partners can create their own connectors to be available in Microsoft Sustainability Manager

![Graphical user interface, application Description automatically generated](media/94f94269c4d88396ac3acb42caa848f7.png)

1.  A new dialog will open for Power Query. On the Power Query dialog:
    1.  Click **Upload file**
    2.  Click **Browse**

**Note:** You can also choose to import an existing file located in OneDrive. For simplicity of this lab, we are using the Upload file functionality.

![Graphical user interface, application Description automatically generated](media/318d685562d61b2dc5bd317ca1b5b08f.png)

1.  On the file selection window, browse to the location of the excel files that were downloaded.
    1.  Select the **Purchased electricity Wide World Importers - 2021.xlsx** file
    2.  Click **Open**

![Graphical user interface, text, application, email Description automatically generated](media/ec898bcacfc55990d284bad8fa83c358.png)

1.  Once the file is successfully uploaded, it may be required to click the sign in button below to create a new Connection credential, this is done by clicking **Sign in**.

![Graphical user interface, table Description automatically generated](media/b5e4f8ffd45568435a9bdf69b53aa6fe.png)

1.  An Office 365 Sign in dialog will appear. Reed selects their user from the list. (For the purposes of this lab, select your “In a Day” user account from the list).

![Graphical user interface, text, application Description automatically generated](media/648e8c60eec1ce5808ff1ffe31462256.png)

1.  Once the sign in process is completed, the new connection is automatically selected. Click **Next**.

![Graphical user interface, text, application Description automatically generated](media/41793c57622d360a5108b23fd082550d.png)

1.  On the “Choose data” page of the Power Query wizard:
    1.  Select the “**Purchased electricity**” sheet
    2.  Click **Transform data**

![Table Description automatically generated](media/dfb5f3a48b29127921a5d9a3a3e61ef6.png)

On the “Transform data” page of the Power Query wizard, various data and column transformations can be performed. This will allow for the adjusting of data types, update column mappings, and even perform advanced transformations familiar with in Power Platform Dataflows or Power BI Datasets.

1.  In this scenario, Reed will need to map the columns from the spreadsheet to the columns in Microsoft Sustainability Manager. To do this click on Map to entity in the upper right corner of the dialog window.

![Graphical user interface, application Description automatically generated](media/a8a4fc38385aa7a26432b9c0910c5727.png)

1.  On the “Map to CDM entity” of the dialog window we need to:
    1.  Select the table name, “**Purchased energy**”
    2.  Select “**Auto map**” to allow any automatic mappings to occur
    3.  Contractual Instrument Type was “Not mapped”, hence Reed selects “**Contracted firm**” from the list of options in the “Query output column”
    4.  Energy Provider name was “Not mapped”, select “**Provider**” from the list of options in the “Query output column”
    5.  When finished, click “**OK**”

![Graphical user interface, table Description automatically generated](media/5cf040b013abdcc4b2e407147574af98.png)

1.  The “Transform data” page should now look like this

    **Note:** Observe that the column names have changed to Contractual Instrument Type and Energy Provider Name

![Graphical user interface, application, table, Excel Description automatically generated](media/2c68eb66b5ab13ae04e3dab2addf45fe.png)

1.  Click “**Create**” to start the data import process:

![Graphical user interface, application Description automatically generated](media/c00bb5bdfcca3c13481a4e7b79a9ab13.png)

1.  The “New data connection” wizard will now be on the Schedule data import page.

    Turning on “Import data automatically” will give the option to set a schedule to have the data imported automatically, this may be a good option if the connector will be used in a scenario where the data will change frequently such as a web API or FTP server.

    Turning on “Replace previously imported data” will remove all previously imported data and bring in the full data set that was retrieved, this may be a good option if the data source is not only providing data from the last import or always includes a full set of data. For this scenario of importing historical data, leave both options turned off.

    Click “**Next**” when finished

![Graphical user interface, text, application, email Description automatically generated](media/59cfa64ef482c9ff35ecf3c57488666c.png)

1.  On the “Review and finish” page:
    1.  Enter a name for the new connection, such as “**Wide World Importers - Purchased Electricity - 2021**”
    2.  Click “**Connect**”

![](media/ac2ab6f773aad12e6221ea2fef0035d4.png)

1.  At the bottom of the window, there will be a message, “Creating connection…”

![Graphical user interface Description automatically generated with medium confidence](media/24f887f684db9c24b1d89737edb0a874.png)

1.  Once the connection is created, click “**Done**”

![](media/d1411ec246288e1e03c5918ff7ce0de8.png)

1.  The “**Connections**” view will now be visible, along with the status of the recently created connection. It should say “**Processing**”

![Graphical user interface, text, application, website Description automatically generated](media/9917200d43e13313b4f6c69d9d7fb94b.png)

1.  After a minute or two click the “**Refresh**” button above the list to see the updated status, which should be “**Completed**”

![Graphical user interface, application Description automatically generated](media/83f377049dd18d079ff24b94ed3b153f.png)

1.  Navigate to “**Activity data**” on the left side of the page.

![Graphical user interface, text, application, chat or text message Description automatically generated](media/1acc43c1849587d1fd0d0c6720a7ea17.png)

1.  Find Purchased electricity in the Scope 2: Indirect emissions section, and click **View**

![Graphical user interface, application Description automatically generated](media/7116ebd0c160916dcdac3307601e4352.png)

1.  The Purchased electricity view shows all purchased electricity activity data that has been imported

![A screenshot of a computer Description automatically generated](media/961362bd118df9ddb945c32d4ac1c6cd.png)

1.  Filter the view by clicking the down arrow next to the **Organizational Unit** column, and selecting **Filter by**

![Graphical user interface, application Description automatically generated](media/e9876843c1d22a57afd4f864c91950b0.png)

1.  Select “**Wide World Importers**” from the Filter By dialog

![Graphical user interface, application Description automatically generated](media/0c7144223599da4b62e541f01f0cbbd9.png)

1.  Click **Apply** to apply the filter to the column

    ![Graphical user interface, text, application, email Description automatically generated](media/bf26e7b669524194047b1162206a50a2.png)

2.  After a few moments, the view will refresh, and the activity data records that were imported during this lab will be displayed.

![](media/3261260cd832162947233195ab5bcbe9.png)

Great job, you have just completed the data import of 2021 Purchased Electricity for Wide World Importers. This is an important step to realizing the goal of recording, reporting, and reducing carbon emissions. Next, we will import the 2021 Miles Driven for Wide World Importers fleet of electric vehicles. **Please continue to the next task.**

### Task 2: Import 2021 data “Miles Driven” for Electric Trucks

In this task, Reed imports the second excel spreadsheet provided by Alex - “Fleet Vehicles Miles Driven Wide World Importers - 2021.xlsx”. While electric vehicles do not produce direct tailpipe emissions, they do produce “Scope 2: Purchased electricity from charging”. This brings in the Miles driven by Wide World Importers fleet of electric truck for the year 2021 into the Purchased electricity activity data.

1.  Navigate to “**Data connections**” on the left side of the page.

![](media/d52273e465a211a3fc2af93b77f219bd.png)

1.  On the “Connections” view, click **+New**

![Graphical user interface, application Description automatically generated](media/806ff899fe0e6faefce66833f4ce84bb.png)

1.  On the “New data connection” wizard:
    1.  Select **Activity data** from data type screen
    2.  Choose **Purchased electricity** from the Activity data drop down list
    3.  Click **Next** when finished

![Graphical user interface, application Description automatically generated](media/3c1120674adfa9de586530448eb8fad2.png)

1.  On the “Choose connector” page:
    1.  Select “**Excel**”
    2.  Click “**Next**” when finished

![Graphical user interface, application Description automatically generated](media/94f94269c4d88396ac3acb42caa848f7.png)

1.  A new dialog will open for Power Query. On the Power Query dialog:
    1.  Click “**Upload file**”
    2.  Click “**Browse**”

![Graphical user interface, application Description automatically generated](media/318d685562d61b2dc5bd317ca1b5b08f.png)

1.  On the file selection window, browse to the location of the excel files the downloaded.
    1.  Select the “**Fleet Vehicles Miles Driven Wide World Importers - 2021.xlsx**” file
    2.  Click “**Open**”

![](media/91efae8488183e2db60c9370ef963314.png)

1.  Once the file is uploaded, the Connection credentials automatically selects the previous connection for authentication. Click “**Next**”

![Graphical user interface, text, application, email Description automatically generated](media/137000ca034e3701a17dbd85c26ccee2.png)

1.  On “Choose data” page of the Power Query wizard:
    1.  Select the “**Miles Driven**” sheet
    2.  Click “**Transform data**”

![](media/176ba49aaf13ff1d341745b7e4d76cb9.png)

On the “Transform data” page of the Power Query wizard, various data and column transformations can be performed. This will allow the adjusting of data types, column mappings updates, and even perform advanced transformations familiar with in Power Platform Dataflows or Power BI Datasets.

1.  In this scenario, Reed will need to map the columns from the spreadsheet to the columns in Microsoft Sustainability Manager. To do this click on Map to entity in the upper right corner of the dialog window.

![Graphical user interface, application Description automatically generated](media/a8a4fc38385aa7a26432b9c0910c5727.png)

1.  On the “Map to CDM entity” dialog window we need to:
    1.  Select the table name, “**Purchased energy**”
    2.  Select “**Auto map**” to allow any automatic mappings to occur
    3.  Contractual Instrument Type was “Not mapped”, hence Reed selects “**Contracted firm**” from the list of options in the “Query output column”
    4.  Energy Provider name was “Not mapped”, select “**Provider**” from the list of options in the “Query output column”
    5.  When finished, click “**OK**”

![Graphical user interface, table Description automatically generated](media/5cf040b013abdcc4b2e407147574af98.png)

1.  The “Transform data” page should now look like this

    **Note:** Observe that the column names have changed to Contractual Instrument Type and Energy Provider Name.

![](media/e32ef1172abad27830fa4a2698427406.png)

1.  Click “**Create**” to start the data import process:

![Graphical user interface, application Description automatically generated](media/c00bb5bdfcca3c13481a4e7b79a9ab13.png)

1.  The “New data connection” wizard will now be on the Schedule data import page.

    Turning on “Import data automatically” will give the option to set a schedule to have the data imported automatically, this may be a good option if the connector will be used in a scenario where the data will change frequently such as a web API or FTP server.

    Turning on “Replace previously imported data” will remove all previously imported data and bring in the full data set that was retrieved, this may be a good option if the data source is not only providing data from the last import or always includes a full set of data. For this scenario of importing historical data, leave both options turned off.

    Click “**Next**” when finished

![Graphical user interface, text, application, email Description automatically generated](media/59cfa64ef482c9ff35ecf3c57488666c.png)

1.  On the “Review and finish” page:
    1.  Enter a name for the new connection, such as “**Wide World Importers - Electric Vehicle Miles Driven - 2021**”
    2.  Click “**Connect**”

![](media/2ad3fd95be45e84334db1e7e00ca1d1c.png)

1.  At the bottom of the window, there will be a message, “**Creating connection…**”

![Graphical user interface Description automatically generated with medium confidence](media/24f887f684db9c24b1d89737edb0a874.png)

1.  Once the connection is created, click “**Done**”

![](media/813cdc06dd0edac9bfde413e8cf19da5.png)

1.  The “**Connections**” view will now be visible, along with the status of the recently created connection. It should say “**Processing**”

![Graphical user interface, text, application Description automatically generated](media/a5af6559c0768a7318f9e627025f339f.png)

1.  After a minute or two click the “**Refresh**” button above the list to see the updated status, which should be “**Completed**”.Ensure you have the correct number of records as below and the status of the data connections are **Complete** before moving to next steps.

Note : In case if you have more duplicate records than below screenshot, due to an issue with the following the correct data import steps , you have to delete the activity data and redo the process .Reach out to the lab instructor for support

![](media/9f20b2ca76ae00176e58dd8ea7724a79.png)

1.  Navigate to “**Activity data**” on the left side of the page.

![](media/1acc43c1849587d1fd0d0c6720a7ea17.png)

1.  Find Purchased electricity in the Scope 2: Indirect emissions section, and click **View**

![](media/7116ebd0c160916dcdac3307601e4352.png)

1.  The Purchased electricity view shows all purchased electricity activity data that has been imported

![](media/14cdec74a1fa7b4d2cc9b1f315f61405.png)

1.  Filter the view by clicking the down arrow next to the **Organizational Unit** column, and selecting **Filter by**

![Graphical user interface, application Description automatically generated](media/e9876843c1d22a57afd4f864c91950b0.png)

1.  Select “**Wide World Importers**” from the Filter By dialog

![Graphical user interface, application Description automatically generated](media/0c7144223599da4b62e541f01f0cbbd9.png)

1.  Click **Apply** to apply the filter to the column

![Graphical user interface, text, application, email Description automatically generated](media/bf26e7b669524194047b1162206a50a2.png)

1.  After a few moments, the view will refresh, and the activity data records that were imported during this lab will be displayed.

![](media/9bc45d7ce3b9357ba9ff858b90070550.png)

**Congratulations!** You have just completed the data import for 2021 Miles Driven for Wide World Importers. This is an important step to realizing the goal of recording, reporting, and reducing carbon emissions. In the following labs we will calculate emissions, review insights and reporting, and define our reduction scorecards and goals.
