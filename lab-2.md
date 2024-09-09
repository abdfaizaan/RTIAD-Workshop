# Lab 2

The lab includes steps for the user to follow along with associated screenshots that provide visual aid. In each screenshot, sections are highlighted with orange boxes to indicate the area(s) user should focus on.

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

#  Fabric Real-Time Hub

## Task 1: Create an Event Stream Source 

1.  Open the **Fabric workspace** you created in the last lab. From here
    we can see the Eventhouse we created.

    ![A screenshot of a
computer](./media/image5.png)

2.  Navigate to the "Real-Time hub" where currently we do not see any
    streams of data. That will change shortly.

![A screenshot of a
computer](./media/image6.png)

3.  Select the "Get events" green button which should be in the upper
    right corner.

![A screenshot of a search box Description automatically
generated](./media/image7.png){width="2.917073490813648in"
height="2.0523698600174978in"}

4.  A window will open that will allow you to select a source for our
    stream data. As we discussed before, there are many fantastic
    options to choose from but for this class we will select the option
    "Azure Event Hubs".\
    \
    ![A screenshot of a computer Description automatically
    generated](./media/image8.png){width="6.506944444444445in"
    height="2.954861111111111in"}

5.  You are now required to create a connection to the Azure Event Hub.
    Click on the **New connection** text since you do not currently have
    a connection.\
    \
    ![A screenshot of a
    computer](./media/image9.png){width="3.4948501749781276in"
    height="2.2687160979877516in"}

6.  From your environment details page, copy and paste all the necessary
    connection settings into the appropriate fields. For these labs we
    are connecting to an Event Hub which has streaming data being sent
    from a python notebook. This notebook is creating fake sales
    transactions at rate of around 3,100 transactions per hour.\
    \
    Event Hub namespace: **realtimeconsumersiad**\
    \
    Event Hub: **rti-iad**\
    \
    Shared Access Key Name: **rti-reader\
    \
    **Shared Access Key:
    **H/5gTWuI+lQLT9HYBzuqzPdKaR6YWXCRw+AEhE6k1gE=**

7.  Once all properties have been filled out click on **Connect**.\
    \
    ![A screenshot of a computer Description automatically
    generated](./media/image10.png){width="5.563276465441819in"
    height="4.531882108486439in"}

8.  In the configuration of the Azure Event Hub data source, you will
    need to modify the **Consumer group** of the Event Hub to ensure
    that you gain access to a unique access point to the stream of data.
    Within your **Environment details** find the property that lists
    what your consumer group name will be and place that into the field
    box. It will appear something like "**cg-xx**".\
    \
    ![A screenshot of a
    computer](./media/image11.png){width="5.594336176727909in"
    height="3.9375284339457566in"}

9.  Before we finalize this data source and Eventstream, let's go ahead
    and rename our Eventstream to something more useful. In the "Stream
    details\" section on the right select the pencil icon next to the
    "Eventstream name" and let's call our Eventstream
    "**es_Fabrikam_InternetSales".\
    **![A screenshot of a
    computer](./media/image12.png){width="2.3354965004374453in"
    height="2.1383048993875766in"}

10. Now we can click on **Next**, which will take us to a final overview
    page.\
    \
    ![A screenshot of a
    computer](./media/image13.png){width="6.204362423447069in"
    height="3.6861986001749782in"}

11. In this overview screen, Verify the contents look correct and click
    **Create source**.\
    \
    ![A screenshot of a computer Description automatically
    generated](./media/image14.png){width="6.506944444444445in"
    height="3.8097222222222222in"}

12. Once the Eventstream and Eventstream source are created select the
    option "**Open Eventstream**"\
    \
    ![A screenshot of a
    computer](./media/image15.png){width="3.055896762904637in"
    height="2.7150896762904635in"}

13. This will take you to the Eventstream user interface. Here is where
    you will see able to connect with a source stream of data, bring it
    into this Fabric item, and then stream it to a new destination like
    a Lakehouse or KQL Database.

14. It may take a few moments for your Source to be **Active** but after
    waiting a few moments, click on the middle icon with the name of
    your Eventstream on it and then click on **Refresh** if you do not
    see a preview of the data.\
    \
    **Note: If you receive a "Warning" status around and audit policy,
    that is fine. The stream will still function\
    **

![A screenshot of a computer Description automatically
generated](./media/image16.png){width="6.2590715223097115in"
height="1.971240157480315in"}

15. You should now see a sample of the data within the bottom window.\
    ![A screenshot of a
    computer](./media/image17.png){width="4.631952099737533in"
    height="3.4554527559055117in"}

