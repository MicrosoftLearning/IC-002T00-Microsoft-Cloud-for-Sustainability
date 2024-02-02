---
lab:
    title: 'Lab 5: Goals and scorecards'
    module: 'Module 7: Configure goals and scorecards'
---
# Module 7 Lesson 2 Lab 5: Goals and scorecard

## Overview

### Background

In the previous four labs, the master and system data were set up and calculations performed to report on emissions. In this lab, the focus is on setting carbon emission reduction goals and tracking them using scorecards. In the scorecard, emission reduction goals can be introduced based on the organization’s sustainability priorities and can be collaboratively tracked with various stakeholders using the Teams collaboration feature.

### Learning Objectives

In this lab, you will do the following:

-   Create Scorecards and Goals to monitor progress towards Carbon reduction targets
-   Understand goal check-ins
-   Configure and use Microsoft Teams Chat collaboration features

### Prerequisites

-   Microsoft Sustainability manager environment is set up with sample data
-   Lab 1 organization and reference data is entered
-   Lab 2 activity data is ingested
-   Lab 3 emissions are calculated
-   Lab 4 deep analysis and reporting review

### Solution Focus Area

Scorecards and goals can help curate sustainability metrics and track them against an organization’s key business objectives. After the scorecard is created that includes goals, the scorecard progression can be periodically checked including how the scorecard is progressing and to make any required adjustments.

There will probably be times when there is a need to share and discuss data, reports, analytics, or goals across many stakeholders in the organization. To help make those conversations contextual and collaborative, Teams Chat is available directly in Microsoft Sustainability Manager.

![image](./Images/Lab05/image0.svg)


### Personas and Scenarios

In this lab, Amber Rodrigues – Sustainability specialist for Contoso Corp creates and monitors Carbon reduction goals. Based on the insights from the Deep Analysis dashboard, Amber creates a new scorecard for Wide World Importers and creates a goal to reduce their carbon emissions from the previous year. Amber sets up automatic goal check-ins to track the ongoing status of the goal.

Finally, Amber, with the help of Reed Flores – IT Admin for Wide World Importers, configures Microsoft Teams collaboration. Once configured, Amber opens a chat with one of their colleagues to discuss changes to a factor library, continuing Ambers great work to record, report, and reduce carbon emissions across Wide World Importers and the entirety of Contoso Corp.

![image](./Images/Lab05/image00.svg)

In this lab exercise, we will focus on the scenarios illustrated below:

![image](./Images/Lab05/image000.svg)


## Exercise 1: Define sustainability goals

In this exercise, you will learn about the steps that Amber takes to create scorecards and goals to help Wide World Importers track carbon reduction progress. Based on the results of the previous lab, Amber has determined that Wide World Importers needs to reduce their Scope 2: Purchased electricity carbon emissions. Scorecards and goals allow organizations to set carbon reduction targets and track their progress to that. You can explore this functionality in deeper detail on Microsoft Docs, please visit Overview of scorecards and goals https://docs.microsoft.com/en-us/industry/sustainability/reports-scorecards-goals.

1. Log into the virtual machine using the virtual machine credentials located on the **Resources** tab above.

2. Open a new browser window and navigate to https://make.powerapps.com.

3. Log into your Microsoft 365 tenant using the credentials for the tenant located on the Resources tab above.

4. If needed, change the environment to yours on the top bar.

5. Open the Sustainability Manager Application.


    >[!ALERT] **Important:** Please make sure that you have completed the previous labs to ensure that the scorecard and goals show meaningful data.

### Task 1: Create a new Scorecard

In this task, Amber will create a new scorecard to track the goals for Wide World Importers. Microsoft Sustainability Manager utilizes scorecards to group goals together.

2.  Navigate to **Scorecards and goals** on the left navigation pane under **Analytics**.
   
3.  On the **Scorecards** view, select **+Add Scorecard**.

    ![image](./Images/Lab05/image5.svg)

