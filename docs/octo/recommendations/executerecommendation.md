# Execute Recommendation

In addition to providing users with recommendations for optimizing their cloud costs, Octo enables users to execute or apply these recommendations directly within its interface. This streamlined approach empowers users to take immediate action on cost-saving suggestions, enhancing efficiency and simplifying the management of AWS resources. By integrating actionable insights and execution capabilities, Octo ensures a seamless experience for users, facilitating quicker responses to optimize their cloud expenditure.

As of now, Octo support executing recommendations exclusively for AWS, with plans to expand this functionality to include GCP and Azure in the future.

## Amazon Web Services Recommendations

Octo leverages AWS Change Manager, a feature within AWS Systems Manager, to handle the execution of recommendations. AWS Change Manager provides a structured and secure way to implement changes by requiring user approval before execution. This process ensures that all actions are reviewed and authorized, reducing the risk of unintended changes and maintaining compliance with organizational policies.

By integrating AWS Change Manager, Octo automates the implementation of cost-saving recommendations while incorporating a critical layer of governance. This enables organizations to act on recommendations efficiently while adhering to best practices and approval workflows.

### Prerequisite
1. Ensure that the AWS account linked to the recommendation has already set up API access, as Octo requires specific permissions to perform the execution.

### Key elements in execution

1. <b>Change template</b> - A predefined framework that specifies the steps, approval workflows, and permissions required for executing a change. Octo automatically creates a change template for each recommendation, ensuring that the execution process aligns with the specifics of the recommendation and its associated region. If a change template for the same recommendation and region already exists, Octo reuses the existing template to avoid duplication and maintain consistency across executions.

2. <b>Change request</b> - A specific request created based on a change template to execute a particular recommendation. Each recommendation has its own unique change request, which captures the details of the intended action, tracks the approval process, and logs the status and results of the execution. Change requests act as a traceable record for managing and auditing the implementation of recommendations.

3. <b>Assume role</b> - Octo programmatically assigns the `OctoChangeTemplateApproverRole` as the designated approver for the change template. This role is specifically designed for the AWS account and can only be assumed by the AWS account to approve the change template. Octo itself cannot assume this role, ensuring that the approval process remains secure and under the control of the account owner. By using this role, the AWS account gains the necessary permissions to review and approve the change template, maintaining the integrity and security of the process while adhering to AWS's role-based access control best practices.

### Execution Statuses

The execution statuses provide a clear overview of the current state of a recommendation's lifecycle. These statuses help users track the progress from availability through approval, execution, and potential errors. Users are encouraged to monitor these statuses closely to ensure timely execution and to address any issues promptly, particularly when encountering execution errors.

| Execution Status   | Description                                                                 |
| ------------------ | --------------------------------------------------------------------------- |
| :octicons-check-circle-fill-24:{ .available-recommendation } `Available`   | The recommendation is available for review and action. It has been identified but has not yet progressed further.                                        |
| :material-alert:{ .pending-recommendation } `Pending approval` | The change template associated with the recommendation is awaiting user approval. Execution cannot proceed until the template is approved. |
| :octicons-check-circle-fill-24:{ .approved-recommendation } `Approved`         | The change template has been approved by the user, and the recommendation is ready to be executed as per the defined steps.        |
| :material-sync:{ .executing-recommendation } `Executing`        | The recommendation is actively being implemented. This status indicates that the execution process is in progress.               |
| :material-alert:{ .executionerror-recommendation } `Execution error`  | An error occurred during the execution process. Users can review the error details and retry execution after addressing the issue.  |

### How to execute recommendation in Octo?

#### 1. Create and Approving change templates
Select the recommendation to execute. For recommendations with the status `Available`, a change template will be created first. To do so, click the three vertical dots.

