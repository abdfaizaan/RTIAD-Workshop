**Microsoft Fabric**

Real-Time Intelligence in a Day

Lab 5

Version:

October 2024

> Contents

[Document Structure [3](#document-structure)](#document-structure)

[Introduction [3](#introduction)](#introduction)

[Real-Time Dashboards [3](#real-time-dashboards)](#real-time-dashboards)

[Task 1: Create a Real-Time Dashboard
[3](#task-1-create-a-real-time-dashboard)](#task-1-create-a-real-time-dashboard)

[Task 2: Connect a Data Source to Real-Time Dashboard
[5](#task-2-connect-a-data-source-to-real-time-dashboard)](#task-2-connect-a-data-source-to-real-time-dashboard)

[Task 3: Create a Real-Time Dashboard Tile with KQL
[7](#task-3-create-a-real-time-dashboard-tile-with-kql)](#task-3-create-a-real-time-dashboard-tile-with-kql)

[Task 4: Add More Dashboard Tiles to Real-Time Dashboard
[12](#task-4-add-more-dashboard-tiles-to-real-time-dashboard)](#task-4-add-more-dashboard-tiles-to-real-time-dashboard)

[Task 5: Add Map Visual for Impressions by Location
[19](#task-5-add-map-visual-for-impressions-by-location)](#task-5-add-map-visual-for-impressions-by-location)

[Task 6: Setup Auto Refresh on the Real-Time Dashboard
[22](#task-6-setup-auto-refresh-on-the-real-time-dashboard)](#task-6-setup-auto-refresh-on-the-real-time-dashboard)

[Optional Task 7: Add Company Logo
[24](#optional-task-7-add-company-logo)](#optional-task-7-add-company-logo)

[Optional Task 8: Apply Conditional Formatting to Visual
[25](#optional-task-8-apply-conditional-formatting-to-visual)](#optional-task-8-apply-conditional-formatting-to-visual)

[Summary [27](#summary)](#summary)

[References [27](#references)](#references)

# Document Structure 

> The lab includes steps for the user to follow along with associated
> screenshots that provide visual aid. In each screenshot, sections are
> highlighted with orange boxes to indicate the area(s) user should
> focus on.

# Introduction 

> In this lab, you will use the data you have streamed and loaded into
> your KQL Database and succinctly linked to a Lakehouse using shortcuts
> to create a Real-Time Dashboard for visualizing and sharing your
> insights from the data streams you accessed.
>
> By the end of this lab, you will have learned:

-   Creating a Real-Time Dashboard in Fabric

-   Using KQL to write queries to populate visuals in a dashboard

-   Adding conditional formatting to dashboard visuals

# Real-Time Dashboards

## Task 1: Create a Real-Time Dashboard

1.  Open the **Fabric workspace** for the course.

> ![A screenshot of a
> computer](.\media\lab-05/media/image5.png){width="4.591741032370954in"
> height="4.8269739720035in"}

2.  Click on the **+ New** **Item** button to create a new item.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image6.png){width="3.3963068678915134in"
height="1.354355861767279in"}

3.  You will see a category for **Visualize Data**. Click on the item
    called **Real-Time Dashboard**.

![A screenshot of a
computer](.\media\lab-05/media/image7.png){width="5.58254593175853in"
height="2.3950732720909884in"}

4.  Give your Real-Time Dashboard the name **RTI Dashboard** and then
    click on **Create**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image8.png){width="3.550307305336833in"
height="2.1251837270341207in"}

5.  You should be immediately taken to a blank instance of a Real-Time
    Dashboard.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image9.png){width="5.609581146106737in"
height="3.2466119860017497in"}

## Task 2: Connect a Data Source to Real-Time Dashboard

1.  Under the Home ribbon find the option called **New data source** and
    click it.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image10.png){width="4.300372922134733in"
height="2.3001990376202976in"}

2.  In the flyout pane that appears on the right-hand side of the
    screen, click on **Add +** and then choose **OneLake data hub**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image11.png){width="3.058597987751531in"
height="1.8918307086614172in"}

3.  A list of available sources in your OneLake will appear, only
    sources from KQL Databases will be listed so one option will be
    available for you, the **eh_Fabrikam** KQL Database. Select that
    option.

![A screenshot of a
computer](.\media\lab-05/media/image12.png){width="4.37093394575678in"
height="1.8453160542432197in"}

4.  At the bottom of the screen click **Connect**.

![A green and orange rectangle with white text Description automatically
generated](.\media\lab-05/media/image13.png){width="2.100181539807524in"
height="0.9250798337707786in"}

5.  You will now be able to create the data source. Click on the **Add**
    button at the bottom of the flyout pane.

![A screenshot of a
computer](.\media\lab-05/media/image14.png){width="2.290734908136483in"
height="3.1663987314085738in"}

6.  You will now see that one data source has been added to the
    Real-Time Dashboard. From here you could add additional KQL
    Databases should the need arise. For now, click on **Close** at the
    bottom of the window.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image15.png){width="2.7513035870516185in"
height="2.817485783027122in"}

## Task 3: Create a Real-Time Dashboard Tile with KQL

1.  Click on the blank tile within the dashboard to populate the tile
    with a visual.

![A screenshot of a web page Description automatically
generated](.\media\lab-05/media/image16.png){width="4.440943788276465in"
height="3.161447944006999in"}

2.  By default you will connect to the KQL Database you created earlier
    as your source. From here you can write out your own KQL query to
    populate this visual with data. Delete all previous markdown KQL
    that is there by default. Copy and paste the following query into
    the query window.

![](.\media\lab-05/media/image17.emf)

3.  Run the query once you have it configured correctly to see the
    results.

![A screenshot of a
computer](.\media\lab-05/media/image18.png){width="4.637340332458443in"
height="3.1345844269466316in"}

4.  Notice that you may only have one result in your output. This is
    because of the **Time range** that is set by default for this tile.
    You have a parameter with which you can alter the range of time with
    which you are returning data from. The eventDate between
    (\_startTime..\_endTime) is what allows you to take advantage of
    this parameter. Modify the **Time Range** parameter to **Last 3
    hours** and observe how your output changes.

![A screenshot of a search box Description automatically
generated](.\media\lab-05/media/image19.png){width="3.025262467191601in"
height="3.0419302274715663in"}

5.  You should now see in your query output the results of clicks over
    the last 3 hour window.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image20.png){width="3.2169455380577427in"
height="1.8501607611548556in"}

6.  While this parameter can be modified, you may wish for it to default
    to a specific time range instead of forcing users to modify it.
    Above the time range option, click on the **@ Parameters** option.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image21.png){width="3.4796522309711286in"
height="1.3126837270341207in"}

7.  Click the **pencil icon** to edit the **Time range** parameter.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image22.png){width="3.0837642169728783in"
height="2.6253663604549433in"}

8.  Change the **Default value** to **Last 24 hours** to always show the
    last day by default. Click **Done** when finished.

![A screenshot of a
computer](.\media\lab-05/media/image23.png){width="3.260262467191601in"
height="4.778741251093614in"}

9.  Close the parameter pane.

10. Now click on the **+ Add visual button** above the query results.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image24.png){width="2.495428696412948in"
height="1.5195264654418197in"}

11. A new flyout will appear on the right-hand side of the screen. Click
    in the text box underneath the **Tile name** option to give this
    visual the name **Clicks by Hour**.

![A screenshot of a computer screen Description automatically
generated](.\media\lab-05/media/image25.png){width="2.3072878390201224in"
height="1.2554363517060367in"}

12. By default, the visual that you're using to display the results of
    this KQL query is a table. This may not be the best way for someone
    to quickly consume and comprehend what is happening with the results
    of your data. Change the type of visual from a table to an **Area
    chart**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image26.png){width="2.6078762029746283in"
height="2.208082895888014in"}

13. With this newly formatted visual, you can better understand the
    peaks and valleys of Clicks from your e-commerce site using the data
    stream you created earlier in this class.

![A graph on a screen Description automatically
generated](.\media\lab-05/media/image27.png){width="4.552276902887139in"
height="3.78582239720035in"}

14. To save this visual down to the Dashboard, click on the **Apply
    changes** button in the top-right corner of the screen.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image28.png){width="3.4586329833770777in"
height="1.7751541994750657in"}

15. Once this visual has been placed within the Dashboard, notice again
    that the visual is only showing the last hour of results. Modify the
    Dashboard to show the **Time Range** of the **Last 24 hours**.

![A graph with blue lines Description automatically
generated](.\media\lab-05/media/image29.png){width="5.917179571303587in"
height="4.100355424321959in"}

16. Refresh the visual and notice that the results will slightly change
    to reflect the data that has come in since the last execution of the
    query.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image30.png){width="2.908584864391951in"
height="1.4334580052493437in"}

## Task 4: Add More Dashboard Tiles to Real-Time Dashboard

1.  From the **Home ribbon** in the Real-Time Dashboard click on the
    **New tile** button.

![A screenshot of a phone Description automatically
generated](.\media\lab-05/media/image31.png){width="5.750728346456693in"
height="1.0777241907261592in"}

2.  Enter the following KQL query into the query pane.

![](.\media\lab-05/media/image32.emf)

3.  **Run** the query.

![A screenshot of a
computer](.\media\lab-05/media/image33.png){width="3.8143339895013124in"
height="3.118733595800525in"}

4.  Click the **+ Add** visual button.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image34.png){width="3.191943350831146in"
height="1.6584765966754156in"}

5.  Edit the visual to change the **Tile name** to **Impressions by
    Hour** and the **Visual Type** to **Area chart**.

![A screenshot of a screenshot of a computer Description automatically
generated](.\media\lab-05/media/image35.png){width="2.8835826771653545in"
height="3.867001312335958in"}

6.  Apply changes to the visual.

![A close up of a sign Description automatically
generated](.\media\lab-05/media/image36.png){width="3.0419302274715663in"
height="0.5250459317585302in"}

7.  Add another **+ New tile**.

![A screenshot of a graph Description automatically
generated](.\media\lab-05/media/image37.png){width="6.506944444444445in"
height="2.7881944444444446in"}

8.  Copy and paste the following query into the query pane. Note, this
    is a multi-statement query that uses multiple let statements & a
    query combined by semicolons.

![](.\media\lab-05/media/image38.emf)

9.  **Run** the query to view the results.

![A screenshot of a
computer](.\media\lab-05/media/image39.png){width="4.595047025371828in"
height="3.9999507874015747in"}

10. Click the **+ Add visual** button.

11. When the visual settings appear modify the following settings to
    create a count of Impressions.

-   **Tile name** - Impressions

-   **Visual type** - Stat

-   **Value column** - impressions (long)

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image40.png){width="2.7752405949256342in"
height="5.342129265091864in"}

12. Choose **Apply changes** when all settings are configured
    appropriately.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image41.png){width="3.6866874453193352in"
height="0.9378412073490814in"}

13. On the new tile, click on the ellipses (...) and select the option
    to **Duplicate tile**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image42.png){width="3.3919608486439197in"
height="3.016928040244969in"}

14. Click on the **pencil icon** for the duplicated tile to edit the
    configurations.

![A screenshot of a computer game Description automatically
generated](.\media\lab-05/media/image43.png){width="3.666984908136483in"
height="1.6418088363954506in"}

15. Rename this **Tile name** to **Clicks** and change the **Value
    column** to **clicks (long)**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image44.png){width="2.4476388888888887in"
height="5.703999343832021in"}

16. Apply the changes to this visual.

17. Duplicate either one of the new tiles one more time to create one
    final stat visual.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image45.png){width="3.758659230096238in"
height="1.4751279527559056in"}

18. Edit the new tile to change the **Tile name** to **Click Through
    Rate** and the **Value column** to **CTR (long)**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image46.png){width="2.741903980752406in"
height="4.7254090113735785in"}

19. Apply the changes.

20. If the tiles are separated or you wish to reorganize them, you can
    hover over the tile until a hand icon appears and drag and drop the
    visual where you wish.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image47.png){width="1.991839457567804in"
height="1.5418000874890638in"}

## Task 5: Add Map Visual for Impressions by Location

1.  Add a **New tile** to the Real-Time Dashboard.

![A screenshot of a phone Description automatically
generated](.\media\lab-05/media/image48.png){width="6.506944444444445in"
height="1.1256944444444446in"}

2.  Copy and paste the following query into the query pane. This query
    extracts the latitude and longitude from the Ip address column from
    this data stream to generate a location that you can plot on a map.
    This query can take a little bit more time than the previous ones.

![](.\media\lab-05/media/image49.emf)

3.  Execute the query to validate that it is configured correctly. Click
    the **+ Add visual** button.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image50.png){width="3.2502821522309713in"
height="2.3752055993000876in"}

4.  Change the **Tile name** to **Impressions by Location** and the
    **Visual type** to **Map**.

![A screenshot of a phone screen Description automatically
generated](.\media\lab-05/media/image51.png){width="2.5335531496062993in"
height="3.133604549431321in"}

5.  Under the **Visual type** area ensure that the latitude and
    longitude are selected appropriately by modifying the **Define
    location by** option to **Latitude and Longitude** and verify that
    the remaining fields match the image below.

![A screenshot of a map Description automatically
generated](.\media\lab-05/media/image52.png){width="3.4919695975503062in"
height="4.092020997375328in"}

6.  Apply the changes.

7.  Grab the anchor point on the bottom left of the map visual within
    the Dashboard to increase the size of the visual.

![A map of the world Description automatically
generated](.\media\lab-05/media/image53.png){width="5.508811242344707in"
height="3.591978346456693in"}

8.  All the visuals are resizable and movable. Feel free to rearrange
    yours how you wish.

![A screenshot of a computer screen Description automatically
generated](.\media\lab-05/media/image54.png){width="6.506944444444445in"
height="3.2868055555555555in"}

9.  Save your changes.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image55.png){width="2.858581583552056in"
height="1.4834623797025372in"}

## Task 6: Setup Auto Refresh on the Real-Time Dashboard

1.  Click on the **Manage ribbon** and then select the option **Auto
    Refresh**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image56.png){width="5.2754571303587054in"
height="0.7250623359580053in"}

2.  Turn on the toggle to enable **Auto Refresh**.

![A close up of a box Description automatically
generated](.\media\lab-05/media/image57.png){width="2.5335531496062993in"
height="0.9917530621172354in"}

3.  Modify the **Minimum time interval** to 30 seconds and the **Default
    refresh rate** to 1 minute.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image58.png){width="2.558555336832896in"
height="2.1251837270341207in"}

4.  Click **Apply** at the bottom of the window.

5.  In the top-right corner of your menu, click on the **Editing
    button** and modify it to **Viewing** to see what your end users
    will experience with this Real-Time Dashboard.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image59.png){width="4.533725940507437in"
height="1.5167979002624672in"}

