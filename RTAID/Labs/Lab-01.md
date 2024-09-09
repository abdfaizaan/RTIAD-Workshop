# Microsoft Fabric - Real-Time Intelligence in a Day

![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.001.png)

# Contents 

[Document Structure	2]

[Scenario / Problem Statement	3](#_toc168496499)

[Introduction	3](#_toc168496500)

[Fabric License	4](#_toc168496501)

[Task 1: Enable a Microsoft Fabric trial license	4](#_toc168496502)

[Real-Time Intelligence and Real-Time Hub	7](#_toc168496503)

[Task 2: Real-Time Intelligence Experience Items	7](#_toc168496504)

[Task 3: Real-Time Hub	8](#_toc168496505)

[Create Workspace and Eventhouse	9](#_toc168496506)

[Task 4: Create a Fabric Workspace	9](#_toc168496507)

[Task 5: Create an Eventhouse	11](#_toc168496508)

[References	15](#_toc168496509)


**




























# <a name="_toc168496498"></a>**Document Structure** 
The lab includes steps for the user to follow along with associated screenshots that provide visual aid. In each screenshot, sections are highlighted with orange boxes to indicate the area(s) user should focus on. 
# <a name="_toc168496499"></a>**Scenario / Problem Statement** 
Fabrikam is an e-commerce company specializing in a wide range of outdoor equipment and accessories. The company caters to retail customers globally through its online platform and is planning to enhance its presence in new international markets. There is a new initiative that involves providing real-time insights from an e-commerce site to provide executives with the ability to make timely decisions based on current information.

As an Analytics Engineer on the Sales team, your responsibilities include collecting, cleaning, and interpreting data sets to solve business problems. You create and maintain batch data pipelines, develop visualizations like charts and graphs, build and optimize comprehensive semantic models and reports, and present your findings to decision-makers in the organization.

**Current Challenges**

- You need to handle a continuous stream of real-time data from the e-commerce website, which requires a robust and scalable architecture.
- Ensuring real-time data processing and analytics to keep up with the fast-paced nature of online sales.
- Handling the volume and velocity of data generated by user interactions, transactions, and website activity.
- Integrating real-time streaming data with historical data for comprehensive analysis.
- Using the Medallion architecture in an Eventhouse environment to structure the data flow efficiently.
- Leveraging the Eventhouse Data within a Lakehouse
- You're interested in leveraging Microsoft Fabric to address the above challenges, using Eventhouse, KQL Database, and Eventstream to build a resilient and efficient data processing pipeline.









# ` `**<a name="_toc168496500"></a>Introduction**  
Today you will learn about various key features of Microsoft Fabric. This is an introductory workshop intended to introduce you to the various product experiences and items available in Fabric. By the end of this workshop, you will learn how to use an Eventhouse, Data Pipeline, Eventstream, KQL Queryset and a Real-Time Dashboard. 

By the end of this lab, you will have learned:  

- Explore Fabric Personas
- How to create a Fabric workspace
- How to create an Eventhouse
# <a name="_toc168496501"></a>**Fabric License** 
## <a name="_toc168496502"></a>Task 1: Enable a Microsoft Fabric trial license 
1. Open the **Microsoft Edge** **browser** on the desktop and navigate to <https://app.powerbi.com/>[.](https://app.powerbi.com/) You will be navigated to the login page. **Note:** If you are not using the lab environment and have an existing Power BI account, you may want to use the browser in private / incognito mode. 

   ![A close-up of a browser

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.002.png)

1. Enter the **Username** available in the **Environment Variables** tab (next to the Lab Guide) as the **Email** and click **Submit.** 

![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.003.png)

1. You will be navigated to the **Password** screen. Enter the **Password** available in the **Environment Variables** tab (next to the Lab Guide) shared with you by the instructor.  
1. Click **Sign in** and follow the prompts to sign into Fabric. 





![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.004.png)

1. You will be navigated to the familiar **Power BI Service Home page**. 
1. We assume you are familiar with the layout of Power BI Service. If you have any questions, please do not hesitate to ask the instructor. 



Currently, you are in **My Workspace**. To work with Fabric items, you will need a trial license and a workspace that has Fabric license. Let’s set this up. 



1. On the top right corner of the screen, select the **user** **icon**. 
1. Select **Start trial**. 



![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.005.png)

1. Upgrade to a free Microsoft Fabric trial dialog opens. Select **Start trial**. 



![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.006.png)



1. Select the “**X**” on the top right corner of **Just one last step** dialog to close the dialog. We will not be providing these details as this is a lab environment. 



![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.007.png)

1. Successfully upgraded to Microsoft Fabric dialog opens. Select **Fabric Home Page**.  



![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.008.png)

1. You will be navigated to the **Microsoft** **Fabric Home page**. 

![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.009.png)
# <a name="_toc168496503"></a>**Real-Time Intelligence and Real-Time Hub**
## <a name="_toc168496504"></a>Task 2: Real-Time Intelligence Experience Items
1. Click on the Real-Time Intelligence Experience.

   ![A screenshot of a computer](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.010.png)

1. You will be navigated to <a name="_int_d4xgvm2o"></a>**Real-Time Intelligence Home page**. You will see <a name="_int_giggikcl"></a>**New**, **Recommended**, and **Quick Access** categories.  With the **New** category notice the items:  
   1. **Eventhouse:** Used to create a workspace of one or multiple KQL database(s), which can be shared across projects. Also creates a KQL Database within the Eventhouse.
   1. **KQL <a name="_int_5ny4ijkw"></a>Queryset:** Used to run queries on the data to produce shareable tables and visuals.** 
   1. **Real-Time Dashboard**: A collection of tiles, optionally organized in pages, where each tile has an underlying query and a visual representation.
   1. **Eventstream:** Used to capture, transform, and route real-time event stream.** 
   1. **Reflex:** For automatically taking actions when patterns or conditions are detected in changing data.
   1. **Use a sample:** Sample solution.** 

![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.011.png)
## <a name="_toc168496505"></a>Task 3: Real-Time Hub
1. Click on the **Real-Time hub** within the Fabric navigation pane on the left side of the screen.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.012.png)

1. The Real-Time hub is the single place for streaming data-in-motion across your entire organization. Every Microsoft Fabric tenant is automatically provisioned with the hub. It enables you to easily discover, ingest, manage, and consume data-in-motion from a wide variety of sources.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.013.png)

1. Within the Real-Time hub you have access to three different types of data integration.
- **Data streams**: For your running eventstreams and KQL databases, all the stream outputs from eventstreams and tables from KQL databases automatically show up in Real-Time hub.
- **Microsoft sources**: Lists all streaming resources from Microsoft services. Whether it’s Azure Event Hubs, Azure IoT Hub, or other services, you can seamlessly ingest data into Real-Time hub.
- **Fabric events:** Events that are generated via Fabric artifacts and external sources, are made available in Fabric to support event-driven scenarios like real-time alerting and triggering downstream actions. You can monitor and react to events including Fabric workspace item events and Azure Blob Storage events.

![A close-up of a word

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.014.png)

1. In the top-right corner of the Real-Time hub, click on the **+ Get events** button.

   ![A green rectangular sign with white text

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.015.png)

1. A window will appear and will detail the currently available streams of data that are available to integrate into the Real-Time hub.  This includes a mixture of Azure sources as well as external cloud streaming sources like Amazon Kinesis, Confluent Cloud Kafka, and Google Cloud Pub/Sub.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.016.png)

1. **Close** the Get events window by clicking the “X” in the upper right corner.

# <a name="_toc168496506"></a>**Create Workspace and Eventhouse**
## <a name="_toc168496507"></a>Task 4: Create a Fabric Workspace 
1. Now let’s create a workspace with Fabric license. Select **Workspaces** from the left navigation bar. A dialog opens. 
1. Select **New workspace**. 



![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.017.png)

1. **Create a workspace** dialog opens on the right side of the browser. 
1. In the **Name** field enter <a name="_int_xpfpfkuj"></a>**RTI\_username**.  Use the username provided to you from the environment details. 

**Note:** The workspace name must be unique. Make sure a green check mark with “**This name is available**” is displayed below the Name field. 

1. If you choose, you can enter a **Description** for the workspace. This is an optional field. 
1. Click on **Advanced** to expand the section. 

![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.018.png)

1. Under **License mode**, make sure **Trial** is selected. (It should be selected by default.) 
1. Select **Apply** to create a new workspace. 



   ![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.019.png)

## <a name="_toc168496508"></a>Task 5: Create an Eventhouse

1. Click the **+ New** box to find all the items you can create in this Fabric workspace.

   ![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.020.png)

1. Select the **Eventhouse** option from the drop-down list. As we have talked about this can be looked at similarly to a Lakehouse in that we can store data but focused around real time data.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.021.png)

1. In the window that appears, give your Eventhouse the name, **eh\_Fabrikam** and click on **Create**.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.022.png)

1. This is where you will ultimately stream data from various sources through the rest of the training today. When the item is created, a window will appear giving you some details about the Eventhouse.  Click on the **Get started** button.

   ![A screenshot of a computer screen

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.023.png)

1. Take a quick tour of the Eventhouse by following the green tooltips on your screen.  This first one shows that an empty Kusto Query Language (KQL) Database was created with the Eventhouse.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.024.png)

1. Follow the remainder of the tooltips around the screen to show you where to create additional databases, check the storage in OneLake of the Eventhouse, check the usage of Fabric resources in compute minutes, and finally see what actions have occurred in the Eventhouse.
1. Within the navigational pane of the Eventhouse, find your KQL Database that was created alongside the Eventhouse.  Click on the ellipses (…) and then select the option **Open in new tab**.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.025.png)

1. This will allow us to still have one tab in our browser to see the overview of our entire Eventhouse and a new tab to focus on the KQL Database properties. One goal that we wish to accomplish in our scenario is ensuring that the data streamed to the KQL database is accessible via OneLake. By enabling this feature, we make the data in this KQL Database easily discoverable through shortcuts to be used in any Lakehouse we may want. Click on the pencil icon next to the **OneLake availability** property.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.026.png)

1. ` `Enable this property by toggling the switch to **Active** and then click on **Done** at the bottom of the window.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.027.png)

1. ` `Return to your **RTI\_username** workspace.
1. ` `If you see the **Task Flows** option, grab the anchor point in the middle of the screen and slide the menu up to the top of your screen to hide. 

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.028.png)
1. ` `You now have the basis for how you will begin to ingest the streaming data into your OneLake.  The next step is to create a stream of data that can receive the data in motion.

   ![A screenshot of a computer

Description automatically generated](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.029.png)

In this lab, we explored the Real-Time Intelligence interface, examined the Real-Time hub, created a Fabric workspace, and an Eventhouse that came with a KQL Database.  In the next lab, you will begin to explore techniques that ingest data from various sources across your data estate to OneLake and do some basic analysis with the Kusto Query Language (KQL).







# <a name="_toc168496509"></a>**References** 
Fabric Real-time Intelligence in a Day (RTIIAD) introduces you to some of the key functions available in Microsoft Fabric. 

In the menu of the service, the Help (?) section has links to some great resources. 





![](Aspose.Words.2c713640-7076-47ff-9afb-e3b735b7d3f1.030.png)

Here are a few more resources that will help you with your next steps with Microsoft Fabric. 

- See blog post to read the full[ ](https://aka.ms/Fabric-Hero-Blog-Ignite23)[Microsoft Fabric GA](https://aka.ms/Fabric-Hero-Blog-Ignite23)[ ](https://aka.ms/Fabric-Hero-Blog-Ignite23)[announcement](https://aka.ms/Fabric-Hero-Blog-Ignite23)[ ](https://aka.ms/Fabric-Hero-Blog-Ignite23)
- Explore Fabric through the [Guided Tour](https://aka.ms/Fabric-GuidedTour)[ ](https://aka.ms/Fabric-GuidedTour)
- Sign up for the [Microsoft Fabric free trial](https://aka.ms/try-fabric)[ ](https://aka.ms/try-fabric)
- Visit the [Microsoft Fabric website](https://aka.ms/microsoft-fabric)[ ](https://aka.ms/microsoft-fabric)
- Learn new skills by exploring the [Fabric Learning modules](https://aka.ms/learn-fabric)[ ](https://aka.ms/learn-fabric)
- Explore the [Fabric technical documentation](https://aka.ms/fabric-docs)[ ](https://aka.ms/fabric-docs)
- Read the [free e](https://aka.ms/fabric-get-started-ebook)[-](https://aka.ms/fabric-get-started-ebook)[book on getting started with Fabric](https://aka.ms/fabric-get-started-ebook)[ ](https://aka.ms/fabric-get-started-ebook)
- Join the[ ](https://aka.ms/fabric-community)[Fabric community](https://aka.ms/fabric-community)[ ](https://aka.ms/fabric-community)to post your questions, share your feedback, and learn from others 

Read the more in-depth Fabric experience announcement blogs: 

- [Data Factory experience in Fabric blog](https://aka.ms/Fabric-Data-Factory-Blog)[ ](https://aka.ms/Fabric-Data-Factory-Blog) 
- [Synapse Data Engineering experience in Fabric blog](https://aka.ms/Fabric-DE-Blog)[ ](https://aka.ms/Fabric-DE-Blog) 
- [Synapse Data Science experience in Fabric blog](https://aka.ms/Fabric-DS-Blog)[ ](https://aka.ms/Fabric-DS-Blog) 
- [Synapse Data Warehousing experience in Fabric blog](https://aka.ms/Fabric-DW-Blog)[ ](https://aka.ms/Fabric-DW-Blog) 
- [Real](https://aka.ms/Fabric-RTA-Blog)[-](https://aka.ms/Fabric-RTA-Blog)[Time Intelligence experience in Fabric blog](https://blog.fabric.microsoft.com/en-us/blog/category/real-time-intelligence)[ ](https://aka.ms/Fabric-RTA-Blog)
- [Power BI announcement blog](https://aka.ms/Fabric-PBI-Blog)[ ](https://aka.ms/Fabric-PBI-Blog)
- [Data Activator experience in Fabric blog](https://aka.ms/Fabric-DA-Blog)[ ](https://aka.ms/Fabric-DA-Blog) 
- [Administration and governance in Fabric blog](https://aka.ms/Fabric-Admin-Gov-Blog)[ ](https://aka.ms/Fabric-Admin-Gov-Blog)
- [OneLak](https://aka.ms/Fabric-OneLake-Blog)[e](https://aka.ms/Fabric-OneLake-Blog)[ ](https://aka.ms/Fabric-OneLake-Blog)[in Fabric blog](https://aka.ms/Fabric-OneLake-Blog)[ ](https://aka.ms/Fabric-OneLake-Blog)
- [Dataverse and Microsoft Fabric integration blog](https://aka.ms/Dataverse-Fabric-Blog)[ ](https://aka.ms/Dataverse-Fabric-Blog)



© 2024 Microsoft Corporation. All rights reserved. 

By using this demo/lab, you agree to the following terms: 

The technology/functionality described in this demo/lab is provided by Microsoft Corporation for purposes of obtaining your feedback and to provide you with a learning experience. You may only use the demo/lab to evaluate such technology features and functionality and provide feedback to Microsoft. You may not use it for any other purpose. You may not modify, copy, distribute, transmit, display, perform, reproduce, publish, license, create derivative works from, transfer, or sell this demo/lab or any portion thereof. 

COPYING OR REPRODUCTION OF THE DEMO/LAB (OR ANY PORTION OF IT) TO ANY OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS EXPRESSLY PROHIBITED. 

THIS DEMO/LAB PROVIDES CERTAIN SOFTWARE TECHNOLOGY/PRODUCT FEATURES AND 

FUNCTIONALITY, INCLUDING POTENTIAL NEW FEATURES AND CONCEPTS, IN A SIMULATED 

ENVIRONMENT WITHOUT COMPLEX SET-UP OR INSTALLATION FOR THE PURPOSE DESCRIBED 

ABOVE. THE TECHNOLOGY/CONCEPTS REPRESENTED IN THIS DEMO/LAB MAY NOT REPRESENT FULL 

FEATURE FUNCTIONALITY AND MAY NOT WORK THE WAY A FINAL VERSION MAY WORK. WE ALSO 

MAY NOT RELEASE A FINAL VERSION OF SUCH FEATURES OR CONCEPTS. YOUR EXPERIENCE WITH USING SUCH FEATURES AND FUNCITONALITY IN A PHYSICAL ENVIRONMENT MAY ALSO BE DIFFERENT. 

**FEEDBACK**. If you give feedback about the technology features, functionality and/or concepts described in this demo/lab to Microsoft, you <a name="_int_i8mu0xdh"></a>give to Microsoft, without charge, the right to use, share and commercialize your feedback in any way and for any purpose. You also give to third parties, without charge, any patent rights needed for their products, technologies and services to use or interface with any specific parts of <a name="_int_4uyyojom"></a>a Microsoft software or service that includes the feedback. You will not give feedback that is subject to a license that requires Microsoft to license its software or documentation to third parties because we include your feedback in them. These rights survive this agreement. 

MICROSOFT CORPORATION HEREBY DISCLAIMS ALL WARRANTIES AND CONDITIONS WITH REGARD 

TO THE DEMO/LAB, INCLUDING ALL WARRANTIES AND CONDITIONS OF MERCHANTABILITY, 

WHETHER EXPRESS, IMPLIED OR STATUTORY, FITNESS FOR A PARTICULAR PURPOSE, TITLE AND NON-

INFRINGEMENT. MICROSOFT DOES NOT MAKE ANY ASSURANCES OR REPRESENTATIONS WITH REGARD TO THE ACCURACY OF THE RESULTS, OUTPUT THAT DERIVES FROM USE OF DEMO/ LAB, OR SUITABILITY OF THE INFORMATION CONTAINED IN THE DEMO/LAB FOR ANY PURPOSE. 

**DISCLAIMER** 

This demo/lab contains only a portion of new features and enhancements in Microsoft Power BI. Some of the features might change in future releases of the product. In this demo/lab, you will learn about some, but not all, new features. 

Version: 08.2024                                Copyright 2024 Microsoft                                                            17|Page  

Maintained by:  Microsoft Corporation  
