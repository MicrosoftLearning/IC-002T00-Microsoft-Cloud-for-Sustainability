# Lab 02: Data ingestion

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

![](./Images/Lab02/L02_image001.png)

### Personas and Scenarios

In this lab, Reed Flores – IT Admin for Wide World Importers utilizes the activity data Excel spreadsheets sourced by Alex Serra – Emissions Analyst. The Activity data spreadsheets contain Electricity Purchased for the year 2021 and Miles driven by the fleet of Fabrikam Electric Trucks for the calendar year 2021. Reed utilizes Microsoft Sustainability Manger’s connector functionality to import from the Excel spreadsheets, and reviews other connectors available for future purposes. Reed uses the built-in Power Query functionality to transform the data to match Microsoft Sustainability Manager’s data schema and looks for other potential issues such as case-sensitive d data fields.

![](./Images/Lab02/L02_image002.png)

In this lab exercise, we will focus on the Lab 2 scenario illustrated below:

![](./Images/Lab02/L02_image003.png)

## Exercise 1: Import Data

In this exercise, you will learn about the steps that Reed takes to ingest the spreadsheets given by Alex. Data import is a vital task to bringing large volumes of data into Microsoft Sustainability Manager. Excel is utilized in this lab; however, many pre-built connectors are available, and Partners can build custom connectors to integrate with additional data sources. You can explore this functionality in deeper detail on Microsoft Docs, please visit [Overview of data connectors](https://docs.microsoft.com/en-us/industry/sustainability/import-data-connectors).

>[!NOTE] **Important** Please ensure you have completed the previous lab to create Reference Data. **The data import process requires all Reference Data to exist, and the process is case sensitive, so please ensure the Reference data that was added has the exact same case formatting as what is found in the lab**. Failure to do so will result in errors during the data import process

-   For our Instructor Lead Training, we suggest using In-private browsing, or a new browser profile.
-   For this lab, you will be utilizing OneDrive. Please ensure that your personal one drive has been initialized by clicking the app selector button in the top left corner of the screen

    ![Graphical user interface, application, chat or text message Description automatically generated](./Images/Lab02/L02_image005.png)

-   Select OneDrive from the Apps list

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image006.png)

-   This will open a new tab with your new OneDrive. You can close this tab and return to the Power Apps maker portal.

    ![Graphical user interface, application, Teams Description automatically generated](./Images/Lab02/L02_image007.png)

-   Open the **Sustainability Manager** Application

    ![A screenshot of a computer Description automatically generated](./Images/Lab02/L02_image008.png)

-   You will land on the **Home** page for Microsoft Sustainability Manager

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image009.png)

-   Area navigation is a common first step in each lab and exercise. You can find the area navigation menu in the bottom corner of your screen.

   ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image010.png) 

### Task 1: Import 2021 data for “Purchased Electricity“ for Facilities

In this task, Reed imports the first excel spreadsheet provided by Alex, Purchased electricity Wide World Importers – 2021.xlsx. This brings in the Electricity Purchased by Wide World Importers facilities for the year 2021 into the Purchased electricity activity data.

1.  In the bottom left corner, change the Area to **Data**

    ![Graphical user interface, application, Teams Description automatically generated](./Images/Lab02/L02_image011.png)

1.  Navigate to “**Activity data**” on the left side of the page.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab02/L02_image012.png)

1.  Find Purchased electricity in the **Scope 2: Indirect emissions** section, and click **Manage**

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image013.png)

1.  On the “Connections” view, click **+New**

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image014.png)

1.  On the “New data connection” wizard:
    1. Select **Activity data** from data type screen
    1. Choose **Purchased electricity** from the Activity data drop down list
    1. Click **Next** when finished

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image015.png)

1.  Take a moment to review the large list of connectors by clicking the “See all Power Query connectors” link

    ![Graphical user interface Description automatically generated](./Images/Lab02/L02_image016.png)

1.  Microsoft Sustainability Manager utilizes Power Query for its data ingestion connectors, there is a broad list of connectors available in Power Query. Click Cancel or the X in the top right corner to close the Power Query dialog.

    ![Graphical user interface Description automatically generated](./Images/Lab02/L02_image017.png)

1.  On the “Choose connector” page:
    1.  Select **Excel**
    1.  Click **Next**

    >[!NOTE]**Note:** Notice the Adatum Utility Management connector at the bottom. Data providers and Partners can create their own connectors to be available in Microsoft Sustainability Manager

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image018.png)

1.  A new dialog will open for Power Query. On the Power Query dialog:
    1.  Click **Upload file**
    1.  Click **Browse**

    >[!NOTE]**Note:** You can also choose to import an existing file located in OneDrive. For simplicity of this lab, we are using the Upload file functionality.

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image019.png)