6.  If time allows and you are interested in retrieving a company logo
    or applying conditional formatting to your visuals as shown below,
    feel free to work through the optional tasks below. Otherwise, the
    lab is complete!

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image60.png){width="6.506944444444445in"
height="2.9194444444444443in"}

## Optional Task 7: Add Company Logo

1.  Just as we did before switch from the **Viewing** mode of the
    dashboard to the **Editing** mode\
    \
    ![A screenshot of a
    computer](.\media\lab-05/media/image61.png){width="3.566284995625547in"
    height="1.6116863517060367in"}

2.  Click on the button in the Home ribbon called **New text tile**.

![A screenshot of a phone Description automatically
generated](.\media\lab-05/media/image62.png){width="4.834950787401575in"
height="0.8338615485564305in"}

3.  Copy and paste the following markdown code within the query window.

![](.\media\lab-05/media/image63.emf)

![A screenshot of a
computer](.\media\lab-05/media/image64.png){width="3.5932589676290463in"
height="1.4829385389326335in"}

4\. Apply the changes.

5\. Resize and move the tile to fit somewhere within your Real-Time
Dashboard. ![A screenshot of a
computer](.\media\lab-05/media/image65.png){width="6.145399168853893in"
height="3.1068022747156605in"}

6\. Save your changes.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image55.png){width="2.858581583552056in"
height="1.4834623797025372in"}

