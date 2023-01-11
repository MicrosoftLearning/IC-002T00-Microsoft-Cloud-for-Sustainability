---
lab:
    title: 'Lab 3: Emission calculations'
    module: 'Module 5: Configure emission calculations'
---
# Module 5 Lesson 2 Lab 3: Emission calculations

## Overview

### Background

In the previous two labs, we laid the foundation for emission calculations by setting up the organization, reference data such as Contractual instrument types and ingesting the Activity data. Now that the groundwork and data has been laid for emission calculations, this lab will focus on performing the emission calculations using a combination of factor libraries, emission factors, estimation factors and calculation profiles. Once the calculations are performed, we will review the emission calculations output.

### Learning Objectives

In this lab, you will do the following:

-   Review the Microsoft Sustainability Manager’s Dynamic calculation capabilities using Factor libraries, Emission factors and more.
-   Review the existing “EPA 2022 - eGRID” factor library and emission factors
-   Create a new custom factor library for estimating miles to kilowatt hours (kWh)
-   Create new calculation models and new calculation profiles for calculation jobs
-   The emissions calculated during this lab exercise will be utilized in the remaining scenarios (reporting and goals) in the upcoming lab exercises.

### Prerequisites

-   Microsoft Sustainability manager environment is set up with sample data
-   Lab 01 organization and reference data is entered
-   Lab 02 activity data is ingested

### Solution Focus Area

In the Emission calculations focus area calculation models are designed to calculate the emissions produced by the ingested activity data. The setup of the calculations breaks it down into two concepts: factor mappings and calculation models. Currently, Sustainability Manager has been verified with EPA default calculations and factor sets only. Additional factor sets will be available over time. Any factor set can easily be added or created by organizations based on their own business needs and regional requirements.

The following terminologies will be used throughout the configuration of Emission Calculations:

-   **Estimation Factor**: Provides a way to convert from one unit type to another, such as night stays to kilowatt hour (kWh) used.
-   **Emission Factor**: Defines the amount of greenhouse gas emitted by a given unit type, this includes defining gas emissions such as CO<sub>2</sub>, CH<sub>4</sub>, and N<sub>2</sub>O.
-   **Factor Mapping**: Provides a way to map reference data to a specific emission factor, simplifying calculation models by allowing customers to choose a reference data type and allowing the system to find the appropriate emission factor.
-   **Factor Library**: A collection/grouping of emission or estimation factors and factor mappings, used by calculation models.
-   **Calculation Model**: Thought of as the instruction set used by the application to perform the emission calculations, utilizes factor libraries, factor mappings, and emission/estimation factors to perform the emission calculations.
-   **Calculation Profile**: Provides the scheduling for calculation jobs, defining activity data filter and the calculation model (instruction set) to use.

![Graphical user interface, application, Teams Description automatically generated](./Images/Lab03/L03_image001.png)

### Personas and Scenarios

In this lab, Alex Serra – Emissions Analyst for Wide World Importers sets up factor mappings for Purchased electricity for facilities, mapping Contractual instrument types to the Florida electric grid (FRCC).

Alex also creates a new estimation factor library for estimating miles driven to kilowatt hours (kWh) for Fabrikam electric trucks. Alex then creates calculation models for calculating the carbon emissions produced per the facility’s purchased electricity. Post that, Alex creates a calculation model for estimated carbon emissions produced by the purchased electricity for charging Fabrikam Electric trucks (based on the kWh per mile driven estimate).

Finally, Alex creates and runs calculation profiles, filtering to Wide World Importers activity data. Post running the Calculation profile, Alex reviews the calculated emissions data before notifying Amber Rodriguez – Sustainability specialist that the emission calculations are complete.

![Diagram Description automatically generated](./Images/Lab03/L03_image002.png)

In this lab exercise, we will focus on the scenarios illustrated below:

![Graphical user interface, application, Teams Description automatically generated](./Images/Lab03/L03_image003.png)

## Exercise 1: Set up Factor Libraries

In this exercise, you will learn about the steps that Alex takes to define the factor mappings for Purchased electricity, and an estimation factor library for estimating the amount of electricity purchased based on the Miles driven by Wide World Importers fleet of electric trucks. While electric vehicles do not have Scope 1, direct tailpipe emissions, they do have to be charged while transporting goods, in this case - across the USA. This charging of Electric trucks results in Scope 2 purchased electricity.

Wide World Importers may not know exactly how much electricity was purchased for charging the Electric Trucks, which grids the electricity came from, or what the energy source is. However, Wide World Importers can estimate the amount of electricity purchased by identifying how many kilowatt hours (kWh) are used per 100 miles, based on EPA vehicle efficiency data. You can explore this functionality in deeper detail on Microsoft Docs, please visit **Overview of Emission factors** at +++https://docs.microsoft.com/en-us/industry/sustainability/calculate-emission-factors+++.

1. Log into the virtual machine using the virtual machine credentials located on the **Resources** tab above.

1. Open a new browser window and navigate to +++https://make.powerapps.com+++.

1. Log into your Microsoft 365 tenant using the credentials for the tenant located on the **Resources** tab above.

1. If needed, change the environment to **MC4S** on the top bar.

1. Open the **Sustainability Manager** Application.