![](https://lh3.google.com/u/0/d/1VOc8ZFZr_6GsnvybIrJ1xVkqwAV0fvVg=w1920-h927-iv1)

Alternatively, user can click the recommendation to view its details. 

![](https://lh3.google.com/u/0/d/1S4ZYGJfuOGInqTIRVByrodakxa7tQWJj=w1920-h927-iv1)

Then, click the `Approve Change Template` button. An Approve Change Template modal will appear.

![](https://lh3.google.com/u/0/d/1MRNNMhVL5QjgOR5BYrHVY0MOXv_Dteyi=w1920-h927-iv2)

!!! note
    Octo utilizes the Assume Role mechanism to manage the approval of change templates. During account registration, Octo creates an IAM role called OctoChangeTemplateApproverRole to facilitate the approval process. Only the associated AWS account is authorized to assume this role, ensuring that Octo itself cannot assume it. This ensures the approval process remains secure and is controlled exclusively by the AWS account.

Click the `Open Switch Role Link` to proceed. Once clicked, there will be a brief loading period as Octo creates the change template. After the loading finishes, users will be redirected to the AWS Switch Role page. Octo will automatically populate the necessary fields, allowing users to simply click the "Switch Role" button to complete the process.

![](https://lh3.google.com/u/0/d/10RwKxY62gp8uvzKGGbJ16zaZ5-ZGRZTi=w1920-h927-iv1)

After clicking "Switch Role," the user will be redirected to the details page of the created change template, as shown below. This page provides detailed information about the change template, including its purpose and specifics. If the user decides to approve the template, they can do so by clicking the "Approve" button located in the upper-right corner of the page.

![](https://lh3.google.com/u/0/d/1OIY7aPR67-yD1h4GXntlAHo8FseJkou1=w1920-h927-iv1)

A modal again will be displayed to confirm the approval. Users can put some comments about the template. However, octo doesn't record this data so users can leave it as blank. Then click `Approve`

![](https://lh3.google.com/u/0/d/1ffvtSU77-WPsms10H837PfyaFszAC-Rp=w1920-h927-iv1)

#### 2. Execute Recommendation

After following the instructions in the Step 1, user must go back to octo.

!!! note 
    Octo delays updating the recommendation status to `approved` as it relies on a cron job that processes approved templates in bulk at scheduled intervals, ensuring efficient handling of multiple updates.

!!! info "Here’s how Octo manages or updates recommendation statuses through Cron tasks"
    As part of the beta testing, the following interval is used for updating statuses. Octo plans to modify this in the future.<br><br>
    1. Every 6 hours, Octo verifies if any change templates have received approval.<br>
    2. At 30-minute intervals within each 6-hour period, Octo creates Change Requests for Recommendations that have approved change templates. After the Change Request is generated, the recommendation status is updated to `Approved`"

After a while, the status of the recommendation has changed to "Approved."

!!! note 
    Recommendations with the same combinations, such as stopping an EC2 instance in account ID 123456789012 and region ap-northeast-1, will also have their status updated to `approved`. As mentioned in the key elements, change templates can be shared across these combinations.

![](https://lh3.google.com/u/0/d/17YqBfHn9FvZ33tcn9BEehAtQ-Bg0Dxiu=w1920-h927-iv1)

To execute, click the 3 vertical dots or open the recommendation details modal and select `Execute recommendation`

![](https://lh3.google.com/u/0/d/1IeodRCimI94eJ1-z8Iwkex2rJXCa6yii=w1920-h927-iv1)

Type `execute` and click `Execute`

![](https://lh3.google.com/u/0/d/1qnUnXTv7KS6YZRESMUokNRzpdSM8x8H_=w1920-h927-iv2)

![](https://lh3.google.com/u/0/d/1S-xTqelx6ROOw7vKmxJjPjr3hfVkp4yw=w1920-h927-iv1)

### What happens after the execution?
#### Successful Execution
If the execution is successful, the recommendation will be moved to the Optimization History. This ensures completed recommendations are properly archived, allowing users to track past optimizations and assess their impact over time. The Optimization History provides a consolidated view of all successfully executed recommendations, making it easier to review and analyze previous actions.

![](https://lh3.google.com/u/0/d/1JIzjwAAC9irD-aNx9JDMdfO_n1SX3gvw=w1920-h927-iv1)

#### Execution error
If an error occurs during execution, the status will update to `Execution Error`. Users can troubleshoot the issue by opening the recommendation's details modal, which provides a comprehensive error message. This message explains the nature of the error and helps users diagnose the root cause.

![](https://lh3.google.com/u/0/d/13tCXXTmKaBYUGNpwhNHemr7hffKBZNnt=w1920-h927-iv1)

![](https://lh3.google.com/u/0/d/1xYH1al45oDla_8z29MXVDSf1D4kwqY6U=w1920-h927-iv1)

### Re-try execution
Octo also allows users to retry execution only when the state is marked as an `Execution error`. This feature provides an easy way to handle failures and ensure tasks are completed successfully. To retry, click the three vertical dots or open the recommendation details modal and click `Re-try execution` This action will trigger a new attempt, allowing users to resolve any issues without needing to manually reconfigure the recommendation.

![](https://lh3.google.com/u/0/d/10R0-6Q_ofKyNahD_qzZY1vCu_NtWTmme=w1920-h927-iv1)

Once the error is resolved and the execution is retried successfully, the recommendation will be moved to the Optimization History, ensuring it is tracked and recorded for future reference.

### Current recommendations that support execution

Currently, Octo supports the following recommendations below. More recommendations will be supported in the future.

??? note "Current recommendations that support execution"
    | Recommendation                                    | Source                  | Category |
    | ------------------------------------------------- | ------------------------| -------- |
    |  Stop EC2 instance                                | Cost Optimization Hub   | Stop     |
    |  Stop RDS DB instance                             | Cost Optimization Hub   | Stop     |
    |  Low Utilization instance Amazon EC2 Instances    | Trusted Advisor         | Stop     |
    |  Rightsize EC2 instance                           | Cost Explorer           | Rightsize|
    |  Rightsize RDS DB instance                        | Cost Optimization Hub   | Rightsize|
    |  Rightsize ECS service                            | Cost Optimization Hub   | Rightsize|
    |  Rightsize Lambda function                        | Cost Optimization Hub   | Rightsize|
    |  Rightsize EC2 Auto Scaling group                 | Cost Optimization Hub   | Rightsize|
