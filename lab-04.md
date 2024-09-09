[Introduction
[3](#_Toc170369881)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369881)

[Medallion Framework within KQL Databases
[4](#_Toc170369882)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369882)

[Task 1: Create Bronze Tables
[4](#_Toc170369883)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369883)

[Task 2: Load Broze Tables
[7](#_Toc170369884)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369884)

[Task 3: Transform Tables in Silver Layer
[12](#_Toc170369885)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369885)

[Task 4: Create Gold Layer with Materialized Views
[16](#_Toc170369886)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369886)

[Fabric Lakehouse and OneLake Availability
[19](#_Toc170369887)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369887)

[Task 5: Create Lakehouse
[19](#_Toc170369888)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369888)

[Task 6: Shortcut to KQL Database Tables
[20](#_Toc170369889)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369889)

[Summary
[22](#_Toc170369890)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369890)

[References
[23](#_Toc170369891)](file:///C:\Users\Shivashant\Downloads\RTIAD%20Templates\RTIAD\RTIAD\Lab%204.docx#_Toc170369891)

[]{#_Toc170369879 .anchor}**Document Structure**

The lab includes steps for the user to follow along with associated
screenshots that provide visual aid. In each screenshot, sections are
highlighted with orange boxes to indicate the area(s) user should focus
on.

[]{#_Toc170369881 .anchor}**Introduction**

In this lab, you will create a Medallion Framework using the Bronze,
Silver, Gold layer approach to handling data in it's different stages of
development and use in analytics. You will then connect the data from
your KQL Database into a Lakehouse to showcase how quickly you can share
your real-time data with those in your organization who want to use it
for Power BI reporting.

By the end of this lab, you will have learned:

-   Creating KQL Database Tables with the Kusto Query Language

-   Loading data into KQL Databases with Data Factory Pipelines

-   Creating Materialized Views in KQL Databases

-   Creating a Lakehouse and Using Shortcuts to the KQL Database

[]{#_Toc170369882 .anchor}**Medallion Framework within KQL Databases**

[]{#_Toc170369883 .anchor}Task 1: Create Bronze Tables

26. Open the **Fabric workspace** for the course and open the KQL
    Queryset you created in the last lab, **Create Tables**.

![A screenshot of a
computer](./media/image127.png){width="4.166666666666667in"
height="3.0555555555555554in"}

27. Within the KQL Queryset paste and **Run** the following code to
    create four new tables that will serve as your Bronze Layer of the
    Medallion Framework.

![](./media/image128.emf)

![A blue screen with black text Description automatically
generated](./media/image129.png){width="4.083333333333333in"
height="0.9916666666666667in"}

28. Once that executes you should immediately see four new tables
    created within your Database Object Explorer.

-   Address

-   Customer

-   SalesOrderDetail

-   SalesOrderHeader

![A screenshot of a computer Description automatically
generated](./media/image130.png){width="2.0833333333333335in"
height="2.4375in"}

29. Expand the **Address table** by click on the **\>** icon next to the
    name.

![A screenshot of a
computer](./media/image131.png){width="1.4583333333333333in"
height="3.2083333333333335in"}

30. This shows you the schema (column names and data types) for the
    table. One thing that will be helpful to add to this table on the
    KQL Database would be a hidden column for the ingestion time that
    will be used later in the Medallion architecture. Let's add that
    now. Copy and paste the script below to alter the tables you just
    created by adding an ingestion time column.

![](./media/image132.emf)

![A screenshot of a computer Description automatically
generated](./media/image133.png){width="5.073611111111111in"
height="2.202777777777778in"}

31. The four new tables are blank tables with their schema defined. Now
    you need a way to properly load these tables. Navigate back to your
    workspace **RTI_username**.

[]{#_Toc170369884 .anchor}Task 2: Load Broze Tables using a Data Pipline

1.  From the new dropdown menu find and select the option called **Data
    pipeline**.

![A screenshot of a computer Description automatically
generated](./media/image134.png){width="2.55in"
height="1.725in"}

2.  Give the new pipeline the name, **Load KQL Database**.

![A screenshot of a computer Description automatically
generated](./media/image135.png){width="2.7in"
height="2.091666666666667in"}

3.  Click on **Create**.

4.  When the pipeline menu appears, click on the **Copy data assistant**
    option.

![A screenshot of a computer Description automatically
generated](./media/image136.png){width="6.506944444444445in"
height="2.5104166666666665in"}

5.  To begin, you will need to create a connection to the source
    database from where you wish to extract the data. Click on the
    **Azure SQL database** option under New sources. If you do not see
    it immediately you can use the search bar at the top to filter
    sources. We will be connecting to the same external Azure SQL
    database from the prior lab but connecting to different tables.

![A screenshot of a
computer](./media/image137.png){width="5.069444444444445in"
height="2.3541666666666665in"}

6.  You will need to input the connection details of the database.
    Follow using the information in your environment or as below.

-   adxdemo.database.windows.net

-   aworks

-   sqlread

-   ChangeYourAdminPassword1

![A screenshot of a computer Description automatically
generated](./media/image138.png){width="2.9652777777777777in"
height="3.4166666666666665in"}

7.  Click **Next** when everything has been filled out.

8.  From the list of avaliable tables, select the following.

-   SalesLT.Address

-   SalesLT.Customer

-   SalesLT.SalesOrderDetail

-   SalesLT.SalesOrderHeader

![A screenshot of a computer Description automatically
generated](./media/image139.png){width="1.8388888888888888in"
height="3.8125in"}

9.  Click on **Next**.

10. You will now be required to set up your destination to determine
    where you want the pipeline to send the data to. Find the **OneLake
    data hub** and then select your KQL database, **eh_Fabrikam**.

![A screenshot of a
computer](./media/image140.png){width="3.125in"
height="1.8541666666666667in"}

11. Click on the **SalesLT.Address** table if it is not already selected
    and then click on the dropdown next to the **Table** option. Click
    on the **Address** table option.

![A screenshot of a
computer](./media/image141.png){width="5.3125in"
height="2.0347222222222223in"}

12. You will now see an overview of the **Column mappings**. This will
    allow you to visualize all the fields coming from the source
    database that you are sending to your KQL Database. You have an
    option to remove specific fields if you do not want them to map over
    from the source.

![A screenshot of a computer Description automatically
generated](./media/image142.png){width="5.489583333333333in"
height="3.13125in"}

13. Follow the same steps as Step 11-12 for the tables
    **SalesLT.Customer**, **SaleLT.SalesOrderDetail**, and
    **SalesLT.SalesOrderHeader**. No column mappings will need to be
    performed so simply match up the table names. Once all tables have
    been appropriately mapped, click on **Next**.

14. The final page using the Copy Data Assistant is an overview page to
    verify all the settings you've selected. Ensure that your source
    number of tables and destination number of tables are the same.

![A screenshot of a
computer](./media/image143.png){width="5.555555555555555in"
height="2.8680555555555554in"}

15. Click on **Save + Run**.

16. After a few moments a flyout window will appear that includes a
    **Parameter**. The copy assistant wizard which we just completed,
    created a list of the tables to iterate though and load into the kql
    tables. Simply click on the **OK** button to run the pipeline as it
    is currently configured from the Copy Data Assistant.\
    \
    ![A screenshot of a computer Description automatically
    generated](./media/image144.png){width="4.227777777777778in"
    height="2.716666666666667in"}

17. Let the pipeline run and after approximately one minute, the data
    movement should be complete. Once you see that all activities within
    the pipeline have **Succeeded**, you will have transferred the
    data.\
    \
    ![A screenshot of a computer Description automatically
    generated](./media/image145.png){width="3.5229166666666667in"
    height="2.060416666666667in"}

18. Let's go and check one of our tables and verify the data. Navigate
    back to the KQL Queryset we have been using called **Create Tables**
    and run the following script\
    \
    ![](./media/image146.emf)\
    \
    ![A screenshot of a computer Description automatically
    generated](./media/image147.png){width="3.8958333333333335in"
    height="0.9722222222222222in"}

19. You should see some data like the image below, but it may not be
    exact\
    \
    ![A screenshot of a
    computer](./media/image148.png){width="5.951388888888889in"
    height="0.9930555555555556in"}

[]{#_Toc170369885 .anchor}Task 3: Transform Tables in Silver Layer

1.  Now that the Bronze tables are loaded run the following KQL script
    within the "Create Tables" Queryset to create four new tables that
    will serve as the Silver Layer of the Medallion Framework.

![](./media/image149.emf)

2.  Run that script by highlighting the new script and clicking **Run**.

![A screenshot of a computer Description automatically
generated](./media/image150.png){width="4.069444444444445in"
height="2.125in"}

3.  Once that script is executed, you will see four new tables added
    into the KQL Database tables menu.

![A group of black text Description automatically
generated](./media/image151.png){width="1.3854166666666667in"
height="0.75625in"}

4.  Now that the tables have been created, you need to load data into
    them. You will create an update policy to transform the data when it
    is ingested into the silver layer. Copy and paste the following
    script and then **Run** the code.

![](./media/image152.emf)

5.  While you may see results of the query execution, the best evidence
    that your query completed is that you will see a new expandable
    folder in your Database objects pane. Click on the **\> icon** next
    to the **Functions folder**. These functions will allow the data
    loaded into the Bronze layer of the KQL Database to then be
    mirrored, transformed and loaded into the Silver layer.

![A screenshot of a
computer](./media/image153.png){width="1.9027777777777777in"
height="1.9097222222222223in"}

6.  Now let's simulate this process, you will run the pipeline you
    created earlier in this lab again. Navigate back to the **Load KQL
    Database** pipeline now.

![A screenshot of a phone Description automatically
generated](./media/image154.png){width="0.9069444444444444in"
height="1.8395833333333333in"}

7.  Simply click the **Run** button within the **Home ribbon** to
    execute the pipeline again and load the data to the Bronze layer
    where it will then be transformed by the functions you created and
    loaded into the Silver tables.

![A screenshot of a computer Description automatically
generated](./media/image155.png){width="3.908333333333333in"
height="2.941666666666667in"}

8.  Click **OK** on this flyout to run the pipeline with the same
    parameters as previously.

![A screenshot of a computer Description automatically
generated](./media/image156.png){width="3.3125in"
height="1.7715277777777778in"}

9.  Again, wait approximately one minute for the pipeline to complete
    its load and when all items in your Output menu indicate
    **Succeeded** move on to the next step.

![A screenshot of a computer Description automatically
generated](./media/image157.png){width="5.158333333333333in"
height="2.4583333333333335in"}

10. Once the data pipeline has been completed, go and validate the
    results in the KQL Database. Open back up the **Create Tables** KQL
    Queryset.

11. On a new line, query the SilverAddress table by writing out the
    following query and executing the code.

![](./media/image158.emf)

![A blue rectangle with red and black text Description automatically
generated](./media/image159.png){width="2.3805555555555555in"
height="0.9895833333333334in"}

12. Notice in your results, your **SilverAddress** table has an
    additional column, **IngestionDate**, that is not physically present
    on the **Address** table.

![A screenshot of a computer Description automatically
generated](./media/image160.png){width="3.5868055555555554in"
height="1.8881944444444445in"}

[]{#_Toc170369886 .anchor}Task 4: Create Gold Layer with Materialized
Views

Now that you have your transformed layer of data within the Silver Layer
you can start to perform analytics with trusted, validated, and enriched
data within a Power BI report, RTI Dataset, or just by simply authoring
some KQL queries. However, there may be times where you think it
necessary to aggregate your data to make it more consumable by end
users. Let's see how this is accomplished within a KQL database.

1.  If it is not already, open your **Create Tables** KQL Queryset.

2.  Paste in the queryset the following code for creating a materialized
    view.

![](./media/image161.emf)

3.  Once the code has been pasted, highlight the code and execute it by
    click on the **Run** button.

![A screenshot of a computer program Description automatically
generated](./media/image162.png){width="5.502083333333333in"
height="1.7368055555555555in"}

4.  You will see an output in your query results detailing information
    on how this materialized view was created.

![A screenshot of a computer Description automatically
generated](./media/image163.png){width="5.586805555555555in"
height="0.8854166666666666in"}

5.  You will also see another folder was created in the KQL Database
    object explorer. Expand the **Materialized View** folder and you
    will find your **GoldAddress** view within.

![A screenshot of a computer Description automatically
generated](./media/image164.png){width="1.7097222222222221in"
height="1.01875in"}

6.  In your query window, run the following code to query the new
    materialized view.

![](./media/image165.emf)

![A close-up of a computer code Description automatically
generated](./media/image166.png){width="1.0625in"
height="0.5409722222222222in"}

7.  This query will return the row with the latest **IngestionDate** for
    each unique **AddressID** in the **SilverAddress** table.

8.  Now paste and run the following queries to build more Gold layer
    materialized views for the other tables.

![](./media/image167.emf)

9.  You should now have six materialized views within your KQL Database.

![A screenshot of a computer Description automatically
generated](./media/image168.png){width="1.7722222222222221in"
height="2.0208333333333335in"}

10. You have now successfully built a Lakehouse Medallion Framework
    within a KQL Database. While this data is easily consumable, you
    will have users that have never worked with Kusto and would prefer
    to access the data from these tables through another means. In the
    next task you will be creating a Lakehouse. Then, using the Onelake
    Availability feature ,which we enabled in Lab 01, make some of the
    tables in our KQL Database accessible through the Lakehouse using
    shortcuts

[]{#_Toc170369887 .anchor}**Fabric Lakehouse and OneLake Availability**

[]{#_Toc170369888 .anchor}Task 5: Create Lakehouse

1.  Return to the **RTI_username** workspace.

2.  Click the **+ New** drop-down menu and then select **Lakehouse**
    from the list of available options.

![A screenshot of a computer Description automatically
generated](./media/image169.png){width="1.6847222222222222in"
height="2.3270833333333334in"}

3.  Give the Lakehouse the name, **lh_Fabrikam** and then click on
    **Create**. Do not enable the preview feature of Lakehouse schemas

![A screenshot of a
computer](./media/image170.png){width="2.0555555555555554in"
height="1.2986111111111112in"}

[]{#_Toc170369889 .anchor}Task 6: Shortcut to KQL Database Tables

Within the Lakehouse user interface, you have a couple options for how
you could bring streaming data into the Lakehouse itself. One option
mentioned earlier in the class is using an Eventstream to load data
directly into the Lakehouse from the Event Hub instead of the KQL
Database. Since you have already decided that KQL Databases were to be
utilized to meet specific goals and requirements, you don't want to copy
that data again. Instead let's use a **Shortcut** to bring that data
from the KQL Database that we already have so users more familiar with
this experience can have access to the data we have been using in the
KQL Database

1.  Choose the option from the menu that says **New shortcut**.

![A screenshot of a
computer](./media/image171.png){width="5.256944444444445in"
height="1.4375in"}

2.  Select the option **Microsoft OneLake** under the **Internal
    sources**.

![A screenshot of a computer Description automatically
generated](./media/image172.png){width="2.4631944444444445in"
height="1.4229166666666666in"}

3.  Within the menu, select the **eh_Fabrikam** KQL Database to bring
    tables from that storage into the Lakehouse without duplicating or
    copying the data.

![A screenshot of a
computer](./media/image173.png){width="3.0555555555555554in"
height="1.9791666666666667in"}

4.  Click **Next** at the bottom of the menu.

5.  Open the tables within the **eh_Fabrikam** by clicking on the **\>
    icon** and the select the following tables to bring over.

-   Clicks

-   Impressions

![A screenshot of a computer Description automatically
generated](./media/image174.png){width="2.3472222222222223in"
height="4.125in"}

6.  These tables could be very useful to any users who may be leveraging
    notebooks within Fabric. This data cold be used in data science to
    train a model that predicts what link users might likely be
    interested in.

7.  Click **Next**.

8.  One last validation screen will appear. Once you are satisfied with
    your selection, click on the **Create** button at the bottom of the
    screen.

![A screenshot of a
computer](./media/image175.png){width="6.25in"
height="2.8472222222222223in"}

9.  You will now see all the tables you selected from the KQL Database
    have appeared within the Lakehouse.

![A screenshot of a computer Description automatically
generated](./media/image176.png){width="2.4652777777777777in"
height="3.7291666666666665in"}

10. Click on the table called **Clicks**.

![A screenshot of a
computer](./media/image177.png){width="5.381944444444445in"
height="1.625in"}

11. You can see a sample of the records from that table have appeared
    within your user interface.

[]{#_Toc170369890 .anchor}**Summary**

In this lab, users created a Medallion Framework within a Kusto Query
Language (KQL) database. Users ingested raw data into the Bronze Layer
of the medallion architecture using a data pipeline. They transformed
this data and loaded it into the Silver Layer for further processing and
refinement. Finally, users aggregated and optimized the data for
analytics in the Gold Layer using Materialized Views.

After building the medallion framework, users employed Microsoft Fabric
shortcuts to link the data from the KQL database to a Lakehouse. This
integration allowed seamless access and analysis of data across both
environments. The lab concluded with users verifying the data linkage
and performing basic queries to ensure the framework\'s functionality.

[]{#_Toc170369891 .anchor}**References**

Fabric Real-Time Intelligence in a Day (RTIIAD) introduces you to some
of the key functions available in Microsoft Fabric. In the menu of the
service, the Help (?) section has links to some great resources.

![](./media/image63.png){width="1.9895833333333333in"
height="4.604166666666667in"}![](./media/image64.jpg){width="1.9895833333333333in"
height="4.604166666666667in"}

Here are a few more resources that will help you with your next steps
with Microsoft Fabric.

-   See blog post to read the full [Microsoft Fabric GA
    announcement](https://aka.ms/Fabric-Hero-Blog-Ignite23)

-   Explore Fabric through the [Guided
    Tour](https://aka.ms/Fabric-GuidedTour)

-   Sign up for the [Microsoft Fabric free
    trial](https://aka.ms/try-fabric)

-   Visit the [Microsoft Fabric
    website](https://aka.ms/microsoft-fabric)

-   Learn new skills by exploring the [Fabric Learning
    modules](https://aka.ms/learn-fabric)

-   Explore the [Fabric technical
    documentation](https://aka.ms/fabric-docs)

-   Read the [free e-book on getting started with
    Fabric](https://aka.ms/fabric-get-started-ebook)

-   Join the [Fabric community](https://aka.ms/fabric-community) to post
    your questions, share your feedback, and learn from others

Read the more in-depth Fabric experience announcement blogs:

-   [Data Factory experience in Fabric
    blog](https://aka.ms/Fabric-Data-Factory-Blog)

-   [Synapse Data Engineering experience in Fabric
    blog](https://aka.ms/Fabric-DE-Blog)

-   [Synapse Data Science experience in Fabric
    blog](https://aka.ms/Fabric-DS-Blog)

-   [Synapse Data Warehousing experience in Fabric
    blog](https://aka.ms/Fabric-DW-Blog)

-   [Real-](https://aka.ms/Fabric-RTA-Blog)[Time Intelligence experience
    in Fabric
    blog](https://blog.fabric.microsoft.com/en-us/blog/category/real-time-intelligence)

-   [Power BI announcement blog](https://aka.ms/Fabric-PBI-Blog)

-   [Data Activator experience in Fabric
    blog](https://aka.ms/Fabric-DA-Blog)

-   [Administration and governance in Fabric
    blog](https://aka.ms/Fabric-Admin-Gov-Blog)

-   [OneLake in Fabric blog](https://aka.ms/Fabric-OneLake-Blog)

-   [Dataverse and Microsoft Fabric integration
    blog](https://aka.ms/Dataverse-Fabric-Blog)

© 2024 Microsoft Corporation. All rights reserved.

By using this demo/lab, you agree to the following terms:

The technology/functionality described in this demo/lab is provided by
Microsoft Corporation for purposes of obtaining your feedback and to
provide you with a learning experience. You may only use the demo/lab to
evaluate such technology features and functionality and provide feedback
to Microsoft. You may not use it for any other purpose. You may not
modify, copy, distribute, transmit, display, perform, reproduce,
publish, license, create derivative works from, transfer, or sell this
demo/lab or any portion thereof.

COPYING OR REPRODUCTION OF THE DEMO/LAB (OR ANY PORTION OF IT) TO ANY
OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS
EXPRESSLY PROHIBITED.

THIS DEMO/LAB PROVIDES CERTAIN SOFTWARE TECHNOLOGY/PRODUCT FEATURES AND

FUNCTIONALITY, INCLUDING POTENTIAL NEW FEATURES AND CONCEPTS, IN A
SIMULATED

ENVIRONMENT WITHOUT COMPLEX SET-UP OR INSTALLATION FOR THE PURPOSE
DESCRIBED

ABOVE. THE TECHNOLOGY/CONCEPTS REPRESENTED IN THIS DEMO/LAB MAY NOT
REPRESENT FULL

FEATURE FUNCTIONALITY AND MAY NOT WORK THE WAY A FINAL VERSION MAY WORK.
WE ALSO

MAY NOT RELEASE A FINAL VERSION OF SUCH FEATURES OR CONCEPTS. YOUR
EXPERIENCE WITH USING SUCH FEATURES AND FUNCITONALITY IN A PHYSICAL
ENVIRONMENT MAY ALSO BE DIFFERENT.

**FEEDBACK**. If you give feedback about the technology features,
functionality and/or concepts described in this demo/lab to Microsoft,
you give to Microsoft, without charge, the right to use, share and
commercialize your feedback in any way and for any purpose. You also
give to third parties, without charge, any patent rights needed for
their products, technologies and services to use or interface with any
specific parts of a Microsoft software or service that includes the
feedback. You will not give feedback that is subject to a license that
requires Microsoft to license its software or documentation to third
parties because we include your feedback in them. These rights survive
this agreement.

MICROSOFT CORPORATION HEREBY DISCLAIMS ALL WARRANTIES AND CONDITIONS
WITH REGARD

TO THE DEMO/LAB, INCLUDING ALL WARRANTIES AND CONDITIONS OF
MERCHANTABILITY,

WHETHER EXPRESS, IMPLIED OR STATUTORY, FITNESS FOR A PARTICULAR PURPOSE,
TITLE AND NON-

INFRINGEMENT. MICROSOFT DOES NOT MAKE ANY ASSURANCES OR REPRESENTATIONS
WITH REGARD TO THE ACCURACY OF THE RESULTS, OUTPUT THAT DERIVES FROM USE
OF DEMO/ LAB, OR SUITABILITY OF THE INFORMATION CONTAINED IN THE
DEMO/LAB FOR ANY PURPOSE.

**DISCLAIMER**

This demo/lab contains only a portion of new features and enhancements
in Microsoft Power BI. Some of the features might change in future
releases of the product. In this demo/lab, you will learn about some,
but not all, new features.

![](./media/image1.png){width="7.226388888888889in"
height="2.303472222222222in"}![](./media/image2.png){width="7.226388888888889in"
height="2.303472222222222in"}![](./media/image1.png){width="7.226388888888889in"
height="2.303472222222222in"}