![Graphical user interface, application, Teams Description automatically generated](./Images/Lab03/L03_image004.png)

>[!ALERT] **Important** Please make sure that you have completed the previous lab to create Activity Data. **The emissions calculations require all the Data Ingestion processes from the previous lab to be completed.** Failure to do so will result in errors or incorrect values during the calculations

### Task 1: Add eGRID Factor mappings

In this task, Alex will create factor mappings to map the Contractual instrument types, for Wide World Importers that were added by Reed previously, to the respective electric grid emission factor. This allows Microsoft Sustainability Manager to find the correct electric grid for a given Contractual instrument type. This can be expanded to map other reference data to specific emission factors, avoiding the need to create calculations models that are for specific emission factors.

1.  In the bottom left corner, change your Area to **Data**.

    ![Graphical user interface, application, Teams Description automatically generated](./Images/Lab03/L03_image005.png)

1.  Navigate to **Factor libraries** on the left side of the page.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image006.png)

1.  Select the **EPA 2022 - eGRID** Factor library to open the Factor library. Make sure you have selected the **2022** library.

    >[!NOTE] **Note**: Microsoft Sustainability Manager includes EPA and IPCC based Factor libraries for emissions and estimations. Additional libraries are on the roadmap. Take time to review the existing factor libraries.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image007.png)

1.  Let’s take a moment to explore the **EPA 2022 - eGRID** factor library. The **General** tab includes identifying information about the Factor library.

    -   **Name**: this is used for identifying the factor library in the list.
    -   **Description**: this is used to provide more information about the factor library.
    -   **Documentation reference**: this is used to identify the documentation used to generate the factor library.
    -   **Type of factor library**: this is used to identify if this factor library is a Custom, Demo (sample), or Standard (pre-loaded based on EPA libraries).
    -   **Library type**: this functionally switches the library type between Emission or Estimation Library. Emission Libraries are used to calculate emission gases, and Estimation Libraries are used to create estimated conversions from one unit type to another, such as night stays at a hotel to kWh used.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image008.png)

1.  Select the **Emission factors** tab to see a list of Emission factors in the **Factor library**.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image009.png)

1.  The **Emission factors** list displays the name of the emission factor, the unit type, sub type, documentation reference, and gases generated. As Wide World Importers is a Florida based business and is connected to the FRCC electrical grid, select **FRCC (FRCC All)** from the list of **Emission factors**.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image010.png)

1.  The FRCC (FRCC All) Emission factor shows us the carbon emissions produced, 861lb of CO<sub>2</sub>, 0.055lb of CH<sub>4</sub>, and 0.007lb of N<sub>2</sub>O, **per megawatt hour (MWh) of energy consumed**.

    This information is important to understand how our final CO<sub>2</sub>E (Carbon equivalent) will be calculated later. When creating a new emission factor, you will want to define how much of each gas is produced per a given unit. There are several other gas types that can be tracked as seen on the screen, depending on the scenario some or all of them may be used.

    ![A screenshot of a computer Description automatically generated](./Images/Lab03/L03_image011.png)

1.  Return to **EPA 2022 - eGRID** by selecting the back arrow, and select the **Factors mapping** tab.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image012.png)

    >[!NOTE] **Note:** Factor mappings help map emission factors to reference data. Microsoft Sustainability Manager will use the factor mappings to find the correct emission factor to be used in an emission calculation for a given activity data. This is based on the reference data linked on the activity data, such as vehicle type or contractual instrument type.

1.  Alex will create factor mappings for the two Contractual instrument types created in previous labs and associate them to the FRCC (FRCC All) emission factor. Each of the Contractual instruments are local power providers in Florida and are part of the FRCC electric grid. Select **+New Factor mapping**.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image013.png)

1.  The fields are explained below.

    - The **Name** of the factor mapping is used for identifying the factor mapping in the list.
    - The **Reference Data** is mapping the Contractual Instrument Type.
    - The **Factor** is mapping the Emission Factor.

1.  Alex will use the following information to populate the fields on the **New Factor mapping**:

    (1) **Name**: +++FRCC - Purchased Electricity - VanArsdel Ltd+++

    (2) **Reference Data Name**: +++VanArsdel Ltd+++

    (3) **Factor**: +++FRCC (FRCC All)+++

    (4) Select **Save & Close** to save the record.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image014.png)

1.  Select **+New Factor mapping**.

    ![Graphical user interface, text Description automatically generated](./Images/Lab03/L03_image015.png)

1.  The fields are explained below.

    - The **Name** of the factor mapping is used for identifying the factor mapping in the list.
    - The **Reference Data** is mapping the Contractual Instrument Type.
    - The **Factor Library** is the library used.
    - The **Factor** is mapping the Emission Factor.

1.  Alex will use the following information to populate the fields on the **New Factor mapping**:

    (1) **Name**: +++FRCC - Purchased Electricity - Adatum Corp+++

    (2) **Reference Data**: +++Adatum Corp+++

    (3) **Factor**: +++FRCC (FRCC All)+++

    (4) Select **Save & Close** to save the record.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image016.png)

1.  There are now two additional **Factor mappings**, one for each of the contractual instruments added during the previous labs.

    ![Graphical user interface, text Description automatically generated](./Images/Lab03/L03_image017.png)

