
# Deploy and Run the Process (25 mins)

### 2.3.1 Create new Space
- Using the breadcrumbs navigation, navigate back to Spaces
- Click on the **Add Space** button to the top right
- In the **Add Space** dialog, give the new Space the name **NewSpace**
- Click on the **New Space** tile


### 2.3.2 Import Full Project

- Click the **Import Projec** button
- In the **Import Project** Dialog, provide the URL: https://github.com/relessawy/procurement-process-final
- Click on the Import button
- Now click on the procurment-process tile to select it, then click on the Ok button to the top right

### 2.3.3 Full Project
- With the full project now loaded in the new Space we create, feel free to explore the completed business process
- We can now package our project and deploy it on the Execution Server. To do this:
- Click on the **Deploy** button in the upper-right corner of the screen. This will package and deploy our project.
- If all goes well, you'll see two green pop-ups verifying the deployment

![SuccessMsg]({% image_path m2p5_SuccessMsg.png %})

### 2.3.3 Run the complete process

- In this section, you will execute the process deployed on the Process Execution Server via the Business Central workbench
- Navigate to Menu → Manage → Process Definitions. 

![ProcessDef]({% image_path m2p6_ProcessDef.png %})

- If everything is correct, the order-management process will be listed. 
- Click on the kebab icon of the order-management process and click on **Start** to run the process.

![StartProcess]({% image_path m2p6i2_StartProcess.png %})

- You will be greeted with the start form that we created in the previous step
- Click the **Submit** button

![StartForm]({% image_path m2p6i3_StartForm.png %})

- You are now in the **Process Instance Details** screen, note that the instance state is active and the active user task is **Request Offer** as expected

![ProcessInstance]({% image_path m2p6i4_ProcessInstance.png %})


- Click on the **Diagram** tab to open the process instance diagram
- The process instance Diagram shows the current state of the process, which path was taken, and what is the current active step

![ProcessDiagram]({% image_path m2p6i5_ProcessDiagram.png %})

- The process is in a **wait** state at the **Request Offer** task. 
- Navigate to Menu → Track -> Task Inbox

![TaskInbox]({% image_path m2p6i6_TaskInbox.png %})


- Remeber when we set the actor for the **Request Offer** task to pamAdmin (your user) in the process model?  This is why **RH PAM** assigned this task to your user and notified you with meassage in your inbox

![RequestOfferTask]({% image_path m2p6i7_RequestOfferTask.png %})

- Click on the **Request Offer** task to open its task window

![OpenRequestOfferTask]({% image_path m2p6i8_OpenRequestOfferTask.png %})

- Click on the **Start** button to start working on the task. 
- Fill in the request form as follows:
- **Item name**: MackBook Pro
- **Urgency**: high
- **Target Price**: 100
- **Supplier Name**: JB HiFi
- Then click the Complete button  

![FilledRequestOfferTask]({% image_path m2p6i9_FilledRequestOfferTask.png %})

- Navigate to Menu-> Manage ->Process Instance
- Click on the **OrderAsset** process instance

![OrderAssetProcessInstance]({% image_path m2p6i10_OrderAssetProcessInstance.png %})

- In the Process Instance screen, click on the **Diagram** tab
- The process has now progressed to the **Prepare Order** task node. 

![ProcessProgressToPrepareOffer]({% image_path m2p6i11_ProcessProgressToPrepareOffer.png %})

- You can also click on the Logs tab to get more details on which user claimed a task, when it was started, updated, and completed

![Logs]({% image_path m2p6i12_Logs.png %})

- Now navigate to Menu -> Track -> Task Inbox again, where you'll find the next task **Prepare Offer** waiting for you

![PrepareOfferTask]({% image_path m2p6i13_PrepareOfferTask.png %})

- Click on the Prepare Offer task in your inbox, then click the **Start** button
- Enter 130 for SupplierPrice
- Click the **Complete** button

![PrepareOfferTaskComplete]({% image_path m2p6i14_PrepareOfferTaskComplete.png %})

- Navigate to Menu-> Manage ->Process Instance
- Click on the orderAsset process instance
- In the Process Instance scree, click on the **Diagram** tab
- Notice that because the supplier's offer was higher than target price even with the high tolerance (130 > 100*1.25), so the **Auto Approval** rule was evaluated to **false** and we progressed to the **Manual Approval** task

![ProcessDesignAtManualApproval]({% image_path m2p6i15_ProcessDesignAtManualApproval.png %})

- Navigate back to your Inbox (Menu -> Track -> Task Inbox), and is you migh expect the **Manual Approval** task is now waiting for you

![ManualApprovalTask]({% image_path m2p6i16_ManualApprovalTask.png %})

- Click on the Manual Approve task in your inbox, then click the **Start** button
- Check the Approved field 
- Click the **Complete** button

![ManualApprovalComplete]({% image_path m2p6i17_ManualApprovalComplete.png %})

- Navigate to Menu-> Manage ->Process Instance
- Note that your process is no longer there
- In the Filters list to the left, click on the Completed state, now your process is visible

![ProcessFilter]({% image_path m2p6i18_ProcessFilter.png %})

- Click on the orderAsset process instance
- In the Process Instance scree, click on the **Diagram** tab
- Notice that the process has reach the end event **Send to ERP**

![m2p6i19_FinishProcess]({% image_path m2p6i19_FinishProcess.png %})

- Run a couple more process instances with different values to test, for example, the functionality of the Automated Approval Rules.



