# Rule Authoring (20 mins)

Our Procurement process contains a Business Rule Task, but we have not yet defined the Decision Model that will be used in the task. In this lab we will implement the automatic approval rules in the form of a DMN model.

- Use the breadcrumb navigator at the top-left of the screen to navigate back to our procurement-process project
- Click on the blue Add Asset button in the top-right corner
- Select Decision from the drop-down menu in the upper-left corner, and click on the DMN tile

![DMNTile]({% image_path m2p1i1_DMNTile.png %}){:width="600px”}

- In the **Create new DMN** dialog give the rule the name **order-approval**, and click the **+OK** button

![DMNNewDialog]({% image_path m2p1i2_DMNNewDialog.png %})}

In the DMN editor, open the property-panel on the right-side of the screen and set the Namespace property to: http://www.redhat.com/pam-workshop/procurement-process-dmn

![NameSpace]({% image_path m2p1i3_NameSpace.png %})}

### 2.1.1 Create Data Types for rule

- We will use two data types in our **DMN Model** 
    - An enumerator called urgency to restict the possible values to high or low
    - The data model that we created in the previous model
- In the DMN editor, click on the Data Types tab

![DataTypes]({% image_path m2p1i4_DataTypes.png %})}

- Click on the **Add a customer Data Type** button

![AddCustomerDataType]({% image_path m2p1i5_AddCustomerDataType.png %})}

- In the editor provide the following
    - **Name**: urgency
    - **Type**: String (from the drop down list)
    
![UrgencyType]({% image_path m2p1i6_UrgencyType.png %})}

- Click the **Add Constraints** link
- Select constraint type as **Enumeration** from the drop down list
- Click the **+Add** button and provide the value **high**, then click on the check mark
- Once more click the **+Add** button, and provide the value **low**, then click on the check mark 
- Click the **OK** button

![AddConstraintsDialog]({% image_path m2p1i7_AddConstraintsDialog.png %})}

- Click the check mark to the far right to save the new data type

![SaveConstraint]({% image_path m2p1i8_SaveConstraint.png %})}

- Next click on the **Import Data Object** button
- Select the OrderInfo object, and click the **Import** button

![ImportData]({% image_path m2p1i9_ImportData.png %})}

- If all goes well you should see a confirmation in green indicating that the Data Object was converted into a DMN data type successfully

![ImportSuccess]({% image_path m2p1i10_ImportSuccess.png %})}


---
![Save]({% image_path m0_save.png %}){:align="left"} 

Remember to save your progress 

---

### 2.1.2 Create Order Info Input

- Navigate back to the model by click on the Model tab
- From the left menu, drag a DMN input data to the canvas

![DMNInputMenu]({% image_path m2p1i11_DMNInputMenu.png %})}

- Give it the name **Order Information**, this has to be the same name as the input you provided to the **Auto Approval** node in the previous model


---
![Info]({% image_path m0_info.png %}){:align="left"} 

Unlike many traditional expression languages, Friendly Enough Expression Language (FEEL) supports spaces and a few special characters as part of variable and function names

---

- Open **Diagram Properties** for this input, click the **Data Type** drop down list and select the new data type we just imported: **OrderInfo**

![OrderInfoInput]({% image_path m2p1i12_OrderInfoInput.png %})}


---
![Info]({% image_path m0_info.png %}){:align="left"} 

You can change the background and font for each element in DMN, using the Background details and Font settings sections under the Properties pane. This only enhances the visibility of the model, but has no impact on the behaviour of the model

---

### 2.1.3 Create Price Tolerance Business Knowledge Model

- We now want to create a **Business Knowledge model** that calculates the price tolerance based on the urgency of the order


---
![Info]({% image_path m0_info.png %}){:align="left"} 

A Business Knowledge Model element (BKM) represents a reusable piece of decision logic. Typically, it is connected to a Decision element which invokes the BKM and passes on a set of inputs. The BKM, using it's internal logic, evaluates an output which is passed back to the Decision.

---

![BKM]({% image_path m2p1i13_BKM.png %})}

- Click on the **Price Tolerance** node, and the click on the **Edit** button to start editing the node

![BKMEdit]({% image_path m2p1i14_BKMEdit.png %})}