Great job, you have completed adding the factor mappings for the Purchased electricity activity data for Alex! This is an important step toward the creation of calculation models that will calculate emissions for multiple emission factors based on reference data, such as Contractual Instrument Types or Facilities. 

By creating these factor mappings, we can choose Contractual Instrument Types as emission factor during our calculation model creation. This tells Microsoft Sustainability Manager to map the contractual instrument type on an activity data record to the emission factor listed in the factor mapping. This allows you to create more dynamic calculations rather than calculations specific to a given emission factor. We will go into more detail on this later in this lab.  **Please continue to the next task.**

===

### Task 2: Create Estimation Factor Library

In this task, Alex will create an estimation factor library to define the estimation factor for estimating the kilowatt hours (kWh) used per miles driven. While electric vehicles do not have Scope 1, direct tailpipe emissions, they do have to be charged while transporting goods across the USA, resulting in Scope 2 purchased electricity. Wide World Importers may not know exactly how much electricity was purchased, what grid the electricity came from, or what the energy source is; however, Wide World Importers can estimate the amount of electricity purchased by identifying how many kilowatt hours (kWh) are used per 100 miles, based on EPA vehicle efficiency.

1.  Navigate to **Factor libraries** on the left side of the page.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image018.png)

1.  Select **Create new library**.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab03/L03_image019.png)

1.  The fields are explained below.

    - The **Name** of the factor library, this is used for identifying the factor library in the list.
    - The **Description** of the factor library is used to provide more information about the factor library for others.
    - The **Documentation reference** for the factor library is used to identify the documentation used to generate the factor library.
    - The **Type** of factor library is used to identify if this factor library is a Custom, Demo (sample), or Standard (pre-loaded based on EPA libraries).
    - The **Library Type** of the factor library, this functionally switches the library type between Emission or Estimation Library. Emission Libraries are used to calculate emission gases, and Estimation Libraries are used to create estimated conversions from one unit type to another, such as 100 miles driven to kWh.

1.  Alex will use the following information to populate the fields on the new Factor library:

    (1) **Name**: +++Electric Vehicle Estimation Library+++

    (2) **Description**: +++Scope 2 Emissions from Electric Vehicles+++

    (3) **Documentation reference**: +++https://fueleconomy.gov/feg/byfuel/EV2022.shtml+++

    (4) **Type**: Custom

    (5) **Library Type**: Estimation factor library

    (6) Select **Save & Close** saves the record.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image020.png)

Great job, you have helped Alex create an Estimation Library to define the estimation factor for estimating the kilowatt hours (kWh) used per miles driven. Estimation Libraries are the first step to utilizing estimations for emissions where you may not be able to determine the exact emissions. Some examples of estimations include estimating the amount of natural gas and electricity per hotel night stay during business travel, or vehicle fuel consumption by distance traveled. **Please continue to the next task.**

===

### Task 3: Create Estimation Factor

In this task, Alex will create the estimation factor for estimating the kilowatt hours (kWh) used per miles driven. The EPA estimates electric vehicle efficiency in kilowatt hours (kWh) per 100 miles. Alex will use this same metric in the estimation factor to ensure that the estimation factor is consistent with the EPA.

1.  On the **Factor library** view, select the **Electric Vehicle Estimation Library** (this will be near the bottom of your page).

    >[!NOTE] **Note**: For the purposes of this lab, we chose the largest electric vehicle available on the EPA, fueleconomy.gov website at the time of writing. **This is only an example**.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image021.png)

1.  Select the **Estimation Factors** tab.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image022.png)

1.  Select **+New Estimation factor**.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image023.png)

1.  The fields are explained below.

    - The **Name**, this is used for identifying the emission factor in the list.
    - The **Documentation reference**, this is used to identify the documentation used to generate the estimation factor.
    - The **Factor library** links the estimation factor to the factor library. This will default if you select “New Estimation factor” while you are in a factor library.
    - The **Unit** is used to identify what unit will be converted.
    - The **Factor value** is used to determine the amount to be estimated per the Factor value unit.
    - The **Factor value unit** is used to specify the unit type to be converted to.

1.  Alex reviews the Fabrikam electric truck details on the EPA website and determines the following information needs to be populated on the **New Estimation factor**:

    (1) **Name**: +++Fabrikam Electric Truck - EPA Estimate+++

    (2) **Documentation reference**: +++https://fueleconomy.gov/feg/noframes/45318.shtml+++

    (3) **Factor Library**: +++Electric Vehicle Estimation Library+++.

    (4) **Unit**: +++100 Mile+++

    (5) **Factor value**: +++49.00+++

    (6) **Factor value unit**: +++kWh+++

    (7) Select **Save & Close** to save the record.

    ![Graphical user interface, application Description automatically generated with medium confidence](./Images/Lab03/L03_image024.png)

1.  The **New Estimation factor** is estimating that every 100 miles is equivalent to 49 kWh.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image025.png)

Great job, you have helped Alex create an estimation factor for estimating the kilowatt hours (kWh) used per miles driven. Estimation factors are important to be able to convert from one unit type to another when an estimate is appropriate, such as estimated fuel or battery economy of vehicles, or estimating gas and electric utilization of hotel stays. **Please continue to the next task.**