16. This will show you a preview of the data that is being received from
    the Azure Event Hub. If you slide your bottom horizontal scroll bar
    all the way to the right-side of your preview, you will be able to
    see the time that the data has been received in the Event Hub in two
    columns called, **EventProcessedUtcTime** and
    **EventEnqueuedUtcTime**. This should reflect the current date/time
    in UTC format.

![A screenshot of a computer Description automatically
generated](./media/image18.png){width="5.133778433945757in"
height="0.7667333770778653in"}

## Task 2: Setup Eventstream Destination

1.  Click on the tile within the canvas area labeled "Switch to edit
    mode to Transform event of add destination\
    \
    ![A screenshot of a
    computer](./media/image19.png){width="4.834008092738408in"
    height="2.5628576115485564in"}

2.  Within the Eventstream user interface, click on the **Transform
    events or add destination** option to open the drop-down menu.

![A screenshot of a computer Description automatically
generated](./media/image20.png){width="2.486573709536308in"
height="1.9190988626421697in"}

3.  View the list of available operations that can be made to the
    stream.

![A screenshot of a phone Description automatically
generated](./media/image21.png){width="1.3973228346456692in"
height="2.0017814960629923in"}

4.  Look below the operations and you will find the **Destinations**
    select the option that says **KQL Database**.

![A screenshot of a computer Description automatically
generated](./media/image22.png){width="1.671599956255468in"
height="1.6412073490813648in"}

5.  A new menu will open on the right-hand side of the screen. The first
    thing you need to modify for the destination is the **data ingestion
    mode**. The two options are **Direct Ingestion** and **Event
    processing before ingestion.** Because we are not going to transform
    anything in our Eventstream and directly load this information in a
    KQL database table ensure that you have selected the **Direct
    ingestion** option.

![A white background with black text Description automatically
generated](./media/image23.png){width="2.666897419072616in"
height="1.108429571303587in"}

6.  Modify the remainder of the settings with the following details
    below.

-   Destination name -- **eh-kql-db-Fabrikam**

-   Workspace -- **RTI_username**

-   KQL Database -- **eh_Fabrikam**

![A screenshot of a
computer](./media/image24.png){width="2.327101924759405in"
height="3.5932141294838145in"}

7.  Click on Save.

8.  With the Eventstream configured, click on the **Publish** button to
    save this Eventstream and begin your ingestion.

![A screenshot of a
computer](./media/image25.png){width="6.506944444444445in"
height="2.154861111111111in"}

9.  Choose the **Configure** option within the **Destination** to
    correctly map the stream to a table in the KQL Database.

![A screenshot of a chat Description automatically
generated](./media/image26.png){width="6.506944444444445in"
height="1.4020833333333333in"}

10. Click on the **+ New table** option underneath the the
    **eh_Fabrikam** database.

![A screenshot of a
computer](./media/image27.png){width="5.957354549431321in"
height="3.353157261592301in"}

11. Give the new table the name, **InterentSales** and then click on the
    checkmark.

![A screenshot of a
computer](./media/image28.png){width="3.3650524934383204in"
height="1.0001399825021873in"}

12. You may need to update your **"Data connection name"** to meet
    requirements. Let us rename it to
    **"eh_Fabrikam_es_InternetSales".** Then we can click on **Next.\
    \
    **![A screenshot of a
    computer](./media/image29.png){width="4.927771216097987in"
    height="3.604669728783902in"}**\
    **

13. After a few moments of searching for events, the user interface
    should allow you to see that sample data was found. Click on
    **Finish** at the bottom of the screen.

![A screenshot of a computer Description automatically
generated](./media/image30.png){width="5.978159448818897in"
height="3.678768591426072in"}

14. After this you will be shown a summary. Once you have all green
    checkmarks, click **close** to move forward.

15. Once you see the user interface showing the mappings from the source
    to the Eventstream to the destination, you have correctly configured
    and started a stream of data into your KQL Database.

![A screenshot of a
chat](./media/image31.png){width="6.379064960629921in"
height="1.0130260279965004in"}

# Kusto Query Language (KQL)

## Task 3: Authoring Kusto Database Queries

1.  Make your way back to your **RTI_username** workspace. You should
    see two new objects that have been created because of your
    Eventstream. The Eventstream itself as well as a Real-Time
    Intelligence Data stream.

![A screenshot of a
computer](./media/image32.png){width="5.573383639545057in"
height="2.2159241032370955in"}

