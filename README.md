
<a name="readme-top"></a>

[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->

<br />
<div align="center">
  <a href="https://swift-expense.onrender.com/">
    <img src="logo-black.svg" alt="Logo" width="80" height="80">
  </a>

<h3 align="center">Swift Expense</h3>

<p align="center">
    An awesome application to manage your employee's reimbursement requests
  </p>
</div>

<!-- TABLE OF CONTENTS -->

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#introcution">Introduction</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li><a href="#getting-started">Getting Started</a></li>
    <li><a href="#join-policies">Join Policies</a></li>
    <li><a href="#reports-dashboard">Reports Dashboard</a></li>
    <li><a href="#expense-reports">Creating your Expense Reports</a></li>
    <li><a href="#admin-zone">Admin Zone</a>
    <ul>
        <li><a href="#admin-manage-policies">Manage Policies</a></li>
        <li><a href="#admin-manage-users">Manage Users</a></li>
      </ul>
    </li>
  </ol>
</details>

<!-- INTRODUCTION -->
## Introcution

Swift Expense - providing solution to companies to manage employee reimbursement requests

Swift Expense Features:
- Simplicity:
   - Easily create & submit expense reports
   - Policy based expense system; for each site/location/event an exclusive policy can be set by System Admins
   - Track your reports and your subordinate employee reports using the reports dashboard
   - Simplify approval process by setting a default supervisor for each employee
- Flexibility:
   - Update supervisor per user level; or per report level
   - Create new policies and set up new expense categories
   - Quickly add users to policies using email / user management page / policy settings page
   - Update existing policies, including policy categories and currency. Swift Expense automatically handles updating the related affected reports !
   - Revoke & regrant policy access and delete users. Swift Expense automatically handles redirecting related reports based on their status; to ensure maintatining completness of the company's expense reports history
- Visibility & connectivity:
   - Full transparency using a report system logs 
   - Communication on a report level using a report chat logs

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

* [![Django](https://img.shields.io/badge/-Django-092E20.svg?logo=django&style=flat)](https://www.djangoproject.com/)
* ![Redux](https://img.shields.io/badge/redux-%23593d88.svg?style=for-the-badge&logo=redux&logoColor=white)
* ![Postgres](https://img.shields.io/badge/postgres-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

- [Visit Swift Expense](https://swift-expense.onrender.com/)
- Register / Log-in

Once you are registered, your default supervisor will be the Primary Admin.<br/>
Only System Admins can appoint you a different supervisor; which will be responsible for reviewing your expense reports.

- Visit "Account" tab to preview your account details:
   1. Profile<br/>
      - Update your personal information & email
      - Attach / Delete profile picture
      - Memory efficiency:
          * Deleting profile picture will remove image from server disk
          * Updating profile picture will remove old image from server disk
   2. Security
      Change password

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- JOIN POLICY -->
## Join Policies

If the System Admin has yet to grant you access to the wanted policy, **feel free** to send an access request for the desired policy in "Policies" tab, each access request will be forwarded to all System Admins' email (Each system admin can update his email address under "Account" tab) - System Admin can grant/reject access via the link received in their own email, once a system admin granted/rejected your request, the request url will expire and other systems admins cannot use the link anymore.

Once you are granted access to the desired policy, you will be able to create & submit reports under the aforementioned policy.

- All policies are set-up by System Admins
- System Admin will set & define the expense categories that you can use within the policy
- System Admin will set the local currency for each policy; this will guarantee maintaining currency unity among all report amounts that are under the same policy

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- REPORTS DASHBOARD -->
## Reports Dashboard

This Dashboard in "Reports" tab consolidates all your reports and your subordinate employees reports in one place.<br/>
You will have access to:
   1. Your own personal expense reports
   2. Other employee's reports that should be reviewed by you

You can filter the reports by:
   1. Date (From / To)
   2. Report Status Multi-Select (Closed, Open, Processing, Approved)
   3. Report owner username. Non-admin can filter **only** usernames of his subordinates or usernames that are owners of reports that should be reviewed by the aforementioned Non-admin user.
   4. Report's policy. Non-admin can filter policies that he has access to, or policies he has no access to **only** if he has subordinates who have submitted a report in that policy to the aforementioned Non-admin user.

You can use the search bar to search for a specific report name.

System Admins have access to all reports of the company in this dashboard.

Notes:
   * For the user's convenience, the filter preferences are saved in the session storage
   * Users can hide the filter section by clicking on `Hide Filters`
   * Users can reset their filter preferences by clicking on `Reset`

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CREATE REPORTS  -->
## Creating your Expense Reports

In the Reports Dashboard you can create a `New Report` (top-right corner):

- Provide report's name, Swift Expense prevents the same user from having reports with duplicate names
- Choose in which policy you would like to submit the report
<br/>Once a report is created, the current supervisor of the user will be set as the report supervisor

The new report will appear now in the Reports Dashboard with summarized data of the following columns:
| `Report ID` | `Report Name` | `Policy` | `From` | `Total` | `Status` | `Supervisor` | `Report Date` |
| ------------- | --------------- | ---------- | -------- | --------- | ---------- | -------------- | --------------- |
| Report's unique ID | Report name | Policy name | Report's owner | Report's total amounts converted to policy's currency | Report's status | Report's supervisor | Report created date |
<br/>
Once you click on a report, you will be forwarded to the report's page which includes:

1. Report Headline<br/>
   The headline will include the policy name, report name, current report status and total expenses amount<br/>
   Click on `Reports` to return to Reports Dashboard

2. `Report Details` button<br/>
   This button opens a pop-up which includes report details:
   | `From`              | `To`                     | `Report Name` | `Policy`                                       |
   | --------------------- | -------------------------- | --------------- | ------------------------------------------------ |
   | Owner of the report.<br/>(Cannot be updated) | Supervisor of the report.<br/>(Only System Admin has access to update this field to set a different supervisor of this report, update is allowed if report status is "Open" or "Processing") | Report name.<br/>(Can be updated by report owner / report supervisor / System Admin if Report status is "Open")   | The policy that the report was submitted under.<br/>(Can be updated to another policy if the report owner has access to the other policy, update can be made by report owner / report supervisor / System Admin if Report status is "Open", existing expenses will be moved to "Uncategorized" category and converted to the new policy's currency) |

   *Any change in report details will be logged in the report's system log box*

3. `New Expense` button (keyboard interactive)<br/>
   Add expenses to your report using the `New Expense` button - fill in the required fields in the pop-up:
   | `Merchant Name` | `Expense Date` | `Total` | `Expense Currency` | `Category` | `Description` | `Image attachment` |
   | ----------------- | ---------------- | --------- | -------------------- | ------------ | --------------- | -------------------- |
   
   *Image attachement is not mandatory*

   Expenses with currency that is different than the policy's currency will be converted to the policy's local currency at the exchange rate as published by the bank of Israel at the date of the expense.

   Expenses can be added by report owner / report supervisor / System Admin only if report status is "Open" (see more on report's status in note 7 below)

   *Added expenses will be logged in the report's system log box*

4. Expenses Table<br/>This table will display all expenses ordered by category name then by expense date<br/>
   You can enter & update each expense by clicking on the expense and updating the fields in the pop-up (keyboard interactive). Report owner / report supervisor / System Admin may update the expenses if the status of the report is "Open", allowed update actions:
   - Update Merchant name, Expense Date, Amount, Currency, Category, Description and invoice attachment<br/>
   Notes:
      * Updating the expense date will cause the expense to be converted again at the rate of the new expense date
      * The invoice can be detached, this will remove the invoice from the server desk
      * Attaching a new invoice will remove the old invoice from the server desk
      * The expense can be deleted
      * For convenience, the expense can be duplicated - this will create a similar expense with similar field values but without an invoice attachment

   *Any change in existing expenses merchant name / date / currency / amount will be logged in the report's system log box*

5. Chat Logs<br/>
   To improve connectivity between users in Swift Expense, each report has its own chat log where the report owner, report supervisor and System Admins can chat & communicate with each other on matters relating to the expense report<br/>
*Toggle off the chat log button to hide the chat box*

6. System Logs<br/>
   To ensure full visibility and transparent control process, **all changes** related to the report will be logged in system logs detailing the username repsonsible of the change and the change that was made, these logs include:
   1. Changing report name
   2. Switching report's policy
   3. Adding / Updating / Removing expenses from the report
   4. System Admin actions:
      - Report Settings - changing the supervisor of the report
      - Policy Settings 
         - Changing policy name
         - Changing policy's currency; if the report was affected (i.e. if there are already expenses in the report)
         - Sending a public message to all existing reports in a specific the policy
         - Updating/Removing policy's category; if the report already includes expenses categorized in this category
         - Removing the report owner's user from Swift Expense:
            - in case the report is in Approved status, to maintain approved expenses history; the report gets directed to Primary Admin ownership
            - If the report is not "Approved", the report gets deleted
         - Removing a user who is a supervisor in existing reports, in this case the report supervisor will be updated to the Primary Admin
         - Revoking user's policy access:
            - If the affected report is "Approved" or "Closed", the revoked user remains the owner of this report & the report's status remains "Approved" or "Closed", respectively. Supervisor / System Admin cannot cahnge the status of this report without regranting the report owner access again to the policy
            - If the affected report is "Open"/"Processing", the revoked user remains the owner of this report & the report status changes to "Closed". Supervisor / System Admin cannot change the status of this report without regranting the report owner access again to the policy
         - Regranting policy access to a user

   *Toggle off the system log button to hide the chat box*

7. Report Status & Action Buttons<br/>
   A report can have 4 different statuses: `Closed` `Open` `Processing` `Approved`

   Report status can change using the Action Buttons:
   | `Submit` | `Approve`  | `Send Back`      |`Call Back` |`Cancel Approval` | `Close`  | `Undo Close`     | `Delete`|
   | ------ | -------- | -------------------- |---------------|--------------- | -------- | ------------- | ----------- |
   | Report owner / Report Supervisor / System Admin can submit the report for approval, this will change the report status from "Open" to "Processing" | Report Supervisor / System Admin can approve the report, this will change the report status from "Processing" to "Approved" | Report Supervisor / System Admin can send back the report, this will change the report status from "Processing" to "Open" | Report Owner can call back the report, this will change the report status from "Processing" to "Open" | Report Supervisor / System Admin can unapprove the report, this will change the report status from "Approved" to "Open" |Report Supervisor / System Admin can close the report, this will change the report status from "Open" to "Closed" | Report Supervisor / System Admin can re-open the report, this will change the report status from "Closed" to "Open" | if report status is "Open", report owner can remove the report. System Admin can remove the report if report status is "Closed" |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ADMIN ZONE -->
## Admin Zone

### Manage Policies

In "Policies" tab System Admin can create new policies using the `New Policy` button, clicking the button will open a pop-up (keyboard interactive):
- Policy names must be unique, Swift Expense prevents having policies with duplicate names
- A base currency must be chosen
<br/>All policies are displayed in the "Policies" main page, including a summarized data of total amounts Approved/Processing/Open/Closed per policy.

Entering a policy will direct you to the policy's page:

1. Headline:
- Clicking `Policies` will take you back to Policies main page
- Clicking the `policy name - currency` will open a pop-up that allows you to update policy name and policy currency, note:
   - Updating the policy's currency will convert the affected report amounts and the total Approved/Processing/Open/Closed amounts per policy
   - System log will record any change made to the policy that affects the related reports

2. Mini Sidebar
- `Categories`:<br/>
   In the categories page System Admin can:
   - set up new expense categories by clicking the `+` button and creating new category in the pop-up (keyboard interactive)
   - Update/Remove existing categories (keyboard interactive)
      <br/>Limitations:
      - Swift Expense prevents having categories with duplicate names within the same policy
      - Each policy must have a minimum of one default category which is called "uncategorized", Swift Expense prevents removing this category
      - Uncategorized category should be used by users when they are unsure under which category they need to categorize their expense
      - Uncategorized category will serve to handle deleting categories that are currently in use in expense reports; if the System Admin removes a category that is currently being used, the expenses will be directed from the removed category to the "Uncategorized" category and a proper system log will record this change in the affected reports
      - Uncategorized category will serve to receive all expenses in a report if the report's policy was switched to a different policy, a proper system log will record this change
- `Users`:<br/>
   **This users page is used to manage users on a policy level**<br/>
   System Admin can use the search bar to search for a specific username and grant/revoke access to the policy

<a name="manage-users"></a>

### Manage Users

**This users page is used to manage all users in Swift Expense**<br/>
System Admin can search for and enter any user in Swift Expense, clicking any user will open a pop-up detailing:

1. user basic information: username, first name, last name and email
2. A multi-select bar showing the policies that user hass access to, System Admin can use this bar to easily bulk update accesses to many policies at once. System Admins have access to all policies so this bar is not available when reviewing a user that is also a system admin
3. Supervisor - System Admin can set the default supervisor of the user, creating future reports will be reviewed by this supervisor. All system admin's supervisor are set to the primary admin, this cannot be changed hence is not available when reviewing a user that is also a system admin
4. Reset password - Primary admin can reset any user's password, Secondary admin can all other users's passwords except for Primary admin. Each user can change his own password under Account tab in the side navigation bar.
5. System Admin can remove any user<br/>
   - To maintain completness and clarity, expense reports that are in status "Approved" will be redircted to the the Primary Admin as the new owner, the report name will be updated to include a documentation of the original deleted owner and the system log will document this change in the log-box<br/>
   - If the deleted user serves as supervisor of other users and reports, supervisor duty will be directed to Primary Admin and a proper system log will record this change in the affected reports
   - To save memory desk, profile images of deleted users gets deleted from server's desk
6. Primary admin can grant/revoke secondary admin permission to users, note - revoking secondary admin from user will revoke his access to all policies, use the Manage users / Manage policies tab to update the user access to policies as needed.
<p align="right">(<a href="#readme-top">back to top</a>)</p>

[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/jalil-zoabi-cpa-67749a14a/