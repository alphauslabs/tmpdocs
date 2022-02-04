# Registering AWS payer accounts using bluectl

!!! note
    This guide is only applicable to Ripple users.

Make sure to install [`bluectl`](https://alphauslabs.github.io/docs/blueapi/bluectl/) first. Also make sure that you have access to deploy [CloudFormation](https://aws.amazon.com/cloudformation/) templates on the payer account. The template used in this guide will setup a new [CUR](https://docs.aws.amazon.com/cur/latest/userguide/what-is-cur.html) export definition to an S3 bucket. It will also create an IAM Role with read access to that target bucket alongside read-only API access to the payer's cost details. You can check out the actual template [here](https://alphaus-cloudformation-templates.s3.ap-northeast-1.amazonaws.com/alphauscurexportdef-v1.yml).

TBD
