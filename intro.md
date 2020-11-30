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
