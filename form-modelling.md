# Form Modelling (25 mins)

In this section we are going to create the process start and user-task forms. There are two techniques to generate forms in Red Hat Process Automation Manager
- We could simply generate these forms with the click of a button, which gives us some standard forms based on the process and task data.
- Or we could use the Form Modeler tool which allows us to design these forms to our specific needs.
In this lab we will show both techniques. 

- Let’s start by modeling the form that the **Purchasing Manager** will use to request an asset e.g. laptop

- Use the **breadcrumb navigator** at the top-left of the screen to navigate back to our **procurement-process** project
- Click on the **OrderAsset** buinsess process
- In the **OrderAsset** process click on the **Request Offer** user task
- Now click on the **Generate Task Form** to the top left of the task
![GenerateTaskForm]({% image_path m2p3i5_GenerateTaskForm.png %})
- Navigate back to the **procurement-process** project and filter the assets by selecting **Form** from the drop down list
- Note that two forms were created 
- **RequestOffer-taskform** that will be used by users to interact with the **Request Offer** task
- And **com_my_space_procurement_process_OrderInfo** which is modeled after the fields of the OrderInfo Object
- In fact **RequestOffer-taskform** uses this form internally to read and write the OrderInfo data object
- Click on the **RequestOffer-taskform** and let's modify this form a bit
- Click on the Kebab icon to the right of the Outputs field and click on **Remove**

![RemoveOutput]({% image_path m2p3i6_RemoveOutput.png %})

- Navigate back to the **procurement-process** project and this time click on the **com_my_space_procurement_process_OrderInfo**
- Click on the Kebab icon next to the **Item Name** field and click **edit**
- Configure this field as follows
- Click the +OK button when done

![ItemField]({% image_path m2p3i4_ItemField.png %})

- Click on the **Urgency** field and drag it next to **Item Name** field
- Click on the **Edit** button for this field and configure it as follows
- Click the +OK button when done

![UrgencyField]({% image_path m2p3i7_UrgencyField.png %})

- Now click on the Kebab icon to the right of the **Supplier Price** field and click on **Remove**
- Your form should like this when your done

![OrderInfoRequestOffer]({% image_path m2p3i8_OrderInfoRequestOffer.png %})

- Save your form and navigate back to the **procurement-process** project 
- Click on the **RequestOffer-taskform**, note that the form has been renedered according to changes you made in the **com_my_space_procurement_process_OrderInfo** form

Now lets create a form from scratch
- Navigate back to the **procurement-process** project, click the **Add Asset** button
- Select the Form tile
- In the **Create new Form** dialog
- Select on **OrderAsset** in the **Select Proces:s** drop down list
- And then select **Start Process Form** in the **Select Form:** drop down list
- Keep the Form name that is generated for you and clikc the **OK** button

![StartForm]({% image_path m2p3i9_StartForm.png %})
- In the **Form Modeler** expand the **Form Controls** sections to the left
- Drag an HTML control to the canvas
- Click on the **Insert Image** icon

![InsertImage]({% image_path m2p3i10_InsertImage.png %})
- Enter the following URL in the **Image:** field
`https://static.redhat.com/libs/redhat/brand-assets/latest/corp/logo.svg`
- **Alignment**: Default 
- Remove the text "Add your HTML here..."
- Click the **OK** button

![ImageDialog]({% image_path m2p3i11_ImageDialog.png %})

- Drag another HTML control to the canvas
- Type "To start the procurement process click on the Submit button"
- Modify your text format to H3 + Bold and click the **OK** button

![TextDialog]({% image_path m2p3i12_TextDialog.png %})

- Save your form

![FinishedStartForm]({% image_path m2p3i13_FinishedStartForm.png %})

What remains is modleing the forms for the **Prepare Offer** and **Manual Approval** tasks, this is very similar to waht you did for the **Request Offer** task so instead of modeling them from scratch you can download those forms and import them directly into your project

- Download the follwing four files
    - OrderForm-PrepareOffer.frm
    - OrderForm-ManualApproval.frm
    - PrepareOffer-taskform.frm
    - ApproveOffer-taskform.frm

- Navigate back to the **procurement-process** project, click the **Import Asset** button
- Select the **Choose File** button, below the **Please select a file to upload** field

![SelectAFile]({% image_path m2p3i13_m2p3i14_SelectAFile.png %})

- Select the OrderForm-PrepareOffer.frm from the path you download the file, then click the **Open** button
- Provide the name **OrderForm-PrepareOffer** in the **Import Asset** field
- Click the **+OK** button

![ImportPrepareOfferForm]({% image_path m2p3i15_ImportPrepareOfferForm.png %})

- Save your form
- Repeat the same steps for the three remaining forms
- Note that the form name should be the same as the file name
- Once your done, the implementation of our process is complete. It’s now time to deploy and run our process

---
![Save]({% image_path m0_save.png %}){:align="left"}

Remember to save.
---













