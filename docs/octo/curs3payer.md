# CUR and S3 Bucket Setup for Payer Accounts

To pull your AWS data to Octo, there is a need to setup the CUR and S3 bucket for payer accounts.


## Two deployment ways when setting up the CUR and S3 bucket:

### Setup CloudFormation using default configuration.
The CUR export settings and the target S3 bucket will be deployed to us-east-1 region.

1. Select `Default configuration`.

2. Click `Open AWS Create Stack Page`.

3. Clicking the link above will take you to your CloudFormation console.

4. Please make sure that it is deployed on the default `us-east-1` region.

5. Once done, come back to Octo and click `Check and Confirm` to start the verification process.

 
### Setup target S3 bucket in a different region.
S3 bucket is setup on a desired region aside from us-east-1 region.

1. Select `Target S3 bucket in a different region`.

2. Under S3 Bucket, click `Open AWS Create Stack Page`.

3. Clicking the link above will take you to your CloudFormation console.

4. Under CUR, click `Open AWS Create Stack Page`.

5. Clicking the link above will take you to your CloudFormation console.

6. Set the `CurS3BucketOption` parameter to `USE_EXISTING`, then set your `CurS3BucketName` and `CurS3BucketRegion` accordingly.

7. Please make sure that it is deployed on the `us-east-1` region.

8. Once done, come back to this page and click `Check and Confirm` to start the verification process.