2.  Open the **eh_Fabrikam** KQL Database item.

![A screenshot of a
computer](./media/image33.png){width="4.057723097112861in"
height="1.2373326771653543in"}

3.  Within this experience, you can get an overview of the current
    structure, size, and use of the KQL Database. Because the
    Eventstream is sending data to this KQL Database consistently you
    will notice the amount of storage will increase over time.

![A screenshot of a computer Description automatically
generated](./media/image34.png){width="6.34346019247594in"
height="2.3749048556430448in"}

4.  Click on the **refresh icon** in the top-right corner of the screen.

![A screenshot of a
phone](./media/image35.png){width="5.891737751531059in"
height="1.939808617672791in"}

5.  The size of the database should have grown. Your numbers here will
    not be exact in their reflection with screenshots in the remainder
    of the lab as depending on how long you take to complete the content
    you will have received less or more records than other members of
    the class. This is completely fine and will not affect your ability
    to follow along whatsoever.

![A black text on a white
background](./media/image36.png){width="4.233502843394576in"
height="1.3045089676290464in"}

6.  Within your System details on the left-hand side of the screen,
    click on the table within your KQL Database called
    **InternetSales**.

![A screenshot of a
computer](./media/image37.png){width="2.4261800087489065in"
height="2.2179932195975502in"}

7.  This menu will give you metadata details about the table you have
    created and any actively streaming data with your Eventstream.
    Again, the size of the table and the number of rows within the table
    are going to vary from student to student and will not affect your
    end results of this or any lab. A few additional items to call out
    on this menu include:

-   **Schema** -- This includes details about the column name and the
    data types of the column that can be queried with KQL.

-   **Mappings** -- This will list all the sources of data and in what
    format the data is being received. You can have various sources in
    various formats all mapping data to the same table on a KQL
    Database.

-   **OneLake availability** -- This is currently active because of the
    property we enabled at the higher level in the Eventhouse.

![A screenshot of a
computer](./media/image38.png){width="5.439140419947506in"
height="4.204448818897638in"}

8.  Click on **Explore your data** in the top-right corner.

![A screenshot of a
computer](./media/image39.png){width="6.213735783027122in"
height="1.9901192038495188in"}

9.  This will open an interface in which you can author KQL queries
    against your database tables. There are a few pre-scripted queries
    that are already authored but need some slight customization. There
    are also two links to Microsoft documentation that can be helpful
    when learning KQL or also looking at SQL to KQL conversions which
    will be discussed later throughout this class.

![A screenshot of a computer Description automatically
generated](./media/image40.png){width="5.557589676290464in"
height="2.634071522309711in"}

10. Click on **Line 8** and where the query says, **YOUR_TABLE_HERE**,
    replace that with the table name, **InternetSales**.

![A screenshot of a computer Description automatically
generated](./media/image41.png){width="6.506944444444445in"
height="0.6361111111111111in"}

11. Highlight **Line 8 and 9** and click on the **Run** button in the
    top-left corner of the window.

![A screenshot of a
computer](./media/image42.png){width="3.037364391951006in"
height="2.1695450568678916in"}

12. The query uses the **take** operator to bring back a specified
    number of rows. When the query runs it will pull data from the
    InternetSales table and bring back whatever number of rows you have
    plugged into the query. For this example, 100 rows will return. The
    specific rows returned cannot be determined with this operator and
    the results of your query will vary from the result of others.

![A screenshot of a computer Description automatically
generated](./media/image43.png){width="5.39198053368329in"
height="2.6367180664916887in"}

13. Click on **Line 12** and where the query says, **YOUR_TABLE_HERE**,
    replace that with the table name, **InternetSales**.

![A screen shot of a computer Description automatically
generated](./media/image44.png){width="3.8963768591426073in"
height="0.6875962379702537in"}

14. Highlight **Line 12 and 13** and click on the **Run** button in the
    top-left corner of the window.\
    \
    ![A screenshot of a computer Description automatically
    generated](./media/image45.png){width="4.083903105861768in"
    height="1.6043908573928258in"}

15. This query uses the count operator. This query will return an
    aggregated number of records that exist at the time of the query
    execution on the KQL Database table. Feel free to run this query a
    few more times and you should notice that the number of records
    increases after every few seconds.

> ![A screenshot of a computer Description automatically
> generated](./media/image46.png){width="2.173869203849519in"
> height="1.387836832895888in"}

16. Repeat the previous steps for the final query that is automatically
    created for you on **Line 16** and run the query again.