4.  Amber uses the following information to populate the fields on the new Scorecard.
 
    (1) Enter the **Name**: Wide World Importers Reduction Plan - 2025

    (2) Select **Save**.

    **Note:** The name of the scorecard is used for identifying the scorecard in the list.

   ![image](./Images/Lab05/image7.svg)

5.  Your new Scorecard will open automatically.

   ![image](./Images/Lab05/image8.svg)

Great job, you have helped Amber create a new scorecard to track the goals for Wide World Importers. Scorecards are used to track progress towards an organization’s sustainability goals by serving to logically group goals together. In the next tasks we will discuss creating goals and goal check-ins.  **Please continue to the next task.**

### Task 2: Create a Goal

In this task, Amber will create a new goal instructing Wide World Importers to reduce their carbon emissions from 900 mtCO<sub>2</sub>E to 600 mtCO<sub>2</sub>E. Amber will enable automatic check-ins and status rules to ensure that the goal is automatically kept up to date. These automatic check-ins will occur once every 24 hours. Microsoft Sustainability Manager utilizes goals to help organizations like Contoso Corp and Wide World Importers track their carbon reduction goals.

1.  Select the **+Add goal** button on the **scorecards** view to create a new goal.

    ![image](./Images/Lab05/image9.svg)

2. The first fields of the goal are explained below: 

    - **Goal name** is used for identifying the goal in the list.
    - **Owner** is used to identify the primary person responsible for monitoring and tracking goal progress.
    - **Scorecard** is used to specify which scorecard to associate the goal with. In this scenario, because the goal was created on the scorecard page, the scorecard field is automatically filled out.
    - **Organizational unit** is used to identify which Organizational unit the goal is associated with.
    - **Start date** is used to identify the starting time frame of the goal.
    - **End date** is used to identify the ending time frame of the goal.
    - **Unit of measure** is used to specify which unit you would like to measure in this goal.
    - **Starting value** is used to specify your starting point for the goal.
    - **Source of current value** is used to specify what the source of the current value is, if set to Enter Manually, or where to retrieve the current value from each day. The **Source of current value** can be a roll up from other child goals, or as in this scenario, Connected to data.

3.  Amber uses the following information to populate these fields on the new Goal. Enter the data:

    (1) **Goal name**: Reduce Scope 2 Emissions – 2023

    (2) **Owner**: MOD and select **MOD Administrator**

    (3) **Scorecard**: Wide World Importers Reduction Plan - 2025

    (4) **Organizational unit**: Wide World Importers

    (5) **Start date**: 12/31/2022 (select from calendar, do not type)

    (6) **End date**: 12/31/2023 (select from calendar, do not type)

    **Note**: The automatic check-in process will not perform a check-in if the current date is outside of the Start and End date range. Wide World Importers chose 12/31/2022 to include the final calculation of 2022 as the first, or base, check-in value for the new goal
   
    ![image](./Images/Lab05/image10.svg)

4. Under Progress tracker, enter Unit of measure – mtCO2e and Starting value - 900

   ![image](./Images/Lab05/image11.svg)

5. Select Connect to data for Source of current value. Click on Set up connection. Enter the following details:

    1. Data source – **Emission**

    2. Value – **CO2E**

    3. Filter – Select **Add > Add row**. Select **Organizational unit equals Wide World Importers (Organizational unit)** and Select **Add>Add** row again. Select **Consumption end date** as **Last x years** with value **1**

    4. Select **Calculate**.

    5. Click on **Confirm**.

    ![image](./Images/Lab05/image12.svg)

   ![image](./Images/Lab05/image13.svg)

6. The connection is completed successfully.

    ![image](./Images/Lab05/image14.svg)