1.  On the file selection window, browse to the location of the excel files that were downloaded.
    1.  Select the **Purchased electricity Wide World Importers - 2021.xlsx** file
    1.  Click **Open**

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab02/L02_image020.png)

1.  Once the file is successfully uploaded, it may be required to click the sign in button below to create a new Connection credential, this is done by clicking **Sign in**.

    ![Graphical user interface, table Description automatically generated](./Images/Lab02/L02_image021.png)

1.  An Office 365 Sign in dialog will appear. Reed selects their user from the list. (For the purposes of this lab, select your “In a Day” user account from the list).

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab02/L02_image022.png)

1.  Once the sign in process is completed, the new connection is automatically selected. Click **Next**.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab02/L02_image024.png)

1.  On the “Choose data” page of the Power Query wizard:
    1.  Select the “**Purchased electricity**” sheet
    1.  Click **Transform data**

    ![Table Description automatically generated](./Images/Lab02/L02_image025.png)

    On the “Transform data” page of the Power Query wizard, various data and column transformations can be performed. This will allow for the adjusting of data types, update column mappings, and even perform advanced transformations familiar with in Power Platform Dataflows or Power BI Datasets.

1.  In this scenario, Reed will need to map the columns from the spreadsheet to the columns in Microsoft Sustainability Manager. To do this click on Map to entity in the upper right corner of the dialog window.

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image026.png)

1.  On the “Map to CDM entity” of the dialog window we need to:
    1.  Select the table name, “**Purchased energy**”
    1.  Select “**Auto map**” to allow any automatic mappings to occur
    1.  Contractual Instrument Type was “Not mapped”, hence Reed selects “**Contracted firm**” from the list of options in the “Query output column”
    1.  Energy Provider name was “Not mapped”, select “**Provider**” from the list of options in the “Query output column”
    1.  When finished, click “**OK**”

    ![Graphical user interface, table Description automatically generated](./Images/Lab02/L02_image027.png)

1.  The “Transform data” page should now look like this

    >[!NOTE]**Note:** Observe that the column names have changed to Contractual Instrument Type and Energy Provider Name

    ![Graphical user interface, application, table, Excel Description automatically generated](./Images/Lab02/L02_image028.png)

1.  Click “**Create**” to start the data import process:

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image029.png)

1.  The “New data connection” wizard will now be on the Schedule data import page.

    Turning on “Import data automatically” will give the option to set a schedule to have the data imported automatically, this may be a good option if the connector will be used in a scenario where the data will change frequently such as a web API or FTP server.

    Turning on “Replace previously imported data” will remove all previously imported data and bring in the full data set that was retrieved, this may be a good option if the data source is not only providing data from the last import or always includes a full set of data. For this scenario of importing historical data, leave both options turned off.

    Click “**Next**” when finished

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab02/L02_image030.png)

1.  On the “Review and finish” page:
    1.  Enter a name for the new connection, such as “**Wide World Importers - Purchased Electricity - 2021**”
    1.  Click “**Connect**”

    ![](./Images/Lab02/L02_image031.png)

1.  At the bottom of the window, there will be a message, “Creating connection…”

    ![Graphical user interface Description automatically generated with medium confidence](./Images/Lab02/L02_image032.png)

1.  Once the connection is created, click “**Done**”

    ![](./Images/Lab02/L02_image033.png)

1.  The “**Connections**” view will now be visible, along with the status of the recently created connection. It should say “**Processing**”

    ![Graphical user interface, text, application, website Description automatically generated](./Images/Lab02/L02_image034.png)

1.  After a minute or two click the “**Refresh**” button above the list to see the updated status, which should be “**Completed**”

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image035.png)

1.  Navigate to “**Activity data**” on the left side of the page.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab02/L02_image036.png)

1.  Find Purchased electricity in the Scope 2: Indirect emissions section, and click **View**

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image037.png)

1.  The Purchased electricity view shows all purchased electricity activity data that has been imported

    ![A screenshot of a computer Description automatically generated](./Images/Lab02/L02_image038.png)

1.  Filter the view by clicking the down arrow next to the **Organizational Unit** column, and selecting **Filter by**

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image039.png)

1.  Select “**Wide World Importers**” from the Filter By dialog

    ![Graphical user interface, application Description automatically generated](./Images/Lab02/L02_image040.png)

1.  Click **Apply** to apply the filter to the column

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab02/L02_image041.png)

2.  After a few moments, the view will refresh, and the activity data records that were imported during this lab will be displayed.

    ![](./Images/Lab02/L02_image042.png)

Great job, you have just completed the data import of 2021 Purchased Electricity for Wide World Importers. This is an important step to realizing the goal of recording, reporting, and reducing carbon emissions. Next, we will import the 2021 Miles Driven for Wide World Importers fleet of electric vehicles. **Please continue to the next task.**