===

## Exercise 2: Set up Calculation Models

In this exercise, you will learn about the steps that Alex takes to define Calculation Models used by Microsoft Sustainability Manager to calculate emissions. Calculation Models are the instruction sets, or recipes, which define all the steps and values to use during the emission calculations. Microsoft Sustainability Manager provides several calculation models.

Take the opportunity review some of the pre-built models, they are a great source of knowledge when creating new calculation models. The calculation models can also be used as a template for new models.. The algorithm used to calculate emissions will be discussed in this exercise and the next. You can explore this functionality in deeper detail on Microsoft Docs, please visit ***Overview of Calculation models*** at +++https://docs.microsoft.com/en-us/industry/sustainability/calculate-calculation-models+++.

### Task 1: Create Purchased Electricity Model

In this task, Alex will create a new calculation model to calculate carbon emissions for purchased electricity based on the contractual instrument type. They will leverage the factor mappings created in the previous exercise to make the calculation model dynamically find the emission factor to be used per line of activity data.

1.  Navigate to **Calculation models** on the left side of the page.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image026.png)

1.  Select **+New** to create a new Calculation model.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab03/L03_image027.png)

1.  A new page will open to configure the Calculation model. A source action is added by default.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab03/L03_image028.png)

1.  The fields are explained below.

    - The **Category name** is used for identifying the calculation model in the list.
    - The **Activity data** is used to identify which type of activity data the model will process.
    - The **Calculation method** is used to roughly note what the calculation will be doing.
    - The **Documentation reference** is used to identify the documentation used to create the calculation model.

1.  Populate the **Source** action with the following data:

    (1) **Category name**: +++Purchased Electricity: Contractual Instrument Based - 2022+++

    (2) **Activity data**: Purchased electricity

    (3) **Calculation method**: +++EPA Equation 1: Electricity (MWh) \* EF+++

    (4) **Documentation reference**: +++https://www.epa.gov/sites/default/files/2020-12/documents/electricityemissions.pdf+++

    (5) Select **Save** to save the record.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image029.png)

1.  Select the **+** to add a new action to the calculation model.

    ![Graphical user interface, application Description automatically generated with medium confidence](./Images/Lab03/L03_image030.png)

1.  Select **Report** on the list of **Available actions**.

    >[!NOTE] **Note**: Only **Source**, **Report**, and **Estimation** actions are covered in this lab. Additional details about each available action can be found in **Calculation models** at +++https://docs.microsoft.com/en-us/industry/sustainability/calculate-calculation-models#add-a-calculation-model+++.

    ![Graphical user interface, application, website Description automatically generated](./Images/Lab03/L03_image031.png)

1.  A new **Report** action is added to the Calculation model. Select that action to configure it.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image032.png)

    The **Report** action is used to calculate and report carbon emissions to the emissions table. This action will use the emission factor or factor mapping to identify the emission factor to be used, based on the emission factor dropdown. In this lab, the action will use contractual instrument type field to identify the factor mapping and emission factor to use in the calculation.

    Once the emission factor for the activity data line has been determined, the activity data quantity and quantity unit will be converted to the same unit type as the emission factor. In this lab, the kWh from the Activity data will be converted to MWh.

    After the quantity has been converted, the converted value will be multiplied against each gas listed in the emission factor, determining the volume of gases produced.

    To determine the CO<sub>2</sub>E (Carbon Dioxide Equivalency), the gases produced are multiplied against their GWP factor (Global Warming Potential factor), which is stored in the “Greenhouse Gases” Dataverse table and are added together.

    The **Report** action stores the gases produced values, CO<sub>2</sub>E value, and other identifying information about the activity data row in the emissions table.

1.  The fields are explained below.

    >[!NOTE] **Note**: This value can also be determined by a Power Fx expression if a more complex value is needed instead of a specific field.

    - The **Category name** is used for identifying the action in the calculation model.
    - The **Description** is used to roughly note what the calculation will be doing.
    - The **Emission report value** is used to identify which field from the activity data type should be used to retrieve the value used in the emission calculation.
    - The **Unit** is used to identify the field from the activity data type to be used to retrieve the unit type of the value. Alternatively, a unit can be specified to always be used in the action, regardless of which unit is specified on the activity date type.
    - The **Emission factor library** is used to identify which factor library will be used to identify the emission factor.
    - The **Emission factor** is used to identify which emission factor or factor mapping will be used to calculate the emissions. Choosing a factor mapping will allow multiple reference data values to map to an emission factor, allowing for a calculation model to not be bound to a single emission factor.

1.  Populate the **Report action** with the following data:

    (1) **Category name**: +++Electricity \* EF (Contractual Instrument Type)+++

    (2) **Description**: +++EPA Equation 1: Electricity (MWh) \* EF+++

    (3) **Emission report value**: Quantity

    (4) **Unit**: Quantity unit

    (5) **Emission factor library**: EPA 2022 - eGRID

    >[!NOTE]**Note**: There are several libraries with similar names. Make sure you select **EPA 2022 - eGRID** from the dropdown.

    (6) **Emission factor**: Contractual Instrument Type

    (7) Select **Save** to save the record.
 
    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image033.png)