7. The following list provides descriptions of the data that you’re entering:

   o	**Name** – Use to identify the goal in the list.

   o	**Owner** – Use to identify the primary person who’s responsible for monitoring and tracking goal progress.

   o	**Scorecard** – Use to specify which scorecard to associate the goal with. In this scenario, because the goal was created on the Scorecard page, the Scorecard field is automatically filled out.

   o	**Organizational unit** – Use to identify which organizational unit the goal is associated with.

   o	**Start date** – Use to identify the starting time frame of the goal.

   o	**End date** – Use to identify the ending time frame of the goal.

   o	**Unit** – Use to specify which unit you want to measure in this goal.

   o	**Starting value** – Use to specify your starting point for the goal.

   o	**Source of current value** – Use to specify the source of the current value, if it’s set to Enter manually, or where to retrieve the current value from each day. The Source of current value can be a roll up from other child goals.

       o   Select **Emission** as the **Data source**. This table is where the data will come from. 

       o   At the top of the form, select **Calculate** for a preview of the data that would be used for the current value check-in. Copy this value. 

       o   Select **Confirm** when you’re finished.

8. Scroll down on the **Add a goal** page. For **Source of target value** – Select **Enter manually**. Select **600** for **Target value**.

   ![image](./Images/Lab05/image15.svg)

9. Select **Automatic** for **Status update method**. Click on **Set up status rules.**

    ![image](./Images/Lab05/image16.svg)
   
10. Click on **Add rule.**

    ![image](./Images/Lab05/image17.svg)
   
11. In the Operator dropdown menu, select **is greater than**. In the Value field, which currently shows **0**, enter **600**. Select **At risk** from the **Set status** to dropdown menu. This option specifies that if the check-in value is greater than 600 (the target value), then the organization is at risk and so the check-in will have a status of **At risk**. In the **Otherwise**, **set status to** dropdown menu, select **On track.**

    ![image](./Images/Lab05/image18.svg)
   
12. The above option specifies that if the condition isn't met during a check-in, then you're on track to meeting the goal and so the check-in will have a status of **On track**. The status rules should resemble the following image. Select **Confirm**.

13. Select **Save** on **Add a goal page**.

    ![image](./Images/Lab05/image19.svg)
    
14. The new goal should be visible in the list of goals for the scorecard.

    ![image](./Images/Lab05/image20.svg)

Great job, you have helped Amber create a goal for your scorecard instructing Wide World Importers to reduce their carbon emissions from 900 mtCO2E to 600 mtCO2E. You enabled automatic check-ins and status rules to ensure that the goal is automatically kept up to date. Goals are important to keep track of an organization’s progress towards reducing their carbon footprint. Any goals you have with a current value that is connected to data will have check-ins created roughly every 24 hours. Let’s go ahead and create our first check-in manually so you are familiar with the check-in data.  **Please continue to the next task**

### Task 3: Create a Goal Check-in

In this task, Amber will create a manual goal check-in Wide World Importers Scope 2 reduction goal, this will be for the first check-in, so they do not need to wait 24 hours for the first check-in to occur.

Sometimes we may have goals that are set to use manually check-ins if we are not able to connect data to them, or even after a goal with connected data is created, we need to wait roughly 24 hours for our first check-in to occur. In either of these situations, you may find it useful to be able to create and review a check-in. This task will take you through the process of creating a Goal Check-in.

1.  Amber opens the goal that was created in the previous task by selecting the goal name from the list in the scorecard.

2.  Amber can see:

    (1) **Progress** towards the Reduce Scope 2 Emissions - 2023 goal

    (2) The goal check-in **History**

    (3) The **Goal details**

    ![image](./Images/Lab05/image21.svg)


3.  In the **History** section, select either the **+** or the **Check-in** button to create a new Goal check-in for the first check-in.

    ![image](./Images/Lab05/image22.svg)

4.  A **New check-in** box will appear.

   ![image](./Images/Lab05/image23.svg)

5.  The fields are explained below:

    - **Update for** is used identify what date the check-in was for. This may be the current date or a date in the past.
    - **New value** is used to specify the current value of the goal check-in. This value will be used on the Progress chart above

        >[!NOTE]Note: In this scenario, the Status will be automatically set based on the Status rules we set on the goal

    - **Note** is optionally used if you want to provide more information or context about the check-in, such as a heatwave increased heating which resulted in an abnormally high carbon emission value for this check-in.

