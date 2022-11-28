# Module 4 Lesson 1- Lab 1: Patient Outreach

### Overview

The **Patient Outreach** application in Microsoft Cloud for Healthcare allows healthcare providers to communicate with their communities and patients in a targeted, efficient way. Patient Outreach is a patient campaign management application that helps you organize and automate marketing and outreach to patients.

Key capabilities of **Patient Outreach** include:

-   Patient segmentation - Prebuilt patient segments are based on the industry standard Healthcare Effectiveness Data and Information Set (HEDIS) to provide baseline patient cohorts.
-   Patient engagement campaigns - Create healthcare-specific email campaigns that use patient segments based on the HEDIS industry standard.
-   Event management - Use provider and payer event management templates for event administration and registration.

Patient Outreach focuses on the **Enhance patient engagement** priority scenario by creating personalized communication based on patient insights.

![](media/df4dee19dba74e977d1d001c9dbd3a3d.png)

This lab focuses on the healthcare story of Elizabeth Moore.

![](media/6ec25178faea7cdb8abc9ae2bf891354.png)

At an annual checkup earlier this year, Elizabeth learned that she has hypermetropia, a common eye condition in adults in which nearby objects are blurry. Lamna Healthcare Company has seen a recent influx of patients who want to be more educated on hypermetropia and has decided to increase their patient outreach efforts by hosting a virtual marketing event.

In this lab, you will play the role of a Lamna Healthcare Company marketing administrator and will use the Patient Outreach capabilities in Microsoft Cloud for Healthcare to create a virtual marketing event.

### Learning objectives

In this lab, you will:

-   Create a patient segment.
-   Create a marketing email.
-   Create a patient journey.
-   Create a healthcare marketing event.

### Step 1: Create a Patient Segment

In this exercise, you will create a Patient Segment using the Patient Outreach app in Microsoft Cloud for Healthcare. A **Patient Segment** is used to group patients into cohorts based on similar characteristics so that they can be better targeted with marketing communications. In this example, you will create a Patient Segment for patients with hypermetropia (a vision condition in which nearby objects are blurry).

1.  While logged into your Microsoft 365 tenant, navigate to <https://make.powerapps.com/>.
1.  Go to Apps and open Marketing.

    ![Graphical user interface, text, application, email Description automatically generated](media/0c80e4c5c760423b6d4e4e2abda03e06.png)

1.  Navigate to the **bottom left drop-down** and change the selection from Marketing to **Settings**.

    ![Graphical user interface, text, application Description automatically generated](media/e72fa56c5f3c9527b0b0e58dbf7e4fc6.png)

1.  On the Settings overview screen, select **Dataset configuration** under Data management.

    ![Graphical user interface, application Description automatically generated](media/8018d431e68878191fbd44f227ab6dbc.png)

1.  Scroll down and select the **Condition (msemr_condition)** entity.

    ![Graphical user interface, text, application Description automatically generated](media/330743414440f627a1f4255c263b1b45.png)

1.  **Publish** **Changes** on the top right.

    ![Publish Changes.](media/077c825edf16384e8cfe22ed35173493.png)

    Note: While it may take up to 30 minutes for changes to take effect, they are generally ready in a few minutes.

1.  Go back to **Apps** and open **Patient Outreach**.

    ![Graphical user interface, text, application, email Description automatically generated](media/756d685076162bd7b183689ddf2c3d67.png)

1.  Click **Segments** on the left navigation bar to create a new specific group of patients.

    ![Click Segments to create a new specific group of patients.](media/e48936f82e9265eb2f56ab8a968aa15f.png)

1.  Click **New** to create a new Patient Segment. Select **+ New** **Dynamic Segment**.

    ![Click New to create a new Patient Segment.  Select + Dynamic Segment. ](media/2e14944f52f2405cd8d880626adc2886.png)

Did you know? Static segments enable you to choose and add segment members manually based on existing lists or search results. Dynamic Segments, which you define by using a set of rules and conditions, are constantly and automatically changing based on