1.  Select the back arrow on the record to return to the list of Calculation models.

    ![Text Description automatically generated with low confidence](./Images/Lab03/L03_image034.png)

1.  The new Calculation model should now appear in the list.

    ![A screenshot of a computer Description automatically generated](./Images/Lab03/L03_image035.png)

Great job, you have helped Alex create a new Calculation model to calculate carbon emissions for purchased electricity based on the contractual instrument type. This will be used in Exercise 3. In this Calculation model you utilized factor mappings, an important differentiator for Microsoft Cloud for Sustainability. Factor mappings allow the Calculation models to be more dynamic by mapping reference data to emission factors, allowing you to have one model that can calculate for multiple emission factors. 

Calculation models are the instruction sets that are used by Microsoft Cloud for Sustainability to calculate emissions. There are several calculation models that are included with Microsoft Cloud for Sustainability based on EPA calculations. Sometimes these included models may not match your unique customer needs and you will need to create new models to provide custom calculations, be sure to review some of the included models to see other types of complex calculation models. **Please continue to the next task.**

===

### Task 2: Create Electric Vehicle Miles Driven Model

In this task, Alex will create a new calculation model to calculate carbon emissions for miles driven by electric vehicles. They will leverage the estimation factor library created in the previous exercise to first estimate the kilowatt hours (kWh) used by an electric vehicle, then calculate the carbon emissions for that electricity based on the US Average emission factor.

1.  Navigate to **Calculation models** on the left side of the page, if necessary.

    ![Application Description automatically generated with low confidence](./Images/Lab03/L03_image036.png)

1.  Select **+New** to create a new Calculation model.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab03/L03_image037.png)

1.  A new page will open to configure the Calculation model. A source action is added by default.

    ![Graphical user interface, application, Teams Description automatically generated](./Images/Lab03/L03_image038.png)

1.  The fields are explained below.

    - The **Category name** is used for identifying the calculation model in the list.
    - The **Activity data** is used to identify which type of activity data the model will process
    - The **Calculation method** is used to roughly note what the calculation will be doing.
    - The **Documentation reference** is used to identify the documentation used to create the calculation model

1.  Populate the Source action with the following data:

    (1) **Category name**: +++Electric Vehicle Miles Driven - 2022+++

    (2) **Activity data**: Purchased electricity

    (3) **Calculation method**: +++Miles Driven to kWh \* EF+++

    (4) **Documentation reference**: +++https://fueleconomy.gov/feg/byfuel/EV2022.shtml+++

    (5) Select **Save** to save the record.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image039.png)

1.  Select the **+** to add a new action to the calculation model.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image040.png)

1.  Select **Estimation factor** on the list of **Available actions**.

    ![Graphical user interface, application, website, Teams Description automatically generated](./Images/Lab03/L03_image041.png)

1.  A new action is added to the Calculation model. Select that action to configure it.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image042.png)
    
    The **Estimation factor** action is used to create an estimated value for converting one unit type to another in a different unit group, such as converting night stays to kilowatt hours (kWh) used. This is important when it may be difficult to know the exact amount of a given emission source that is used. In this lab, the action will be used to convert miles driven by the fleet of electric vehicles to kWh used. This helps Wide World Importers estimate the carbon emissions for their fleet of electric vehicles that are driving across the USA and may be charging various amounts and on different grids and energy sources.

    The activity data quantity and quantity unit will be converted to the same unit type as the estimation factor. In this lab, the mile unit from the Activity data will be converted to 100 mile units.

    After the quantity has been converted, the converted value will be multiplied against the Factor quantity and stored in the output variable. The output variable is only accessible within the calculation model, available for use by actions further down the chain. The estimated value will not be stored in a table.

1.  The fields are explained below.

    - The **Category name** is used for identifying the action in the calculation model.
    - The **Estimation value** is used to identify which field from the activity data type should be used to retrieve the value used in the estimation calculation.

    >[!NOTE] **Note**: This value can also be determined by a Power Fx expression if a more complex value is needed instead of a specific field.

    - The **Unit** is used to identify the field from the activity data type should be used to retrieve the unit type of the value. Alternatively, a unit can be specified to always be used in the action, regardless of which unit is specified on the activity date type.
    - The **Estimation factor library** is used to identify which factor library will be used to identify the estimation factor.
    - The **Estimation factor** is used to identify which estimation factor or factor mapping will be used calculate the estimation. In this scenario only one estimation factor has been created so, it does not make sense to select a factor mapping currently.
    - The **Output variable name** is used to name the output of the estimation factor calculation for use in actions further down the chain.

1.  Populate the Estimation factor action with the following data:

    (1) **Category name**: +++Estimate kWh/100 Mile+++

    (2) **Estimation value**: Quantity

    (3) **Unit**: Quantity unit

    (4) **Estimation factor library**: Electric Vehicle Estimation Library

    (5) **Estimation factor**: Fabrikam Electric Truck - EPA Estimate

    (6) **Output variable name**: +++kWhQuantity+++

    (7) Select **Save** to save the record.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image043.png)

1.  Select the **+** to add a new action to the calculation model.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image044.png)

1.  Select **Report** on the list of Available actions

    ![Graphical user interface, application, website Description automatically generated](./Images/Lab03/L03_image045.png)

1.  A new action is added to the Calculation model. Select that action to configure it.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image046.png)