## Optional Task 8: Apply Conditional Formatting to Visual

1.  Click on the **pencil icon** on the **Click Through Rate** visual.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image66.png){width="2.4335444006999123in"
height="2.475214348206474in"}

2.  At the bottom of the visual formatting pane, click on the **+ Add
    rule** button underneath **Conditional formatting**.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image67.png){width="3.4252963692038496in"
height="2.6585640857392825in"}

3.  Click the **pencil icon** to edit the conditional formatting rule.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image68.png){width="3.0286701662292215in"
height="0.9945997375328084in"}

4.  Modify the conditions of the rule to point to the **Column** called
    **CTR (long)** and make the rule **\> 10** for the operator and
    value.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image69.png){width="5.456585739282589in"
height="2.0155008748906384in"}

5.  Feel free to modify the Formatting however you wish. As long as the
    value of the CTR is greater than 10 it will appear on that visual.

![A close-up of a white rectangular object Description automatically
generated](.\media\lab-05/media/image70.png){width="5.673273184601925in"
height="0.8083048993875765in"}

6.  Click the **Save** button within the Conditional formatting pane.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image71.png){width="1.8158234908136484in"
height="1.8715999562554682in"}

7.  Apply the changes.

8.  Save your changes.

![A screenshot of a computer Description automatically
generated](.\media\lab-05/media/image55.png){width="2.858581583552056in"
height="1.4834623797025372in"}

# Summary

> In this lab, users created a Real-Time Dashboard and connected it to
> our KQL Database. We got to see that we use the KQL language to curate
> queries and then we can visualize the results in many ways, with each
> visual having its own configuration. As well we saw how we could
> modify the default parameter available in the dashboard and make it so
> the dashboard will automatically refresh.

# References 

> Fabric Real-Time Intelligence in a Day (RTIIAD) introduces you to some
> of the key functions available in Microsoft Fabric. In the menu of the
> service, the Help (?) section has links to some great resources.
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