- You now see the boxed expression of this node, feel free to resize it to your convinience

![PriceToleranceBoxedEx]({% image_path m2p1i15_PriceToleranceBoxedEx.png %})}

- Click on the **Edit Parameters** link, an editor will open. 
- Click on **Add parameter** button. Name the parameter **order info**  and set the type to **OrderInfo**
- Click anywhere outside the **Edit Parameters** dialog to return to the **Price Tolerance Function editor**

![PriceTolerance_Input]({% image_path m2p1i16_PriceTolerance_Input.png %})}

- Right click in the empty white cell under the parameter definitions and select **Clear**. The text **Select expression** will appear in the cell.
- Click on the cell and select **Decision Table**.

![DecisionTableExpression]({% image_path m2p1i17_DecisionTableExpression.png %})}

- Click in the header of the first column (input-1) to add an input to decision table
- The name of the input clause is **order info.urgency**, which references the urgency attribute of the order information parameter. 
- Set the type to **Urgency**, which references the **urgency** enumeration we created earlier.

![orderinfo_urgency]({% image_path m2p1i18_orderinfo_urgency.png %})}

- Set the name of the output clause to **Price Tolerance** and data type to **number**. Leave the name empty.

![DecisionTableOutput]({% image_path m2p1i19_DecisionTableOutput.png %})}

- Click on the Price Tolerance cell (top cell of the table), and set the data type to number

![BKM_Output]({% image_path m2p1i20_BKM_Output.png %})}

- Implement the first row of the decision table as follows

![DT_FirstRow]({% image_path m2p1i21_DT_FirstRow.png %})}

- Now click the validate button in the upper right menu

![ValidateButton]({% image_path m2p1i22_ValidateButton.png %})}

- Note that the modeler detects a gap in the rules you specified in the table because one of the possible values of the enumerator Urgency is missing, i.e. you need to define a rule for the value “low”

![ValidateError]({% image_path m2p1i23_ValidateError.png %})}

- Define the second rule in the decision table as follows and save your model
- To add a rule, right click on the Decision table and click on **insert below**


![FinalDecisionTable]({% image_path m2p1i24_FinalDecisionTable.png %})}


---
![Save]({% image_path m0_save.png %}){:align="left"} 

Remember to save your progress 

---

### 2.1.4 Create Approve Decision Node

- Navigate back to the model by clicking on the **Back to order-approval** link at the top-left of the editor.
- Drag a **DMN Decision** node to the canvas, and name it Approve

![ApproveDecisionNode]({% image_path m2p1i25_ApproveDecisionNode.png %})}

- Connect the **Order Information** input and the **Price Tolerance** business knowledge model node to the **Approve** decision node.

![ConnectDMNModel]({% image_path m2p1i26_ConnectDMNModel.png %})}

- Select the **Approve** decision node and click on the **Edit** button.
- Click on **Select Expression**, and set the logic type to **Literal Expression**.

![DecisionLiteralExpression]({% image_path m2p1i27_DecisionLiteralExpression.png %})}

- Click on the **Approve** cell (top cell of the table), and set the data type to **boolean**.
- Enter the following expression:

`Order Information.supplierPrice < Price Tolerance(Order Information) * Order Information.targetPrice`

![RuleExpression]({% image_path m2p1i28_RuleExpression.png %})}

- Navigate back to the model by clicking on the **Back to order-approval** link at the top-left of the editor.
- Our DMN model is now complete. Make sure to save your model.
- With our DMN model implemented, we can now revisit our Business Rules Task in our BPMN2 model. 
- Open the **Project Explorer** to the left of the screen

![ProjectExplorer]({% image_path m2p1i29_ProjectExplorer.png %})}

- Expand the **Business Processes** section and click on OrderAsset

![BuinssProcessOrderAsset]({% image_path m2p1i30_BuinssProcessOrderAsset.png %})}

- Open the Auto Approval node Diagram Properties 
- Expand Implementation/Execution section and set the Namespace field to: `http://www.redhat.com/pam-workshop/procurement-process-dmn`
- DMN Model Name: **order-approval**


---
![Save]({% image_path m0_save.png %}){:align="left"} 

Remember to save your progress 

---