1.  The fields are explained below. 

    - The **Category name** is used for identifying the action in the calculation model.
    - The **Emission report value** is used to identify which field should be used to retrieve the value used in the emission calculation. In this scenario, the Output variable from the Estimation factor action is used.

    >[!NOTE] **Note**: In this scenario, the Unit is automatically selected based on the Unit type of the Output variable from the Estimation factor node

    - The **Emission factor library** is used to identify which factor library will be used to identify the emission factor.
    - The **Emission factor** is used to identify which emission factor or factor mapping will be used to calculate the emissions. In this scenario, Alex and Wide World Importers may not know which electric grid a vehicle was charged on or the energy source, so Alex chooses the US Average emission factor to provide the estimated emissions.

1.  Populate the Report action with the following data:

    (1) **Category name**: +++kWh \* EF+++

    (2) **Emission report value**: kWhQuantity and **Unit**: kWh

    (3) **Emission factor library**: EPA 2022 - eGrid (make sure you select the correct library)

    (4) **Emission factor**: +++US Average+++

    (5) Select **Save** to save the record.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image047.png)

1.  Select the back arrow on the record to return to the list of Calculation models.

    ![A picture containing logo Description automatically generated](./Images/Lab03/L03_image048.png)

1.  The new Calculation model should now appear in the list.

    ![A screenshot of a computer Description automatically generated](./Images/Lab03/L03_image049.png)

Great job, you have helped Alex create another new Calculation model to calculate carbon emissions for miles driven by electric vehicles. This Calculation model included an estimation factor, allowing Alex to calculate emissions in areas where he may not know the exact quantity of an emission source, but still needs to account for the carbon emissions.  This model will be used in the following exercise. 

Calculation models are the instruction sets that are used by Microsoft Cloud for Sustainability to calculate emissions. There are several calculation models that are included with Microsoft Cloud for Sustainability based on EPA calculations. Sometimes these included models may not match your unique customer needs and you will need to create new models to provide custom calculations, be sure to review some of the included models to see other types of complex calculation models. **Please continue to the next task.**

===

## Exercise 3: Run Calculations

In this exercise, you will learn about the steps that Alex takes to define and run Calculation Profiles. Microsoft Sustainability Manager uses calculation profiles to define the parameters and scheduling of calculation jobs. Calculation profiles allow an organization to define what activity data to calculate emissions for, any filters on that data, which Calculation model to use, and if the calculation should be redone every time the chosen activity data changes. Calculation profiles use the parameters to create calculation jobs, which are the background worker jobs iterating over an organization’s activity data and determining the carbon emissions, based on the calculation model defined in the calculation profile. You can explore this functionality in deeper detail on Microsoft Docs, please visit **Overview of Calculation profiles** at +++https://docs.microsoft.com/en-us/industry/sustainability/calculate-calculation-models#calculation-profile+++.

### Task 1: Create Purchased Electricity Calculation Profile

In this task, Alex will create a Calculation Profile for the electricity purchased by Wide World Importers for their facilities for the year 2022. Alex will use the calculation model defined early in this lab and filter the profile to only activity data for the Wide World Importers organizational unit, and where the unit type is kWh. These filters will ensure that only the purchased electricity for Wide World Importers is included in the calculation job. This will exclude the miles driven by the fleet of electric vehicles, which is covered in the next task.

1.  Navigate to **Calculation profiles** on the left side of the page.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image050.png)

1.  Select **+New Calculation profile** to create a new Calculation profile.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image051.png)

1.  The first fields of the **New calculation profile** wizard are explained below:

    -  The **Calculation profile** name is used for identifying the calculation profile in the list.
    -  The **Emission source** is used to identify which activity data type should be used in the calculation.
    -  The **Activity data to include calculation** filter is used to filter activity data to a specific subset of the activity data type.  
 
1.  Populate them with the following information: 

    (1) **Calculation profile name**: +++Purchased Electricity: Contractual Instrument Based 2022 Wide World Importers+++

    (2) **Emission source**: Purchased electricity

    (3) **Activity data to include in calculation**: Organizational Unit equals Wide World Importers AND Quantity Unit equals kWh
   
    To create the filter perform the following steps:

    1.  Select **Add -> Add row**.

        ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image052.png)

    1.  In the **Select a field** dropdown, choose **Organizational Unit**.

        ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image053.png)

    1.  In the **Value** dropdown, choose **Wide World Importers (Organizational unit)**.
        
        ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image054.png)

    1.  Select **Add -> Add row** again.

        ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image055.png)

    1.  In the **Select a field** dropdown, choose **Quantity unit**.

        ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image056.png)

    1.  In the **Value** dropdown, choose **kWh**.

        ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image057.png)

1.  The final fields of the **New calculation profile** wizard are explained below:

    - The **Calculation model** is used to identify which calculation model should be used for the calculation. Choose the **Calculation model** from the dropdown list. 
    - **Automatically run this calculation when data is refreshed** is used to automatically trigger calculations when the matching activity data is refreshed.

