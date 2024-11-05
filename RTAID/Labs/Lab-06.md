**Microsoft Fabric**

Real-Time Intelligence in a Day


> Contents

[Document Structure [3](#document-structure)](#document-structure)

[Scenario / Problem Statement [3](#_Toc171420411)](#_Toc171420411)

[Introduction [4](#introduction)](#introduction)

[Creating an Alert with Reflex
[4](#creating-an-alert-with-reflex)](#creating-an-alert-with-reflex)

[Task 1: Use the Real-Time Dashboard to Set Alerts
[4](#task-1-use-the-real-time-dashboard-to-set-alerts)](#task-1-use-the-real-time-dashboard-to-set-alerts)

[Task 2: Test Email Alert from Reflex Experience
[7](#task-2-test-email-alert-from-reflex-experience)](#task-2-test-email-alert-from-reflex-experience)

[Task 3: Create A New Reflex Object from Data Stream
[9](#task-3-create-a-new-reflex-object-from-data-stream)](#task-3-create-a-new-reflex-object-from-data-stream)

[Clean Up Resources [12](#clean-up-resources)](#clean-up-resources)

[Task 4: Clean Up Workspace
[12](#task-4-clean-up-workspace)](#task-4-clean-up-workspace)

[Summary [14](#summary)](#summary)

[References [14](#references)](#references)

# Document Structure 

> The lab includes steps for the user to follow along with associated
> screenshots that provide visual aid. In each screenshot, sections are
> highlighted with orange boxes to indicate the area(s) user should
> focus on.

# Introduction 

> In this lab, you will learn how to leverage Data Activator to create a
> Reflex to send out alerts from our newly created Real-Time dashboard.
> As well we will see how we can extend the usage of Reflex to create
> additional custom alert on the data we are streaming into our
> Eventhouse
>
> By the end of this lab, you will have learned:

-   Creating a Reflex from the Alert Option on a Real-Time Dashboard

-   Using Data Activator Reflex Items to Create More Custom Alerts

# Creating an Alert with Reflex

## Task 1: Use the Real-Time Dashboard to Set Alerts

1.  Open the **Fabric workspace** for the course and select the
    Real-Time Dashboard you created in the last lab.

> ![A screenshot of a computer Description automatically
> generated](.\media\Lab-06/media/image5.png){width="4.501556211723535in"
> height="2.226781496062992in"}

2.  On the **Click Through Rate** visual click on the ellipses (...) and
    select the option to **Set alert**.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image6.png){width="3.9067957130358706in"
height="1.7398261154855643in"}

3.  A new flyout will open on the right-side of the screen. You can see
    what you are monitoring from the dashboard including the specific
    visual that the alert will be affiliated with. The condition is
    something you have full control over. Modify the **Condition** to
    **Is less than**.

![A screenshot of a
computer](.\media\Lab-06/media/image7.png){width="2.6462904636920386in"
height="3.676334208223972in"}

4.  A new field will appear for you to input a **Value** modify this to
    be **20**.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image8.png){width="2.5938068678915136in"
height="2.5938068678915136in"}

5.  You have three possible actions currently available for what type of
    alert you wish to receive once the Data Activator Reflex item
    recognizes that your condition has been met. Choose the option of
    **Message me in Teams**.

![A screenshot of a
computer](.\media\Lab-06/media/image9.png){width="2.593876859142607in"
height="1.6487401574803149in"}

6.  Finally, you need to decide the location where you will store the
    **Reflex item** that you are creating with this alert. This by
    default should select your current workspace, but you need to
    specifically call out a **New item** under the Item drop-down menu.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image10.png){width="2.3079483814523183in"
height="1.3924628171478566in"}

7.  Rename the item to **CTR Reflex** and then click on **Create**. This
    will take a few moments to create.

![A screenshot of a
computer](.\media\Lab-06/media/image11.png){width="2.3794575678040246in"
height="2.4501345144356956in"}

8.  You will receive a validation that the reflex alert was created.
    Click on the **Open** button to open the Reflex.

![A screenshot of a
phone](.\media\Lab-06/media/image12.png){width="2.323155074365704in"
height="4.023380358705162in"}

9.  This will take you to the formal **Reflex experience**. From here
    you can monitor the stream of data in real-time, view the Data that
    is used to support the Reflex, and create additional Triggers from
    the same stream.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image13.png){width="6.506944444444445in"
height="2.3048611111111112in"}

## Task 2: Test Email Alert from Reflex Experience

1.  From the **CTR is less than 20** trigger click on the **Send me a
    test alert** button to get a sample message in teams from the
    Reflex.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image14.png){width="6.248724846894138in"
height="1.4104647856517936in"}

2.  Open a New tab within your Environment Edge Browser and go to
    **Teams.Microsoft.com**.

3.  Sign in with your environment credentials if you are asked. A
    message to start a trial may appear and you will want to accept
    this.

4.  You should have a message within teams letting you know that the CTR
    is less than 20.

![A screenshot of a computer error
message](.\media\Lab-06/media/image15.png){width="3.8257097550306214in"
height="2.464785651793526in"}

5.  Navigate back to the Reflex experience and let's create another
    trigger.

## Task 3: Create A New Reflex Object from Data Stream

1.  On the bottom left corner of the screen next to the Fabric Persona
    Switcher click on the tab that says **Data**.

![](.\media\Lab-06/media/image16.png){width="2.9184241032370952in"
height="0.913490813648294in"}

2.  The **Data view** shows your stream of data and what is possible to
    monitor based on the source of data and the query that is returning
    that data. With this you are currently using that stream to push
    data to an **Object** this is where you have set a condition and a
    trigger to alert you based on the incoming stream. Let's create a
    new object and make another trigger with the same stream. Go back to
    the **Design** view.

![A close up of a logo Description automatically
generated](.\media\Lab-06/media/image17.png){width="2.894339457567804in"
height="0.9803390201224846in"}

3.  Create a **New Trigger** from this data stream.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image18.png){width="3.24742782152231in"
height="3.026451224846894in"}

4.  Click on the **pencil** icon and give this Trigger the name,
    **Clicks Greater Than 30,000** (you can choose a value here that
    falls more in line with however much data you have streamed in).

![A screenshot of a
computer](.\media\Lab-06/media/image19.png){width="4.953421916010499in"
height="1.601357174103237in"}

5.  To begin, you need to monitor one of the columns from the data
    stream. Click on **Select a property or event column**. Work through
    the cascading levels until you eventually see a list of all the
    columns and select **Clicks**.

![A screenshot of a
computer](.\media\Lab-06/media/image20.png){width="5.6775164041994755in"
height="1.8504943132108487in"}

6.  Now that you are monitoring a column from the stream, you need to
    set up the conditions to **Detect** when you alert the user. Click
    in the Detect drop-down box that reads **Choose a type of
    detection**.

![A close up of a sign Description automatically
generated](.\media\Lab-06/media/image21.png){width="2.7502384076990376in"
height="0.8500732720909886in"}

7.  Using the **Numeric** type of detection, find the **Is greater
    than** option towards the bottom of the list.

![A screenshot of a
computer](.\media\Lab-06/media/image22.png){width="3.73126312335958in"
height="2.9620986439195103in"}

8.  Modify the logical expression to read **Is greater than 30000 Each
    time** using the various drop-downs.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image23.png){width="4.632181758530184in"
height="0.8965507436570429in"}

9.  For the last step, you need to set up how this Reflex will **Act**.
    Choose the option that says **Teams message**.

![A screenshot of a message box Description automatically
generated](.\media\Lab-06/media/image24.png){width="2.68787510936133in"
height="2.0106977252843397in"}

10. The default settings for the email will be sufficient for this
    example.

![A screenshot of a
phone](.\media\Lab-06/media/image25.png){width="2.9252340332458444in"
height="3.2817465004374453in"}

11. Finally, **Save** and **Start** this Trigger.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image26.png){width="4.708990594925634in"
height="1.1251574803149607in"}

12. You now have two triggers that are monitoring the same data stream.

![](.\media\Lab-06/media/image27.png){width="3.059142607174103in"
height="2.4559317585301836in"}

# Clean Up Resources

## Task 4: Clean Up Workspace

1.  This is the last lab and last part of Real-Time Analytics in a Day.
    If you have completed the lab and have no further questions or needs
    from the instructor on the content, please help us by deallocating
    the workspace. Navigate to the **RTI_username** workspace.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image28.png){width="3.4037095363079617in"
height="3.7893996062992126in"}

2.  Click on the **Workspace Settings** in the top-right corner.

![](.\media\Lab-06/media/image29.png){width="5.833838582677165in"
height="0.4750415573053368in"}

3.  From the **General** workspace settings, scroll down and click on
    the **Remove this workspace** button.

![A screenshot of a computer Description automatically
generated](.\media\Lab-06/media/image30.png){width="3.8949442257217846in"
height="4.295430883639545in"}

4.  Lab and Class Complete!

# Summary

> In this lab, we walked through using Data Activator. With this feature
> you can connect directly to real-time dashboards or streams of data
> and create triggers on that data. These triggers can then be
> configured with detection conditions and once those conditions are met
> and action can be taken. Within this lab we used the ability to send
> an email when certain conditions were met within our triggers. Data
> Activator is still in preview so new actions may be come available in
> the future.

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
