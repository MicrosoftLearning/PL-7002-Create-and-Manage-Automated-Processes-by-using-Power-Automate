---
lab:
  title: 'Lab 4: Approval flow'
  module: 'Module 3: Build approval flows with Power Automate'
  description: In this lab you will create an approval flow.
  duration: 30 minutes
  level: 100
  islab: true
---

# Practice Lab 4 – Approval flow

In this lab you will create an approval flow.

## What you will learn

- How to create a Power Automate approvals cloud flow

## High-level lab steps

- Create an automated cloud flow for the SharePoint list
- Create an approval
- Add condition for approval outcome
- Test the flow
  
## Prerequisites

- Must have completed **Lab 3: SharePoint**

## Detailed steps

## Exercise 1 – Create approval flow

### Task 1.1 - Create the trigger

1. Navigate to the Power Automate portal `https://make.powerautomate.com`

1. Make sure you are in the **Dev One** environment.

1. Select the **+ Create** tab from the left navigation panel.

1. Select **Automated cloud flow**.

1. Enter `Task approval` for **Flow name**.

1. Enter `SharePoint` in Search all triggers.

1. Select **When an item is created**.

1. Select **Create**.

### Task 1.2 - Configure the trigger

1. Select the **When an item is created** step.

1. Select the **When an item is created** step name and enter `New task`.
> [!NOTE]
> If you encounter an issue editing the trigger name, use **Copilot** to rename it.  
> Select **Copilot**, and in the Copilot chat enter the following prompt:
> `Rename the trigger to New task`.

1. Select the **Power Automate SharePoint site** created in the previous lab. If the site is not listed, select **Enter custom value** and paste the URL of the Power Automate SharePoint site

1. Select the **Tasks** list.

    ![Screenshot of SharePoint trigger.](../media/sharepoint-trigger.png)

### Task 1.3 - Add approval action

1. Select the **+** icon under the trigger step to add an action.

1. Enter `approval` in the search box.

    ![Screenshot of approvals search.](../media/search-approval.png)

1. Select **Start and wait for an approval** under **Standard approvals**.

1. Select **Create New**.

1. Select **Approve/Reject - First to respond** for **Approval Type**

1. Select **Start and wait for an approval** step name and enter `Approval`

1. Enter `/` into the **Title** field and select **Insert dynamic content**.

1. Select **Title** under **New Task**.

    ![Screenshot of dynamic content for SharePoint item.](../media/sharepoint-dynamic-content.png)

1. Enter your tenant user id for **Assigned To**.

1. Enter `/` into the **Details** field and select **Insert dynamic content**.

1. Select **Description**.

1. Enter `/` into the **Item Link** field and select **Insert dynamic content**.

1. Select **See More**, and then select **Link to item**.

    ![Screenshot of Approval action step.](../media/start-approval-action.png)

### Task 1.4 - Add condition

1. Select the **+** icon under the approval step and select **Add an action**.

1. Enter `condition` in search.

1. Select **Condition** under **Control**.

1. Enter `/` into the left **Choose a value** field and select **Insert dynamic content**.

    ![Screenshot of dynamic content for a condition.](../media/add-condition.png)

1. Select **Outcome**.

1. Select **is equal to** for **Operator**.

1. Select the right **Choose a value** field and enter `Approve`

    ![Screenshot of the condition.](../media/condition.png)

### Task 1.5 - Update status actions

1. Select the **+** icon under **True** and select **Add an action**.

1. Enter `update item` in search.

1. Select **Update item** under **SharePoint**.

1. Select **Update item** step name and enter `Set task to approved`

1. Select the **Power Automate SharePoint site**.

1. Select the **Tasks** list.

1. Enter `/` into the **Id** field and select **Insert dynamic content**.

1. Select **ID** from **New task**.

1. Select **Show all** next to **Advanced parameters**.

1. Enter `/` into the **Title** field and select **Insert dynamic content**.

1. Select **Title** from **New task**.

1. Select **Approved** for **Approval Status Value**.

1. Select the **+** icon under **False** and select **Add an action**.

1. Enter `update item` in search.

1. Select **Update item** under **SharePoint**.

1. Select **Update item 1** step name and enter `Set task to declined`.

1. Select the **Power Automate SharePoint site**.

1. Select the **Tasks** list.

1. Enter `/` into the **Id** field and select **Insert dynamic content**.

1. Select **ID** from **New task**.

1. Select **Show all**.

1. Enter `/` into the **Title** field and select **Insert dynamic content**.

1. Select **Title** from **New task**.

1. Select **Declined** for **Approval Status Value**.

1. Select **Save**.

1. Select the **<-** Back button from the top left of the command bar.

## Exercise 2 – Test approval

### Task 2.1 - Trigger approval flow

1. Navigate to the SharePoint site and select the **Tasks** list.

1. Select **+ Add new item** and enter the following data and select **Save**:

   1. Title=`Approval test`
   1. Description=`Test`
   1. Owner Name=`MOD Administrator`
   1. Deadline=**Today**
   1. Approval Status=**New**

### Task 2.2 - Progress approval

1. Navigate to the Power Automate portal `https://make.powerautomate.com`

1. Make sure you are in the **Dev One** environment.

1. Select the **My flows** tab from the left navigation menu.

1. Select **Task approval**.

1. Select the date and time in the flow run history.

1. Select the **Approvals** tab from the left navigation menu.

    ![Screenshot of approvals in the portal.](../media/approvals.png)

1. Select the **Approval test**, select the **Tick**, and select **Confirm**.

1. Select **Done**.

1. Select the **My flows** tab from the left navigation menu.

1. Select **Task approval**.

1. Select the date and time in the **28-day run history**.

1. Expand the condition step.

1. Navigate to the SharePoint site and select the **Tasks** list.

1. Verify that the **Approval status** of the **Approval test** item is **Approved**.