6.  Populate the **New check-in** with the following data:

    (1) **Update for**: Use today’s date.

    (2) **New value**: The preview value from the Source of current value connection screen. In this scenario, 379.59.

    (3) Select **Add Note** and set First check-in.

    (4) Select **Save**.

   ![image](./Images/Lab05/image24.svg)

   ![image](./Images/Lab05/image25.svg)

7.  Amber now sees:


    o	Use **Update for** to identify what date the check-in was for. This date might be the current date or a date in the past.

    o	Use **New value** to specify the current value of the goal check-in. This value will be used on the Progress chart.

**Note** - In this scenario, the **Status** will be set automatically based on the status rules that you've set on the goal.
    
    o	Using the **Note** box is optional if you want to provide more information or context about the check-in, such as a heatwave or increased heating that resulted in an abnormally high carbon emission value for this check-in.

Now, the **Progress** section should show as updated with the latest check-in value and status, as well its plot on the graph. Additionally, the **History** section should show the recently created check-in with the status automatically set based on the goal rules. Check-ins will be shown in the order of newest to oldest.

  ![image](./Images/Lab05/image26.svg)
  
Great job, you have helped Amber create a scorecard and goal to help Wide World Importers track carbon reduction progress. These tasks are critical to helping an organization realize their Sustainability goals. Some important notes:

-  **Automated Goal check-ins run via a backend service roughly every 24 hours**, based on the time of day when the Microsoft Cloud for Sustainability was installed.
-  **As of the current release, there is not a way to change the timing for Automated Goal check-ins**.
-  You can create a manual check-in at any time.
-  You can import historical Goal Check-ins by using the native Power Platform data import wizard. The Goal Check-in table is called **Check-ins**.

**Please continue to the next task.**


## Exercise 2: Set up Teams collaboration

In this exercise, Reed Flores – IT Admin for Wide World Importers will configure integration with Microsoft Teams for Microsoft Sustainability Manager. Microsoft Teams offers several features useful for organizations. By integrating Microsoft Cloud for Sustainability with Microsoft Teams, you can improve the collaboration between your sustainability team and improve the performance of your carbon reduction goals. You can quickly collaborate with colleagues utilizing Microsoft Teams Chat embedded in Dynamics 365.

**Note**: The following task, **Enable enhanced Teams Integration and Turn on Microsoft Teams chats inside Dynamics 365**” requires Global Administrator rights in your tenant. 

### Task 1: Enable enhanced Teams Integration and Turn on Microsoft Teams chats inside Dynamics 365

By default, the Basic and Enhanced Microsoft Teams integration is disabled in Microsoft Sustainability Manager. In this Task, Reed will enable Microsoft Teams in Dynamics 365.

1.  In the left navigation pane, under **Settings**, select **Teams chat**. 

3.  On the **Microsoft Teams collaboration and chat** page, switch **Turn on the linking of Dynamics 365 records to Microsoft Teams channels** to **Yes**. Select the **Save** button at the bottom left.

    ![image](./Images/Lab05/image29.svg)

4.  After the page finishes saving, switch **Turn on Enhanced Microsoft Teams Integration** to **Yes**.

     ![image](./Images/Lab05/image30.svg)

5.  Another pop-up window will open to grant permissions. Select the user you are signed in as currently (this account must be a global administrator).

6.  Select **Accept** for requested permissions. It may take several minutes to configure. Ensure you do not have pop ups blocked that may interfere with the communication. If so, turn off blockers for this website, cancel and try connecting again.

     ![image](./Images/Lab05/image31.svg)

7.  Once the dialog disappears, Select the **Save** button at the bottom left.

8.  Both Microsoft Teams Integration settings are now set to **Yes**.

     ![image](./Images/Lab05/image32.svg)

9.  On the **Microsoft Teams collaboration and chat** page, switch **Turn on Microsoft Teams chats inside Dynamics 365** to **Yes**. Click on **Save.**
 
    ![image](./Images/Lab05/image33.svg)