![A screenshot of a
computer](./media/image47.png){width="6.15280949256343in"
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
    ![](./media/image48.emf)

![](./media/image49.png){width="1.4205325896762904in"
height="0.5494510061242345in"}

2.  The comment line "\--" followed by the keyword "explain" will allow
    you to now create a SQL query and return a result with the KQL query
    that could be used to achieve a similar query and result. Below
    input the following query to explain what the KQL query would look
    like:\
    \
    ![](./media/image50.emf)

![A screenshot of a computer Description automatically
generated](./media/image51.png){width="5.583232720909886in"
height="1.6267202537182852in"}

3.  This is a simple SQL query that will retrieve results from the
    InternetSales table to return two columns, the product key and a
    count of the number of orders. Because there is an aggregated column
    and a non-aggregated column, you must use a GROUP BY to return
    results for each individual product. Run the entire query beginning
    with the "\--" to the end of the T-SQL query.

> ![A screenshot of a chat Description automatically
> generated](./media/image52.png){width="3.900337926509186in"
> height="1.6834787839020122in"}

4.  The output of the explain query should be a single record with the
    translated KQL query as the result. Click on the **caret icon (\>)**
    to expand the results and allow for easier translation.

![A screenshot of a computer Description automatically
generated](./media/image53.png){width="6.506944444444445in"
height="0.9243055555555556in"}

5.  Click on the query pane highlighted below in orange. This will allow
    you to select translated KQL query and copy it. Paste this query in
    the KQL Queryset we have been using

![A screenshot of a
computer](./media/image54.png){width="6.506944444444445in"
height="1.44375in"}

6.  With the results in your query pane, highlight and run the query to
    retrieve the results. The **summarize** operator will produce a
    table that aggregates the content of the input table while
    determining how to group each record with the **by Product Key** and
    the **project** operator will select the columns to include, rename,
    or drop while inserting new compute columns.

![A screenshot of a
computer](./media/image55.png){width="6.506944444444445in"
height="2.6006944444444446in"}

7.  Feel free to explore a complete list of SQL to KQL cheat sheet
    operations at the top of your queryset for additional capabilities
    and conversions.

![A close-up of a message Description automatically
generated](./media/image56.png){width="4.858754374453193in"
height="0.7834011373578302in"}

8.  Instead of using KQL, another alternative to querying the results of
    the KQL Database within Fabric is to write and run a T-SQL query.
    Highlight the original SQL statement that was used to translate the
    KQL query and run only that.

![A screenshot of a computer
code](./media/image57.png){width="3.8330030621172355in"
height="1.8617432195975503in"}

9.  This will also yield perfectly valid results without having to
    convert to KQL beforehand.

![A screenshot of a computer Description automatically
generated](./media/image58.png){width="4.427701224846894in"
height="2.4586767279090114in"}

# KQL Queryset

## Task 5: Create a KQL Queryset

1.  While most of the queries within this window were automatically
    created from the user interface, there may be times in the future
    where you wish to save the results of a query to access later in
    your exploration of KQL and working with your real-time data. Within
    the **Explore your data** window, you have several additional
    options for how to accomplish something like this.

2.  Click on the option **Save as KQL queryset**.

![A screenshot of a
computer](./media/image59.png){width="3.430376202974628in"
height="2.7246467629046367in"}

3.  Within the window that appears input the name of the object you're
    creating as **First KQL Query**. Click on **Create**.

![A screenshot of a computer Description automatically
generated](./media/image60.png){width="3.233613298337708in"
height="1.4751279527559056in"}

4.  A OneLake data hub menu may appear allowing you to connect to other
    KQL databases available in your organization. If this does appear,
    select the "**Cancel"** option in the bottom right corner

5.  You will see a new user interface appear when the KQL queryset
    opens. A new object has been created within your workspace that
    allows you to quickly go back to this queryset that you have
    authored and continue to add more queries, pin results to a
    dashboard, or build a Power BI report. Additional capabilities
    within this interface include working with Copilot, should that be
    available to your organization, and exporting results to a CSV file.

![A screenshot of a
computer](./media/image61.png){width="6.506944444444445in"
height="1.3798611111111112in"}

6.  Return to your **RTI_username** workspace. You should have the
    following objects present

![A screenshot of a computer Description automatically
generated](./media/image62.png){width="4.406864610673666in"
height="2.8858191163604547in"}

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
> ![](./media/image63.png){width="2.011388888888889in"
> height="4.476666666666667in"}![](./media/image64.jpg){width="1.8677777777777778in"
> height="4.330555555555556in"}
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
