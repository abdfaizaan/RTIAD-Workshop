**Microsoft Fabric**

Real-Time Intelligence in a Day

Lab 2

Version:

October 2024

> Contents

[Document Structure [3](#document-structure)](#document-structure)

[Introduction [3](#introduction)](#introduction)

[Fabric Real-Time Hub [3](#fabric-real-time-hub)](#fabric-real-time-hub)

[Task 1: Create an Event Stream Source
[3](#task-1-create-an-event-stream-source)](#task-1-create-an-event-stream-source)

[Task 2: Setup Eventstream Destination
[9](#task-2-setup-eventstream-destination)](#task-2-setup-eventstream-destination)

[Kusto Query Language (KQL)
[13](#kusto-query-language-kql)](#kusto-query-language-kql)

[Task 3: Authoring Kusto Database Queries
[13](#task-3-authoring-kusto-database-queries)](#task-3-authoring-kusto-database-queries)

[Task 4: Using T-SQL Queries Against a KQL Database
[18](#task-4-using-t-sql-queries-against-a-kql-database)](#task-4-using-t-sql-queries-against-a-kql-database)

[KQL Queryset [21](#kql-queryset)](#kql-queryset)

[Task 5: Create a KQL Queryset
[21](#task-5-working-with-a-kql-queryset)](#task-5-working-with-a-kql-queryset)

[Summary [22](#summary)](#summary)

[References [23](#references)](#references)

# Document Structure 

> The lab includes steps for the user to follow along with associated
> screenshots that provide visual aid. In each screenshot, sections are
> highlighted with orange boxes to indicate the area(s) user should
> focus on.

# Introduction 

> In this lab, you will experience a way to handle a continuous stream
> of real-time data. You will use a Fabric Real-Time Intelligence object
> called an Eventstream to ingest this data to the Eventhouse you
> created in the last lab and write some basic KQL queries.
>
> By the end of this lab, you will have learned:

-   How to create an Eventstream

-   Load Real-time data into a KQL Database

-   Write basic Kusto Query Language Queries

# Fabric Real-Time Hub

## Task 1: Create an Event Stream Source 

1.  Open the **Fabric workspace** you created in the last lab. From here
    we can see the Eventhouse we created.

![A screenshot of a
computer](.\media\Lab 2 1/media/image5.png){width="2.4719160104986875in"
height="1.937293307086614in"}

2.  Navigate to the "Real-Time hub" where currently we do not see any
    streams of data. That will change shortly.

![A screenshot of a computer
menu](.\media\Lab 2 1/media/image6.png){width="1.8299245406824147in"
height="2.5002274715660544in"}

3.  Select the **+ Add Source** green button which should be in the
    upper right corner.

![A green and white sign Description automatically
generated](.\media\Lab 2 1/media/image7.png){width="1.614808617672791in"
height="0.718850612423447in"}

4.  A window will open that will allow you to select a source for our
    stream data. As we discussed before, there are many fantastic
    options to choose from but for this class we will select the option
    "Azure Event Hubs".\
    \
    ![](.\media\Lab 2 1/media/image8.png){width="6.506944444444445in"
    height="2.754861111111111in"}

5.  You are now required to create a connection to the Azure Event Hub.
    Click on the **New connection** text since you do not currently have
    a connection.\
    \
    ![A screenshot of a
    computer](.\media\Lab 2 1/media/image9.png){width="3.4948501749781276in"
    height="2.2687160979877516in"}

6.  From your environment details page, copy and paste all the necessary
    connection settings into the appropriate fields. For these labs we
    are connecting to an Event Hub which has streaming data being sent
    from a python notebook. This notebook is creating fake sales
    transactions at rate of around 3,100 transactions per hour.\
    \
    Event Hub namespace: **rtiadhub{userid} -- provided by cloudlabs**\
    \
    Event Hub: **rti-iad-fabrikam**\
    \
    Shared Access Key Name: **rti-reader\
    \
    **Shared Access Key: **Available in Environment Details tab**

7.  Once all properties have been filled out click on **Connect**.\
    \
    ![A screenshot of a computer Description automatically
    generated](.\media\Lab 2 1/media/image10.png){width="4.9191579177602796in"
    height="4.007179571303587in"}

8.  In the configuration of the Azure Event Hub data source, you may
    need to modify the **Consumer group** of the Event Hub to ensure
    that you gain access to a unique access point to the stream of data.
    For this workshop you can leave the "\$Default" value as shown
    below\
    \
    ![A screenshot of a
    computer](.\media\Lab 2 1/media/image11.png){width="5.799681758530184in"
    height="2.5420811461067365in"}

9.  Before we finalize this data source and Eventstream, let's go ahead
    and rename our Eventstream to something more useful. In the "Stream
    details\" section on the right select the pencil icon next to the
    "Eventstream name" and let's call our Eventstream
    "**es_Fabrikam_InternetSales".\
    **![A screenshot of a
    computer](.\media\Lab 2 1/media/image12.png){width="2.1525546806649167in"
    height="2.2478707349081364in"}

10. Now we can click on **Next**, which will take us to a final overview
    page.\
    \
    ![A screenshot of a
    computer](.\media\Lab 2 1/media/image13.png){width="1.436994750656168in"
    height="2.647649825021872in"}

11. In this overview screen, verify the contents look correct and click
    **Create source**.\
    \
    **Note: Your details will differ from what you see in the
    screenshot\
    **\
    ![A screenshot of a computer Description automatically
    generated](.\media\Lab 2 1/media/image14.png){width="3.848911854768154in"
    height="2.2534831583552055in"}

12. Once the Eventstream and Eventstream source are created select the
    option "**Open Eventstream**"\
    \
    ![A screenshot of a
    computer](.\media\Lab 2 1/media/image15.png){width="3.055896762904637in"
    height="2.7150896762904635in"}

13. This will take you to the Eventstream user interface. Here is where
    you will see your source stream of data flowing into our eventstream
    and we have the ability to add transform events as well.

14. It may take a few moments for your Source to be **Active** but after
    waiting a few moments, click on the middle icon with the name of
    your Eventstream on it and then click on **Refresh** if you do not
    see a preview of the data.\
    \
    **Note: If you receive a "Warning" status around and audit policy,
    that is fine. The stream will still function\
    **

![](.\media\Lab 2 1/media/image16.png){width="6.2590715223097115in"
height="1.971240157480315in"}

15. You should now see a sample of the data within the bottom window.\
    ![A screenshot of a
    computer](.\media\Lab 2 1/media/image17.png){width="4.631952099737533in"
    height="3.4554527559055117in"}

16. This will show you a preview of the data that is being received from
    the Azure Event Hub. If you slide your bottom horizontal scroll bar
    all the way to the right-side of your preview, you will be able to
    see the time that the data has been received in the Event Hub in two
    columns called, **EventProcessedUtcTime** and
    **EventEnqueuedUtcTime**. This should reflect the current date/time
    in UTC format.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image18.png){width="5.133778433945757in"
height="0.7667333770778653in"}

## Task 2: Setup Eventstream Destination

1.  Click on the tile within the canvas area labeled "Switch to edit
    mode to Transform event of add destination\
    \
    ![A screenshot of a
    computer](.\media\Lab 2 1/media/image19.png){width="4.834008092738408in"
    height="2.5628576115485564in"}

2.  Within the Eventstream user interface, click on the **Transform
    events or add destination** option to open the drop-down menu.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image20.png){width="2.2601399825021873in"
height="1.7443416447944007in"}

3.  View the list of available operations that can be made to the
    stream.

![A screenshot of a phone Description automatically
generated](.\media\Lab 2 1/media/image21.png){width="1.3973228346456692in"
height="2.0017814960629923in"}

4.  Look below the operations and you will find the **Destinations**
    select the option that says **Eventhouse**.

> ![A screenshot of a computer Description automatically
> generated](.\media\Lab 2 1/media/image22.png){width="1.9273523622047244in"
> height="1.6877351268591425in"}

5.  A new menu will open on the right-hand side of the screen. The first
    thing you need to modify for the destination is the **data ingestion
    mode**. The two options are **Direct Ingestion** and **Event
    processing before ingestion.** Because we are not going to transform
    anything in our Eventstream and directly load this information in a
    KQL database table ensure that you have selected the **Direct
    ingestion** option.

![A screenshot of a
computer](.\media\Lab 2 1/media/image23.png){width="2.8298053368328957in"
height="1.541155949256343in"}

6.  Modify the remainder of the settings with the following details
    below.

-   Destination name -- **eh-kql-db-fabrikam**

-   Workspace -- **RTI_username**

-   Eventhouse -- **eh_Fabrikam**

-   KQL Database -- **eh_Fabrikam**

![A screenshot of a
computer](.\media\Lab 2 1/media/image24.png){width="2.411363735783027in"
height="4.799242125984252in"}

7.  Click on Save.

8.  With the Eventstream configured, click on the **Publish** button to
    save this Eventstream and begin your ingestion.

![A screenshot of a
chat](.\media\Lab 2 1/media/image25.png){width="5.878044619422572in"
height="1.9898786089238845in"}

9.  Choose the **Configure** option within the **Destination** to
    correctly map the stream to a table in the KQL Database.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image26.png){width="6.506944444444445in"
height="1.8798611111111112in"}

10. Click on the **+ New table** option underneath the the
    **eh_Fabrikam** database.

![A screenshot of a
computer](.\media\Lab 2 1/media/image27.png){width="5.957354549431321in"
height="3.353157261592301in"}

11. Give the new table the name, **InternetSales** and then click on the
    checkmark.

![A screenshot of a
computer](.\media\Lab 2 1/media/image28.png){width="3.3650524934383204in"
height="1.0001399825021873in"}

12. You may need to update your **"Data connection name"** to meet
    requirements. Let us rename it to
    **"eh_Fabrikam_es_InternetSales".** Then we can click on **Next.\
    \
    **![A screenshot of a
    computer](.\media\Lab 2 1/media/image29.png){width="4.927771216097987in"
    height="3.604669728783902in"}**\
    **

13. After a few moments of searching for events, the user interface
    should allow you to see that sample data was found. Click on
    **Finish** at the bottom of the screen.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image30.png){width="5.978159448818897in"
height="3.678768591426072in"}

14. After this you will be shown a summary. Once you have all green
    checkmarks, click **close** to move forward.

15. Once you see the user interface showing the mappings from the source
    to the Eventstream to the destination, you have correctly configured
    and started a stream of data into your KQL Database.

![A screen shot of a
computer](.\media\Lab 2 1/media/image31.png){width="5.947115048118985in"
height="1.6971806649168855in"}

# Kusto Query Language (KQL)

## Task 3: Authoring Kusto Database Queries

1.  Make your way back to your **RTI_username** workspace. You should
    see the new Eventstream you just created along side all the
    Evenhouse items.

![A screenshot of a
computer](.\media\Lab 2 1/media/image32.png){width="3.946890857392826in"
height="2.202706692913386in"}

2.  Open the **eh_Fabrikam** KQL Database item.

![A screenshot of a
computer](.\media\Lab 2 1/media/image33.png){width="4.061921478565179in"
height="1.8020516185476816in"}

3.  Within this experience, you can get an overview of the current
    structure, size, and use of the KQL Database. Because the
    Eventstream is sending data to this KQL Database consistently you
    will notice the amount of storage will increase over time.

![A screenshot of a
computer](.\media\Lab 2 1/media/image34.png){width="6.171492782152231in"
height="2.572004593175853in"}

4.  Click on the **refresh icon** in the top-right corner of the screen.

![A screenshot of a
phone](.\media\Lab 2 1/media/image35.png){width="5.891737751531059in"
height="1.939808617672791in"}

5.  The size of the database should have grown. The value you see may
    not be exact in comparison to the screenshots in the remainder of
    the lab. Depending on how long you take to complete the content you
    will have received less or more records than other members of the
    class. This is completely fine and will not affect your ability to
    follow along whatsoever.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image36.png){width="3.0316732283464565in"
height="1.4793733595800524in"}

6.  Within the database navigation area on the left-hand side of the
    screen, click on the table within your KQL Database called
    **InternetSales** and you will see an overview of the table

![A screenshot of a
computer](.\media\Lab 2 1/media/image37.png){width="2.0744149168853894in"
height="1.8964129483814522in"}

7.  This overview will give you metadata details about the table you
    have created and any actively streaming data with your Eventstream.
    Again, the size of the table and the number of rows within the table
    are going to vary from student to student and will not affect your
    end results of this or any lab. A few additional items to call out
    on this menu include:

-   **Histogram** -- Shows number of rows ingested, time it was last
    generated and the interval of display

-   **Data Preview** -- Shows a preview of the table ingestion results.

-   **Schema** **Insights**-- This includes details about the column
    name and the data types of the column that can be queried with KQL.
    Also shows the Top 10 count for the values in the selected column

-   **Table Details** -- Shows Compressed and Original size of table,
    OneLake availability, number of rows in the tables and various other
    details

![A screenshot of a
computer](.\media\Lab 2 1/media/image38.png){width="6.506944444444445in"
height="2.2055555555555557in"}

8.  Click on **Explore your data** in the top-right corner.

![A white background with black text Description automatically
generated](.\media\Lab 2 1/media/image39.png){width="6.506944444444445in"
height="0.8777777777777778in"}

9.  This will open the default KQL Queryset that was created alongside
    the Eventhouse. There are a few pre-scripted queries that are
    already authored but need some slight customization. There are also
    two links to Microsoft documentation that can be helpful when
    learning KQL or also looking at SQL to KQL conversions which will be
    discussed later throughout this class.

![A screenshot of a
computer](.\media\Lab 2 1/media/image40.png){width="6.506944444444445in"
height="2.3965277777777776in"}

10. Click on **Line 8** and where the query says, **YOUR_TABLE_HERE**,
    replace that with the table name, **InternetSales**.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image41.png){width="6.506944444444445in"
height="0.6361111111111111in"}

11. Highlight **Line 8 and 9** and click on the **Run** button in the
    top-left corner of the window.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image42.png){width="2.1878051181102363in"
height="1.8335892388451445in"}

12. The query uses the **take** operator to bring back a specified
    number of rows. When the query runs it will pull data from the
    InternetSales table and bring back whatever number of rows you have
    plugged into the query. For this example, 100 rows will return. The
    specific rows returned cannot be determined with this operator and
    the results of your query will vary from the result of others.

![](.\media\Lab 2 1/media/image43.png){width="5.39198053368329in"
height="2.6367180664916887in"}

13. Click on **Line 12** and where the query says, **YOUR_TABLE_HERE**,
    replace that with the table name, **InternetSales**.

![A screen shot of a computer Description automatically
generated](.\media\Lab 2 1/media/image44.png){width="3.8963768591426073in"
height="0.6875962379702537in"}

14. Highlight **Line 12 and 13** and click on the **Run** button in the
    top-left corner of the window.\
    \
    ![A screenshot of a
    computer](.\media\Lab 2 1/media/image45.png){width="2.534669728783902in"
    height="1.819763779527559in"}

15. This query uses the count operator. This query will return an
    aggregated number of records that exist at the time of the query
    execution on the KQL Database table. Feel free to run this query a
    few more times and you should notice that the number of records
    increases after every few seconds.

> ![A screenshot of a computer Description automatically
> generated](.\media\Lab 2 1/media/image46.png){width="2.173869203849519in"
> height="1.387836832895888in"}

16. Repeat the previous steps for the final query that is automatically
    created for you on **Line 16/17** and run the query again.

![A screenshot of a
computer](.\media\Lab 2 1/media/image47.png){width="6.15280949256343in"
height="2.148558617672791in"}

17. This query will give you the number of records that have been
    ingested into your table within an hour window. The overall
    distribution of these records for the data you are currently
    ingesting will be approximately 4,100 per hour. There will be slight
    variations within that numbers of transactions per hour though and
    this query will detail if less or more records were ingested in each
    window.

## Task 4: Using T-SQL Queries Against a KQL Database

You may be working with the Kusto Query Language for the first time.
While this language is intuitive and easy to learn for simple queries,
you may want to return the results of a more complex queries than you
are currently capable of. Several helpful tools have been included
within the KQL Queryset capabilities including converting SQL queries to
KQL queries and simply authoring T-SQL queries within the KQL Queryset.
Let's explore!

1.  You need to create a query that returns the number of each product
    that has been sold. This is something you can quickly do with T-SQL.
    Within the query window, you can translate your SQL queries into KQL
    to better understand how to author KQL queries in the future. Start
    with writing the following command.\
    **(Note: Double click the object below in order to be able to copy
    the text)\
    **\
    ![](.\media\Lab 2 1/media/image48.emf)

![](.\media\Lab 2 1/media/image49.png){width="1.4205325896762904in"
height="0.5494510061242345in"}

2.  The comment line "\--" followed by the keyword "explain" will allow
    you to now create a SQL query and return a result with the KQL query
    that could be used to achieve a similar query and result. Below
    input the following query to explain what the KQL query would look
    like:\
    \
    ![](.\media\Lab 2 1/media/image50.emf)

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image51.png){width="5.583232720909886in"
height="1.6267202537182852in"}

3.  This is a simple SQL query that will retrieve results from the
    InternetSales table to return two columns, the product key and a
    count of the number of orders. Because there is an aggregated column
    and a non-aggregated column, you must use a GROUP BY to return
    results for each individual product. Run the entire query beginning
    with the "\--" to the end of the T-SQL query.

> ![A screenshot of a computer Description automatically
> generated](.\media\Lab 2 1/media/image52.png){width="4.750662729658792in"
> height="2.333659230096238in"}

4.  The output of the explain query should be a single record with the
    translated KQL query as the result. Click on the **caret icon (\>)**
    to expand the results and allow for easier translation.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image53.png){width="6.506944444444445in"
height="0.9243055555555556in"}

5.  Click on the query pane highlighted below in orange. This will allow
    you to select translated KQL query and copy it. Paste this query in
    the KQL Queryset we have been using

![A screenshot of a
computer](.\media\Lab 2 1/media/image54.png){width="6.506944444444445in"
height="1.44375in"}

6.  With the results in your query pane, highlight and run the query to
    retrieve the results. The **summarize** operator will produce a
    table that aggregates the content of the input table while
    determining how to group each record with the **by Product Key** and
    the **project** operator will select the columns to include, rename,
    or drop while inserting new compute columns.

![A screenshot of a
computer](.\media\Lab 2 1/media/image55.png){width="6.506944444444445in"
height="2.6006944444444446in"}

7.  Feel free to explore a complete list of SQL to KQL cheat sheet
    operations at the top of your queryset for additional capabilities
    and conversions.

![A close-up of a message Description automatically
generated](.\media\Lab 2 1/media/image56.png){width="4.858754374453193in"
height="0.7834011373578302in"}

8.  Instead of using KQL, another alternative to querying the results of
    the KQL Database within Fabric is to write and run a T-SQL query.
    Highlight the original SQL statement that was used to translate the
    KQL query and run only that.

![A screenshot of a computer
code](.\media\Lab 2 1/media/image57.png){width="3.8330030621172355in"
height="1.8617432195975503in"}

9.  This will also yield perfectly valid results without having to
    convert to KQL beforehand.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image58.png){width="4.427701224846894in"
height="2.4586767279090114in"}

# KQL Queryset

## Task 5: Working with a KQL Queryset

1.  While most of the queries within this window were automatically
    created from the user interface, there may be times in the future
    where you wish to create your own KQL queries from scratch. This can
    be managed through the tabs feature located at the top. It also
    should be noted that this Queryset automatically saves periodically.

2.  Notice at the top of the Queryset the default name of our first page
    is the same name as our database.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image59.png){width="4.490209973753281in"
height="3.594251968503937in"}

3.  Let's go ahead and re-name this tab by clicking on the pencil icon,
    let's call it "**My** **First KQL Query"**.

![A screenshot of a computer Description automatically
generated](.\media\Lab 2 1/media/image60.png){width="2.6774573490813647in"
height="1.9794433508311462in"}

4.  In the future if we would like to isolate our code, we can simply
    create additional tabs by clicking the "+" icon.\
    \
    ![A screenshot of a computer Description automatically
    generated](.\media\Lab 2 1/media/image61.png){width="2.6774573490813647in"
    height="1.9794433508311462in"}

5.  Return to your **RTI_username** workspace. You should have the
    following objects present

![A screenshot of a
computer](.\media\Lab 2 1/media/image62.png){width="4.516534339457568in"
height="3.1729057305336834in"}

# Summary

In this lab, you began by setting up a connection to an Event Hub that
has a running stream of data and used an Eventstream to take that data
and ingest it into a KQL Database. Once the data was ingested, you were
able to author several KQL queries and look at the functionality of
using T-SQL to help learn KQL syntax or simply return results with SQL
statements.

# References 

> Fabric Real-time Intelligence in a Day (RTIIAD) introduces you to some
> of the key functions available in Microsoft Fabric.
>
> In the menu of the service, the Help (?) section has links to some
> great resources.
>
> Here are a few more resources that will help you with your next steps
> with Microsoft Fabric.

-   See blog post to read the full [[Microsoft Fabric GA]{.underline}
    [announcement]{.underline}](https://aka.ms/Fabric-Hero-Blog-Ignite23)

-   Explore Fabric through the [[Guided
    Tour]{.underline}](https://aka.ms/Fabric-GuidedTour)

-   Sign up for the [[Microsoft Fabric free
    trial]{.underline}](https://aka.ms/try-fabric)

-   Visit the [[Microsoft Fabric
    website]{.underline}](https://aka.ms/microsoft-fabric)

-   Learn new skills by exploring the [[Fabric Learning
    modules]{.underline}](https://aka.ms/learn-fabric)

-   Explore the [[Fabric technical
    documentation]{.underline}](https://aka.ms/fabric-docs)

-   Read the [[free e-book on getting started with
    Fabric]{.underline}](https://aka.ms/fabric-get-started-ebook)

-   Join the [[Fabric
    community]{.underline}](https://aka.ms/fabric-community) to post
    your questions, share your feedback, and learn from others

> Read the more in-depth Fabric experience announcement blogs:

-   [[Data Factory experience in Fabric
    blog]{.underline}](https://aka.ms/Fabric-Data-Factory-Blog)

-   [[Synapse Data Engineering experience in Fabric
    blog]{.underline}](https://aka.ms/Fabric-DE-Blog)

-   [[Synapse Data Science experience in Fabric
    blog]{.underline}](https://aka.ms/Fabric-DS-Blog)

-   [[Synapse Data Warehousing experience in Fabric
    blog]{.underline}](https://aka.ms/Fabric-DW-Blog)

-   [[Real-](https://aka.ms/Fabric-RTA-Blog)[Time Intelligence
    experience in Fabric
    blog](https://blog.fabric.microsoft.com/en-us/blog/category/real-time-intelligence)]{.underline}

-   [[Power BI announcement
    blog]{.underline}](https://aka.ms/Fabric-PBI-Blog)

-   [[Data Activator experience in Fabric
    blog]{.underline}](https://aka.ms/Fabric-DA-Blog)

-   [[Administration and governance in Fabric
    blog]{.underline}](https://aka.ms/Fabric-Admin-Gov-Blog)

-   [[OneLake]{.underline} [in Fabric
    blog]{.underline}](https://aka.ms/Fabric-OneLake-Blog)

-   [[Dataverse and Microsoft Fabric integration
    blog]{.underline}](https://aka.ms/Dataverse-Fabric-Blog)

> © 2024 Microsoft Corporation. All rights reserved.
>
> By using this demo/lab, you agree to the following terms:
>
> The technology/functionality described in this demo/lab is provided by
> Microsoft Corporation for purposes of obtaining your feedback and to
> provide you with a learning experience. You may only use the demo/lab
> to evaluate such technology features and functionality and provide
> feedback to Microsoft. You may not use it for any other purpose. You
> may not modify, copy, distribute, transmit, display, perform,
> reproduce, publish, license, create derivative works from, transfer,
> or sell this demo/lab or any portion thereof.
>
> COPYING OR REPRODUCTION OF THE DEMO/LAB (OR ANY PORTION OF IT) TO ANY
> OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS
> EXPRESSLY PROHIBITED.
>
> THIS DEMO/LAB PROVIDES CERTAIN SOFTWARE TECHNOLOGY/PRODUCT FEATURES
> AND
>
> FUNCTIONALITY, INCLUDING POTENTIAL NEW FEATURES AND CONCEPTS, IN A
> SIMULATED
>
> ENVIRONMENT WITHOUT COMPLEX SET-UP OR INSTALLATION FOR THE PURPOSE
> DESCRIBED
>
> ABOVE. THE TECHNOLOGY/CONCEPTS REPRESENTED IN THIS DEMO/LAB MAY NOT
> REPRESENT FULL
>
> FEATURE FUNCTIONALITY AND MAY NOT WORK THE WAY A FINAL VERSION MAY
> WORK. WE ALSO
>
> MAY NOT RELEASE A FINAL VERSION OF SUCH FEATURES OR CONCEPTS. YOUR
> EXPERIENCE WITH USING SUCH FEATURES AND FUNCITONALITY IN A PHYSICAL
> ENVIRONMENT MAY ALSO BE DIFFERENT.
>
> **FEEDBACK**. If you give feedback about the technology features,
> functionality and/or concepts described in this demo/lab to Microsoft,
> you give to Microsoft, without charge, the right to use, share and
> commercialize your feedback in any way and for any purpose. You also
> give to third parties, without charge, any patent rights needed for
> their products, technologies and services to use or interface with any
> specific parts of a Microsoft software or service that includes the
> feedback. You will not give feedback that is subject to a license that
> requires Microsoft to license its software or documentation to third
> parties because we include your feedback in them. These rights survive
> this agreement.
>
> MICROSOFT CORPORATION HEREBY DISCLAIMS ALL WARRANTIES AND CONDITIONS
> WITH REGARD
>
> TO THE DEMO/LAB, INCLUDING ALL WARRANTIES AND CONDITIONS OF
> MERCHANTABILITY,
>
> WHETHER EXPRESS, IMPLIED OR STATUTORY, FITNESS FOR A PARTICULAR
> PURPOSE, TITLE AND NON-
>
> INFRINGEMENT. MICROSOFT DOES NOT MAKE ANY ASSURANCES OR
> REPRESENTATIONS WITH REGARD TO THE ACCURACY OF THE RESULTS, OUTPUT
> THAT DERIVES FROM USE OF DEMO/ LAB, OR SUITABILITY OF THE INFORMATION
> CONTAINED IN THE DEMO/LAB FOR ANY PURPOSE.
>
> **DISCLAIMER**
>
> This demo/lab contains only a portion of new features and enhancements
> in Microsoft Power BI. Some of the features might change in future
> releases of the product. In this demo/lab, you will learn about some,
> but not all, new features.
