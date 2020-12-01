
# Correcting errors (10 mins)

During process instance execution, a lot of things can go wrong. Like for example users might fill in incorrect data, we will now explore how we can manually change the process to another state by restarting an already completed User Task. 

- To test this we want to complete the Prepare Offer task in such a way that the order is not automatically approved and the process proceeds to the Approve User Task 

- Start a new process instance of our Order Management process.
- Navigate to Menu → Manage → Process Definitions. 
- Click on the kebab icon of the order-management process and click on **Start** to run a new process instance
- Just like before click the **Submit** button at the process start form
- Navigate to your Inbox (Menu -> Track -> Task Inbox), and open the **Request Offer** task
- Click on the **Start** button, and provide input like before
    - Item Name: MacBook Pro
    - Urgency: high
    - Target Price: 100
    - Supplier Name: JB HiFi
- Click the **Complete** button
- Navigate back to your Inbox (Menu -> Track -> Task Inbox), and open the **Prepare Offer** task
- Click on the **Start** button, and once more provide input like before
    - Supplier Price = 130
- Click the **Complete** button
- Now navigate to Menu-> Manage-> Process Instances
- Click on the OrderAsset process and switch to the Diagram tab
- Observe that the process is now waiting at the **Manual Approval** task
- In the Diagram, click on the **Prepare Offer** task
- In the **Node Actions** panel on the left-hand-side of the screen, verify that the **Prepare Offer** node is selected and click on the **Trigger** button. 

![TriggerPrepareOffer]({% image_path m2p7i1_TriggerPrepareOffer.png %})

- Observe that the **Prepare Offer** user task has been activated.

![PrepareOfferTriggered]({% image_path m2p7i2_PrepareOfferTriggered.png %})

- Although we have re-activated the **Prepare Offer** node, we have not yet de-activated the **Manual Approval** task. Click on the active **Manual Approval** task and expand the Node Instances section in the Node Actions panel. Click on the kebab icon of the active **Manual Approval** instance and click on Cancel

![CancelManualApproval]({% image_path m2p7i3_CancelManualApproval.png %})

- Navigate to your **Task Inbox**. Observe that the **Manual Approval** user task is not there, instead the **Prepare Offer** task is re-assigned.
- Open the **Prepare Offer** task
- Click on the **Start** button, this time provide input the will set the process to auto-approve the offer
    - Supplier Price = 100
- Click the **Complete** button
- Navigate to Menu-> Manage ->Process Instance
- In the Filters list to the left, click on the Completed state
- Click on the last OrderAsset process to rune, should be Id 2
- Observe that the process has now accepted the offer and moved to the end event **Send to ERP**
