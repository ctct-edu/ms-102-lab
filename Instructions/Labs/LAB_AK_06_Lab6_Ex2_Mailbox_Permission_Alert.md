# Learning Path 6 - Lab 6 - Exercise 2 - Implement Mailbox Permission Alert

In this exercise you will configure and test an alert that will notify Lynne Robbins when FullAccess permissions are granted to any mailbox within Adatum.

### Task 1 – Create a Mailbox Permission Alert

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as Holly Dickson. 

2. **Microsoft 365 Defender** should still be open in your Edge browser from the prior task. Select the **Microsoft 365 Defender** tab now. In the left-hand navigation pane, under the **Email & collaboration** section, select **Policies & rules**. 

3. On the **Policies & rules** window, select **Alert policy**. If a dialog box appears indicating the alert policy portal has been updated, select the **Dismiss** button.

4. In the **Alert Policy** window, note the message at the top of the page indicating the fact that mail flow alerts have moved to the Exchange admin center. Mail flow alerts can no longer be maintained in the Microsoft 365 Defender security portal. Since you will be creating a mailbox permission alert and not a mail flow alert, you can continue on with this task in the Microsoft 365 Defender portal. <br/> 

	In the **Alert Policy** window, review the list of preconfigured alert policies that are available in Microsoft 365. Select **+New Alert Policy** on the menu bar. This initiates the **New Alert Policy** wizard.

5. On the **Name your alert, categorize it, and choose a severity** page, enter the following information:

	- Name: **Mailbox permission change**

	- Description: **This alert notifies Lynne Robbins when FullAccess permissions are granted to any mailbox in Adatum Corporation**

	- Severity: **Medium**

	- Category: **Permissions**

6. Select **Next**.

7. On the **Choose an activity, conditions and when to trigger the alert** page, enter the following information:

	- Activity is: select the drop-down arrow in the field, enter **mail** in the **Select an activity** field, and select **Granted mailbox permission** from the list of activities containing **mail**

	- How do you want the alert to be triggered?: **Every time an activity matches the rule**

8. Select **Next**.

9. On the **Decide if you want to notify people when this alert is triggered** page, enter the following information:

	- Email recipients: Select the "X" to the right of **Holly Dickson's** account to remove her, the enter **Lynne** in the field, and then select **Lynne Robbins** from the list of users whose first name starts with **Lynne**

	- Daily notification limit: **No limit**

10. Select **Next**.

11. On the **Review your settings** page, review the settings and if anything needs to be corrected, select its corresponding **Edit** option and make the necessary corrections. <br/>

	When everything is correct, under the **Do you want to turn the policy on right away?** setting, select **Yes, turn it on right away**. Select **Submit**.

12. On the **New Alert Policy** window, select **Done**.

13. Verify your new alert policy appears in the list on the **Alert policy** page, its **Type** is set to **Custom**, and its **Status** in **On**.

14. Leave the Alert policy tab in your Edge browser open for the next task.

You have now created an activity alert in Microsoft 365 Defender that is triggered when FullAccess permissions are granted to any mailboxes.


### Task 2 – Validate the Mailbox Permission Alert

In the prior task, you configured an alert that will notify Lynne Robbins when FullAccess permissions are granted to any mailbox within Adatum. To test this alert, Holly Dickson will change the FullAccess permission on Alex Wilber’s mailbox by granting Joni Sherman FullAccess to his mailbox. This activity should trigger the alert policy that you just created, which should send an alert notification email to Lynne Robbins’ mailbox. You will then log into LON-CL2 as Lynne Robbins and see if she received this email. 

1. On LON-CL1, in your Edge browser, you should still be logged into Microsoft 365 as **Holly Dickson**. 

2. In your Edge browser, select the **Microsoft 365 admin center** tab, and then in the left-hand navigation pane, under the **Admin centers** group, select **Exchange**. This opens the Exchange admin center for Exchange Online.

3. In the **Exchange admin center**, the **Manage Mailboxes** window appears by default (if it doesn't, then in the left-hand navigation pane, under the **Recipients** group, select **Mailboxes**). 

4. In the **Manage Mailboxes** window, select **Alex Wilber** from the list of mailboxes (select Alex's name; do not select the check box to the left of his name).

5. In the **Alex Wilber** pane that appears, the **General** tab is displayed by default. Select the **Delegation** tab.

6. On the **Delegation** tab, there are three mailbox permissions that can be updated: **Send as**, **Send on behalf**, and **Read and manage (Full Access)**. You want to add each of these permissions for Alex's mailbox to **Joni Sherman**. For each permission, perform the following steps to add Joni to that permission: <br/>

	- Select the **Edit** button for the permission. 
	- On the **Manage mailbox delegation** pane, select **+Add members**.
	- In the list of users that appears, select the check box for **Joni Sherman** and then select **Save**.
	- In the **Add delegate permissions?** pane, select **Confirm**.
	- Once the mailbox permission is added to Alex's mailbox, select the back arrow at the top of the pane. 
	- This returns you to the **Delegation** tab on the **Alex Wilber** pane, which displays the three permissions. Repeat these steps for each of the two remaining permissions. 

7. Once you have assigned Joni to each of the three permissions on the **Delegation** tab, select the **X** in the upper right-hand corner to close the **Alex Wilber** pane. 

8. Since **Holly Dickson** has changed the mailbox permissions for Alex Wilber by giving Joni Sherman full access permissions to his mailbox, an alert email should automatically be sent to Lynne Robbins’ Inbox that notifies her of this event. You will verify this email was sent by checking Lynne's Inbox on LON-CL2. <br/>

	‎Switch to **LON-CL2**. 

9. On **LON-CL2**, you should be signed into the machine as the local **administrator** (lon-cl2\admin) account. Select the **Microsoft Edge** icon in the taskbar, maximize the window (if necessary), and then enter the following URL in the address bar: **https://outlook.office365.com**

10. In the **Pick an account** window, if Lynne Robbins account (**LynneR@xxxxxZZZZZZ.onmicrosoft.com**) appears in the user list, then select it now; otherwise, select **Use another account** and sign in as **LynneR@xxxxxZZZZZZ.onmicrosoft.com** (where xxxxxZZZZZZ is the tenant prefix provided by your lab hosting provider). Then enter the same **Microsoft 365 Tenant Password** provided by your lab hosting provider for the tenant admin account (i.e. the MOD Administrator account) as Lynne's password.

11. Lynne Robbins’ **Inbox** should include an email from the Alerts notification system (**Office365Alerts@microsoft.com**) to let her know that Holly Dickson has made a Mailbox permission change. <br/>

	**WARNING:** Lab testing has shown that in some cases, it can take up to 15 minutes or so for the email to be received in Lynne's Inbox. You may need to refresh Outlook one or more times until you receive the email.

12. Once the notification email arrives in Lynne's Inbox, open the email and review the contents. Scroll to the bottom of the email and select the **View alert details** button. This opens the **Microsoft 365 Defender** portal in a new tab.

13. The **Microsoft 365 Defender** portal displays the **Alerts** window, and it automatically opens the **Mailbox permission change** pane for this alert activity that triggered the email notification to Lynne. <br/>

	Scroll down through the **Mailbox permission change** pane and review all the information for this activity. When you are done, select **Close** to close the pane.

14. In your Edge browser, close the **View Alerts - Microsoft 365 security** tab. Leave Lynne's **Outlook** tab open, as you will use that in the next lab exercise.


You have just successfully tested a mailbox permission alert that sent an alarm message on granting FullAccess to a user mailbox.

# Proceed to Lab 6 - Exercise 3
