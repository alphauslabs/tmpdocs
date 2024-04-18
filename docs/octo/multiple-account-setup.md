# Multiple Account API Access Setup
Using CloudFormation StackSets, it is possible to deploy API access for all sub-accounts that the payer account sees in the same organization. This guide shows how to use this ability to onboard your accounts.

As each linked accounts are automatically created with Alphaus IAM role, these accounts are also automatically onboarded to Octo.

## Prerequisites

- User access to the payer account in your AWS Management Console
- User permissions to use StackSets in your AWS Management Console
- [Activate trusted access with AWS Organizations](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-orgs-activate-trusted-access.html)

Reference: [AWS CloudFormation StackSets and AWS Organizations](https://docs.aws.amazon.com/organizations/latest/userguide/services-that-can-integrate-cloudformation.html)

## Procedure

1. On the Octo app, you can register a new payer account or edit the existing payer account.

    - To register a new payer account, go to More -> Account Registration -> Register New Account -> Amazon Web Services.

    - To edit an existing payer account, go to More -> select payer -> Action -> Edit Setting.

2. Under Multiple Account API Access Setup, click Open AWS Launch Page.

3. Choose a Template

    - Scroll down to Prerequisite - Prepare Template and select Template is ready.
    - Under Specify template, ensure that Amazon S3 URL is selected and paste the Template URL from Step 4 into this field.
    - Click Next.
![Choose Template](https://lh3.googleusercontent.com/d/1mLNA8kB2PCAaHetABW46zlNrvzgW-FN_)

4. Specify StackSet details

    - Fill in StackSet name with your desired name.
    - Paste your InternalID and Principal into the relevant field under Parameters. You can check the details on the Octo app.
    - Click Next.
![Stackset Details](https://lh3.googleusercontent.com/d/1qWAcUESjeIhrmtEz8_WciHA2DfZlmUGv)

5. Configure StackSet options

    - Under Execution configuration, select either Inactive or Active.
    - Click Next.
![Stackset Options](https://lh3.googleusercontent.com/d/1lUQYndzbTXm1BIQsGgN1u0xzIgoYBm9O)

6. Set deployment options

    - Scroll down to Specify regions and input `us-east-1`.
    - Click Next.
![Deployment](https://lh3.googleusercontent.com/d/1_raixipmHnOqt-0BN4kDVHF8P-opfypp)
![Deployment next](https://lh3.googleusercontent.com/d/17Xp0RAzEbYh53PX9HSM-xoGIkh3u2YXF)

7. Review
    - Review your newly created StackSet and click Run.
    - Your new StackSet should appear within a few moments on the main StackSets page.
![Review](https://lh3.googleusercontent.com/d/1kgg274T6O_UbBsFTf35Vc7pzPz0kXuvi)

8. After successful stackset deployment, go back to Octo account registration page and click `Confirm`.