10.  Microsoft Teams chats inside Dynamics365 is now set to **Yes**, and a new section appears at the bottom of the screen called **Connect chats to Dynamics 365 records**.

     ![image](./Images/Lab05/image34.svg)

Great job, you have helped Reed enable Microsoft Teams integration for Dynamics 365 and turn on Microsoft Teams chats inside Dynamics 365. This will help Reed improve collaboration between teams and improve performance on goals. Please continue to the next task. **Please continue to the next task.**

### Task 2: Add Link chats to Dynamics 365 records

In this task, Reed will add a new Dynamics 365 record type, Factor Library, to the Link chats configuration. This feature allows other record types to be linked to Teams chats directly within Microsoft Sustainability Manager.

1.  Select **+Add Record Types** to add a Link chat configuration.

     ![image](./Images/Lab05/image35.svg)

2.  On the **Allow chats to be connected to this record type** form, select Factor library in the **Choose record type** lookup (you can scroll or type).

     ![image](./Images/Lab05/image36.svg)

3.  Set the **Join chat** and **New connected chats** toggles to **Yes**. Turn the slider to **Yes** for **Provide context for new linked chats**. Select **Factor libraries** under the **Message view** dropdown menu

    ![image](./Images/Lab05/image37.svg)

4.  Hovering the mouse over a view while the Message view list is open will give a preview of the message. The first 4-5 fields from the view are included in the message.

     ![image](./Images/Lab05/image38.svg)

5.  Select **Save**.
6.  Factor library is now visible in the list of connected record types.

     ![image](./Images/Lab05/image39.svg)
    
Great job, you have helped Reed turn on and configure a new Dynamics 365 record type, Factor Library, to the Link chats configuration. This will allow Reed to create linked Microsoft Teams chats directly inside of Cloud for Sustainability to discuss specific records. Next, we will test out the Microsoft Teams integration. **Please continue to the next task.**

### Task 3: Create a Microsoft Teams linked chat

In this task, Amber will create a linked chat to collaborate with a colleague to discuss the EPA 2022 - eGRID in preparation for 2022 reporting needs.

2.  Navigate to **Factor libraries** on the left side of the page under **Calculations**

     ![image](./Images/Lab05/image41.svg)

3.  Select the **EPA 2022 - eGRID** Factor library.

    ![image](./Images/Lab05/image42.svg)

4.  Select the **Chat** icon in the top right corner of the screen to open the Microsoft Teams chats inside of Cloud for Sustainability.

     ![image](./Images/Lab05/image43.svg)

5.  Select **New linked chat** to create a new chat window with another user to discuss changes to the Factor mappings on the EPA 2022 - eGRID Factor library.

    **Note**: You may need to wait a few minutes or perform a hard refresh (CTRL+F5) for the **New linked chat** button to appear the first time.

     ![image](./Images/Lab05/image44.svg)

6.  On the **New linked chat** blade:

    (1)  Search for chat **Participants** - for this scenario use one of the dummy accounts available, such as **Allen Deyoung**.

    **Important** - Allen Contoso may not be present in your environment, please select any available user or look up a newly added user.

    (2)  Enter a name for the Chat.

    (3)  Add a note to provide context for the chat to the participants.

    (4)  When finished, select **Start chat**.

   ![image](./Images/Lab05/image45.svg)

7.  In a few moments an embedded chat window with all participants will appear, and a message will be displayed with the note that was included, some of the record data, and a link to the record.

    ![image](./Images/Lab05/image46.svg)

Great job, you have helped Amber create a linked chat to collaborate with a colleague to discuss the EPA 2022 - eGRID in preparation for 2022 reporting needs.

**Congratulations!** Reed and Amber can now use the scorecard and its information in the new linked chat you set up with one of their colleagues to discuss changes to a factor library, continuing Ambers great work to record, report, and reduce carbon emissions across Wide World Importers and the entirety of Contoso corp. Linked chats can be used to help teams and organizations collaborate and improve efficiency by having the record context directly in the chat. You can configure many entities to have linked chats, as well as utilize custom system views to tailor the displayed fields to an organization’s needs.
