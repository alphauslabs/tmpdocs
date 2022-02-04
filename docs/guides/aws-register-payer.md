# Registering AWS payer accounts using bluectl

!!! note
    This guide is only applicable to Ripple users.

Make sure to install [`bluectl`](https://alphauslabs.github.io/docs/blueapi/bluectl/) first. Also make sure that you have the needed permissions to deploy [CloudFormation](https://aws.amazon.com/cloudformation/) templates on the payer account. The template used in this guide will setup a new [CUR](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html) export definition to an S3 bucket. It will also create an IAM Role with read access to the target bucket alongside read-only API access to the payer's cost details. You can check out the actual template [here](https://alphaus-cloudformation-templates.s3.ap-northeast-1.amazonaws.com/alphauscurexportdef-v1.yml).

Open a terminal and run the following command (`131920598436` here is a sample payer account):

```sh
$ bluectl xacct create 131920598436
Open the link below in your browser and deploy:
https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/...
Confirm successful deployment? [Y/n]: 
```

Click on the URL link, or it copy to your browser. It will open the CloudFormation console with the parameters filled up. Check the "acknowledge" checkbox, and click "Create stack".

Once the deployment is done and successful, return to the terminal above and press Enter (`Y` is the default option). The deployment validation will begin. If no issues encountered, registration details are returned and the process is completed.