1. Set the remaining fields as follows:

    (4) Select +++**Purchased Electricity: Contractual Instrument Based - 2022**+++ in the **Calculation model** dropdown list

    (5) Check **Schedule Automatically run**.

    (6) The form should resemble the image below. Select **Next**.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image058.png)

    On the **Preview** page of the New calculation profile wizard the emissions are calculated for the first row of data that matches the Activity data to include filter.

    These values were determined by converting the consumed kWh to MWh: 3519.038/1000 = 3.519038 MWh

    The values of emissions gasses are determined by multiplying the converted consumption by each of the greenhouse gas factors from the emission factor (FRCC) determined in the factor mapping:

    -   CO<sub>2</sub>: 3.519038 \* 861 = 3,029.892 lb
    -   CH<sub>4</sub>: 3.519038 \* .055 = 0.194 lb
    -   N<sub>2</sub>O: 3.519038 \* .007 = 0.025 lb

    Finally, multiplying the greenhouse gases by their GWP factor (Global Warming Potential) found in the Greenhouse gases table, and adding up the values.

    >[!NOTE] **Note**: The values in this by hand demonstration have been rounded to 3 decimal points resulting in a slightly different value. Microsoft Sustainability Manager computes up to 10 decimal points

    -   CO<sub>2</sub>: 3,029.892 \* 1 = 3,029.892 lb
    -   CH<sub>4</sub>: 0.194 \* 25 = 4.85 lb
    -   N<sub>2</sub>O: 0.025 \* 298 = 7.45 lb
    -   CO<sub>2</sub>E: 3,029.892 + 4.85 + 7.45 = 3,042.19 lb

1.  You can select **Save** to save your Calculation profile.

    >[!NOTE] **Note:** In this scenario, the values seen in the preview may be different than the image below. If your preview does not show up, it is OK.**

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image059.png)

Great job, you have helped Alex create a calculation profile for the electricity purchased by Wide World Importers for their facilities for the year 2022. This profile used the calculation model defined early in this lab. The profile was filtered to only activity data for the Wide World Importers organizational unit, and where the unit type is kWh. 

Calculation profiles are the mechanisms by which Calculation jobs are queued. You can set your Calculation profiles to run automatically when matching Activity Data is added or updated, as we chose in this scenario, or you can run them manually which we will discuss in Task 3 of this exercise. **Please continue to the next task.**

===

### Task 2: Create Electric Vehicle Miles Driven Calculation Profile

In this task, Alex will create a Calculation Profile for the miles driven by Wide World Importers’ fleet of electric vehicles for year 2022. They will use the calculation model defined earlier in this lab and filter the profile to only activity data for the Wide World Importers organizational unit, and where the unit type is mile. These filters will ensure that only the miles driven for Wide World Importers’ fleet of electric vehicles is included in the calculation job. This will exclude the purchased electricity, which was covered in the previous task.

1.  Navigate to **Calculation profiles** on the left side of the page, if necessary.

    ![Graphical user interface, text, application Description automatically generated with medium confidence](./Images/Lab03/L03_image060.png)

1.  Select **+New Calculation profile** to create a new Calculation profile.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image061.png)

1.  The first fields of the New calcualtion profile are explained below:

    -  The **Calculation profile name** is used for identifying the calculation profile in the list.
    -  The **Emission source** is used to identify which activity data type should be used in the calculation.
    -  The **Activity data to include in calculation** filter is used to filter activity data to a specific subset of the activity data type.

1.  Populate them with the following information:

    (1) **Calculation profile name**: +++Electric Vehicle Miles Driven 2022+++

    (2) **Emission source**: Purchased electricity

    (3) **Activity data to include in calculation**: Organizational Unit equals Wide World Importers AND Quantity unit equals mile
     
    To create the filter perform the following steps:

    1.  Select **Add -> Add row**.

        ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image062.png)
        
    1.  In the **Select a field** dropdown, choose **Organizational Unit**.

        ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image063.png)

    1.  In the **Value** dropdown, choose **Wide World Importers (Organizational unit)**.

        ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image064.png)

    1.  Select **Add -> Add row** again.

        ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image065.png)

    1.  In the **Select a field** dropdown, choose **Quantity unit**.

        ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image066.png)

    1.  In the **Value** dropdown, choose **mile**.

        ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image067.png)

1.  The final fields of the New calculation profile wizard are explained below:

    - The **Calculation model** is used to identify which calculation model should be used for the calculation. Choose the **Calculation model** from the dropdown list
    - **Automatically run this calculation when data is refreshed** is used to automatically trigger calculations when the matching activity data is refreshed.

