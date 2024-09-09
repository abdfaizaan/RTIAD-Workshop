# Lab 2

The lab includes steps for the user to follow along with associated screenshots that provide visual aid. In each screenshot, sections are highlighted with orange boxes to indicate the area(s) user should focus on.

## Introduction

In this lab, you will experience a way to handle a continuous stream of real-time data. You will use a Fabric Real-Time Intelligence object called an Eventstream to ingest this data to the Eventhouse you created in the last lab and write some basic KQL queries.

By the end of this lab, you will have learned:

- How to create an Eventstream
- Load Real-time data into a KQL Database
- Write basic Kusto Query Language Queries

## Fabric Real-Time Hub

### Task 1: Create an Event Stream Source

1. Open the **Fabric workspace** you created in the last lab. From here we can see the Eventhouse we created.

    ![A screenshot of a computer](./media/image5.png)

2. Navigate to the "Real-Time hub" where currently we do not see any streams of data. That will change shortly.

    ![A screenshot of a computer](./media/image6.png)

3. Select the "Get events" green button which should be in the upper right corner.

    ![A screenshot of a search box](./media/image7.png)

4. A window will open that will allow you to select a source for our stream data. As we discussed before, there are many fantastic options to choose from but for this class we will select the option "Azure Event Hubs".

    ![A screenshot of a computer](./media/image8.png)

5. You are now required to create a connection to the Azure Event Hub. Click on the **New connection** text since you do not currently have a connection.

    ![A screenshot of a computer](./media/image9.png)

6. From your environment details page, copy and paste all the necessary connection settings into the appropriate fields. For these labs we are connecting to an Event Hub which has streaming data being sent from a python notebook. This notebook is creating fake sales transactions at a rate of around 3,100 transactions per hour.

    - Event Hub namespace: **realtimeconsumersiad**
    - Event Hub: **rti-iad**
    - Shared Access Key Name: **rti-reader**
    - Shared Access Key: **H/5gTWuI+lQLT9HYBzuqzPdKaR6YWXCRw+AEhE6k1gE=**

7. Once all properties have been filled out click on **Connect**.

    ![A screenshot of a computer](./media/image10.png)

8. In the configuration of the Azure Event Hub data source, you will need to modify the **Consumer group** of the Event Hub to ensure that you gain access to a unique access point to the stream of data. Within your **Environment details** find the property that lists what your consumer group name will be and place that into the field box. It will appear something like "**cg-xx**".

    ![A screenshot of a computer](./media/image11.png)

9. Before we finalize this data source and Eventstream, let's go ahead and rename our Eventstream to something more useful. In the "Stream details" section on the right select the pencil icon next to the "Eventstream name" and let's call our Eventstream "**es_Fabrikam_InternetSales**".

    ![A screenshot of a computer](./media/image12.png)

10. Now we can click on **Next**, which will take us to a final overview page.

    ![A screenshot of a computer](./media/image13.png)

11. In this overview screen, verify the contents look correct and click **Create source**.

    ![A screenshot of a computer](./media/image14.png)

12. Once the Eventstream and Eventstream source are created select the option "**Open Eventstream**".

    ![A screenshot of a computer](./media/image15.png)

13. This will take you to the Eventstream user interface. Here is where you will see able to connect with a source stream of data, bring it into this Fabric item, and then stream it to a new destination like a Lakehouse or KQL Database.

14. It may take a few moments for your Source to be **Active** but after waiting a few moments, click on the middle icon with the name of your Eventstream on it and then click on **Refresh** if you do not see a preview of the data.

    **Note: If you receive a "Warning" status around and audit policy, that is fine. The stream will still function**

    ![A screenshot of a computer](./media/image16.png)

15. You should now see a sample of the data within the bottom window.

    ![A screenshot of a computer](./media/image17.png)

16. This will show you a preview of the data that is being received from the Azure Event Hub. If you slide your bottom horizontal scroll bar all the way to the right-side of your preview, you will be able to see the time that the data has been received in the Event Hub in two columns called **EventProcessedUtcTime** and **EventEnqueuedUtcTime**. This should reflect the current date/time in UTC format.

    ![A screenshot of a computer](./media/image18.png)

### Task 2: Setup Eventstream Destination

1. Click on the tile within the canvas area labeled "Switch to edit mode to Transform event of add destination".

    ![A screenshot of a computer](./media/image19.png)

2. Within the Eventstream user interface, click on the **Transform events or add destination** option to open the drop-down menu.

    ![A screenshot of a computer](./media/image20.png)

3. View the list of available operations that can be made to the stream.

    ![A screenshot of a phone](./media/image21.png)

4. Look below the operations and you will find the **Destinations**. Select the option that says **KQL Database**.

    ![A screenshot of a computer](./media/image22.png)

5. A new menu will open on the right-hand side of the screen. The first thing you need to modify for the destination is the **data ingestion mode**. The two options are **Direct Ingestion** and **Event processing before ingestion**. Because we are not going to transform anything in our Eventstream and directly load this information in a KQL database table ensure that you have selected the **Direct ingestion** option.

    ![A white background with black text](./media/image23.png)

6. Modify the remainder of the settings with the following details below.

    - Destination name: **eh-kql-db-Fabrikam**
    - Workspace: **RTI_username**
    - KQL Database: **eh_Fabrikam**

    ![A screenshot of a computer](./media/image24.png)

7. Click on Save.

8. With the Eventstream configured, click on the **Publish** button to save this Eventstream and begin your ingestion.

    ![A screenshot of a computer](./media/image25.png)

9. Choose the **Configure** option within the **Destination** to correctly map the stream to a table in the KQL Database.

    ![A screenshot of a chat](./media/image26.png)

10. Click on the **+ New table** option underneath the **eh_Fabrikam** database.

    ![A screenshot of a computer](./media/image27.png)

11. Give the new table the name, **InterentSales** and then click on the checkmark.

    ![A screenshot of a computer](./media/image28.png)

12. You may need to update your **"Data connection name"** to meet requirements. Let us rename it to **"eh_Fabrikam_es_InternetSales"**. Then we can click on **Next**.

    ![A screenshot of a computer](./media/image29.png)

13. After a few moments of searching for events, the user interface should allow you to see that sample data was found. Click on **Finish** at the bottom of the screen.

    ![A screenshot of a computer](./media/image30.png)

14. After this you will be shown a summary. Once you have all green checkmarks, click **close** to move forward.

15. Once you see the user interface showing the mappings from the source to the Eventstream to the destination, you have correctly configured and started a stream of data into your KQL Database.

    ![A screenshot of a chat](./media/image31.png)