1. Set the remaining fields as follows:

    (4) Select **Electric Vehicle Miles Driven - 2022** from the **Calculation model** dropdown list.   

    (5) Check **Schedule Automatically run**.

    (6) The form should resemble the image below. Select **Next**.

    ![Graphical user interface Description automatically generated with medium confidence](./Images/Lab03/L03_image068.png)

    On the **Preview** page of the New calculation profile wizard you will see the emissions calculated for the first row of data that matches your Activity data to include filter. 

    These values were determined by converting the miles driven to kWh: (7484.724 / 100) \* 49 = 3667.515 kWh

    The consumed kWh converted to MWh: 3667.515/1000 = 3.667515 MWh

    Multiplying the converted consumption by each of the greenhouse gas factors from the emission factor (FRCC) determined in the factor mapping:

    -   CO<sub>2</sub>: 3.667515 \* 861 = 3,001.127 lb
    -   CH<sub>4</sub>: 3.667515 \* .055 = 0.238 lb
    -   N<sub>2</sub>O: 3.667515 \* .007 = 0.033 lb

    Finally, multiplying the greenhouse gases by their GWP factor (Global Warming Potential) found in the Greenhouse gases table, and adding up the values.

    >[!NOTE]**Note**: The values in this by hand demonstration have been rounded to 3 decimal points resulting in a slightly different value. Microsoft Sustainability Manager computes up to 10 decimal points.

    -   CO<sub>2</sub>: 3,001.127 \* 1 = 3,001.127 lb
    -   CH<sub>4</sub>: 0.238 \* 25 = 5.95 lb
    -   N<sub>2</sub>O: 0.033 \* 298 = 9.834 lb
    -   CO<sub>2</sub>E: 3,001.127 + 5.95 + 9.834 = 3,016.911 lb

1. You can select **Save** to save your Calculation profile and select **Done** if necessary.

>[!NOTE]**Note**: In this scenario, the values seen in the preview may be different than the image below.

![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image069.png)

Great job, you have helped Alex create another calculation profile using the calculation model defined earlier in this lab. You filtered the profile to only activity data for the Wide World Importers organizational unit, and where the unit type is mile to ensure ensure that only the miles driven for Wide World Importers’ fleet of electric vehicles is included in the calculation job. 

Calculation profiles are the mechanisms by which Calculation jobs are queued. You can set your Calculation profiles to run automatically when matching Activity Data is added or updated, as we chose in this scenario, or you can run them manually which we will discuss in Task 3 of this exercise. **Please continue to the next task.**

===

### Task 3: Run Calculation Profiles

In this task, Alex will run the newly created Calculation Profiles for the electricity purchased by Wide World Importers and miles driven by Wide World Importers fleet of electric vehicles. This will create a calculation job that will iterate over each activity data row matching the Calculation Profile filter criteria and use the Calculation Models created earlier in this lab to calculate the carbon emissions for each row. The results will be placed in the emissions table, which Alex will review once the calculations complete.

1.  Navigate to **Calculation profiles** on the left side of the page, if necessary.

    ![Graphical user interface, text, application Description automatically generated with medium confidence](./Images/Lab03/L03_image060.png)

1.  To run the calculation profile for **Purchased Electricity: Contractual Instrument Type - 2022**:

    (1) Select **Purchased Electricity: Contractual Instrument Based - 2022 - Wide World Importers** in the list.

    (2) Select **Run calculation** on the command bar.

    ![Graphical user interface, text, application Description automatically generated](./Images/Lab03/L03_image071.png)

1.  To run the calculation profile for **Electric Vehicle Miles Driven - 2022**:

    (1) Select **Electric Vehicle Miles Driven - 2022** in the list.

    (2) Select **Run calculation** on the command bar.

    ![Graphical user interface, text, application, email Description automatically generated](./Images/Lab03/L03_image072.png)

1.  After several minutes (approximately 6 minutes) both calculation jobs should be completed. Alex selects the **Refresh** button on the command bar to check the status of the calculation jobs. The two Calculation profiles should now have a status of **Succeeded**. If you are unable to see the column with **Succeeded**, you can scroll to the bottom and then to the right.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab03/L03_image073.png)

1.  In the bottom left corner, change the Area to **Analytics**.

    ![Graphical user interface, text, application, chat or text message Description automatically generated](./Images/Lab03/L03_image074.png)

1.  Navigate to **All emissions** on the left side of the page.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image075.png)

1.  The All emissions view shows all emissions that have been calculated or directly imported.

    ![A screenshot of a computer Description automatically generated](./Images/Lab03/L03_image076.png)

1.  Filter the view by selecting the down arrow next to the **Organizational Unit** column, and selecting **Filter by**. If you are unable to see the column with **Succeeded**, you can scroll to the bottom and then to the right. 

    ![Graphical user interface, application, Word Description automatically generated](./Images/Lab03/L03_image077.png)

1.  Select **Wide World Importers** from the **Filter By** dialog.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image078.png)

1.  Select **Apply** to apply the filter to the column.

    ![Graphical user interface, application Description automatically generated](./Images/Lab03/L03_image079.png)

1.  After a few moments, the view will refresh, and the calculated emissions data for each of the activity data records imported in previous labs will be shown. Scroll to the right to see the CO<sub>2</sub>E carbon emission values.

    ![A screenshot of a computer Description automatically generated](./Images/Lab03/L03_image080.png)

Great job, by completing these steps you have helped Alex, the Emissions Analyst, run the newly created Calculation Profiles for the electricity purchased by Wide World Importers and miles driven by Wide World Importers fleet of electric vehicles.

**Congratulations!** Alex and Amber, the Sustainability specialist, can now review the Wide World Importers' results produced from the emission calculations you performed to make better decisions regarding the company's carbon emissions. You did these calculations using factor libraries, emission factors, estimation factors and calculation profiles. Calculation profiles are the final step in calculating and recording your carbon emissions in Microsoft Cloud for Sustainability. From here you will be able to Report and Reduce your carbon emissions, which we will discuss in the next labs. It may take 30 minutes for your emissions to appear in the Reporting areas.
