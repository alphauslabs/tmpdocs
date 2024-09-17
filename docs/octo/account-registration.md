# Account Registration
Octo's cost and usage data rely on the registered cloud service provider's account. In the account page, CSP's accounts are registered, listed, updated and deleted.

![Account Registration](https://lh3.googleusercontent.com/d/1E5-S2QGRbpABwhwEA3N4kKClCTgTbmLY)

## Registering an account
Account registration enables the user to register the source of data in Octo. As of now, Octo supports AWS, Azure and GCP vendors. This is only accessible to admin users.

After successful account registration, it will take up to a day for Octo to retrieve the data from your CSP account for them to be displayed in Octo.


=== "AWS"
    Currently we have 2 steps in registering AWS account in Octo. First is through AWS console, which requires you to sign-in to you account and involves deploying stacks or stackset in your AWS account. Second option is using Terraform module, you can use our  terraform module to deploy the necessary resources in your AWS account. 
   
    **Via AWS Console**

    1. **Select Registration Method.** Choose Connect via AWS Console.
    
    
    2. **Basic Details.** This step will save your account's Id and name if provided.
    
        a. Input your AWS Account Id (12 digits).

        b. Input Account Name (Optional).

        c. Click Register Account.

        d. If there is no error, then click Next.
      

    3. **Setup API Access.** In this step it will deploy a stack in your AWS account, this will setup needed permission to allow Octo to perfome API Operation in your account.

        a. Click Open AWS create stack page. This will bring you create stack page in your currently signed-in AWS account, make sure you deploy the stack in your intended account, default region would be `us-east-1`.

        b. Please check default values when creating stack:

        - Stack name (You can retain the value or input your desired stack name.)

        - ExternalId (Do not change.)

        - Principal (Do not change.)

        c. Tick the checkbox to agree the I acknowledge that AWS CloudFormation might create IAM resources with custom names. message.

        d. After checking the stack details, click Create stack button. If create stack is success, go back to Octo.

        e. Click Check and Confirm to verify the deployment.

        f. If verification is success, it would check whether your account is a linked or payer account. If it is linked, you can click the Confirm and Finish button to finish the registration. If payer then click next to proceed with additional steps for payer accounts.
        
    
    4. **Setup Multiple API Access - Optional** (Payer Only). This step will use stackset to deploy API Access in all linked accounts under the payer account. This is useful if your organization have many linked accounts that you want to register to Octo.

        a. Click Open AWS create stackset page. This will bring you to create stackset page in your currently signed-in AWS account, make sure you deploy the stackset in your intended account.
 
        b. In the create stackset page, follow this guide: [Setup multiple account API Access using stackset](https://labs.alphaus.cloud/docs/octo/multiple-account-setup/)

        c. Click check and confirm. This will verify you stackset deployment.

        d. If success, you can click Next.

    5. **Setup CUR and S3 bucket** (Payer Only). This will deploy stacks for setting up CUR definition in your account, it will also setup a bucket to store your CUR data. You can choose whether to proceed with the default configuration or target S3 bucket in a different region. Another guide can be found [here](https://labs.alphaus.cloud/docs/octo/curs3payer/)

        a. Click AWS create stack page. This will bring you create stack page in your currently signed-in AWS account, make sure you deploy the stack in your intended account.

        b. Click check and confirm. This will verify you stack deployments.

        d. If success, you can click Confirm and finish.

    **Via Terraform**
    
    Note: You must have terraform installed in your local machine to proceed. You can follow this [guide](https://www.terraform.io/downloads.html).
    (Optional) If you prefer to use AWS CLI for authenticating your AWS account, you can follow this [guide](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).

    1. **Select Registration Methodd.** Click Via other options, choose terraform.
    
    2. **Basic Details.** This step will save your account's Id and name if provided.
    
        a. Input your AWS Account Id (12 digit).

        b. Input Account Name (Optional).

        c. Click Register Account.

        d. If there is no error, then click Next.

    3. Check this [terraform module](https://registry.terraform.io/modules/alphauslabs/octo/aws/latest), from there you can read it's README section for more detailed information about the module and the required inputs.

    4. Run **terraform init** to initialize the module, **terraform plan** to check what resorces will be created, and **terraform apply** to create those resources.  

    5. After running those commands above, check if the deployments are successful, if so, click **Check and confirm** to verify. You can also check your AWS account to see if the resources are properly created.

    6. On Octo, you can see the status of the deployments for API Access, CUR and S3 bucket (Payer account only), and multiple account API access - optional (Payer account only).

    7. If API Access is success, you can click **Confirm and Finish**.

    For Payer accounts, if it's registered without using stackset, you can still enable it by doing the steps above, just make sure you set the **use_stackset** to true in the terraform module, it will update the resources and automatically register all your linked account to Octo, there is no need to delete your payer account and register again.



=== "Microsoft Azure"  

    Registering Azure CSP Payer Account involves 3 steps, Basic Details, Partner Center Credentials, and Partner API Credentials.

    Note: You can only register one payer account as of now.

    1. **Basic Details**

        a. Input your preferred acount name (Optional).

        b. Click Next.

    2. **Partner Center Credentials**

        a. Input your Client ID, Application ID, and Secret key to procceed.

        b. Click Register Credentials. This will verify your input credentials.

        c. If success, you can now click Next.

    3. **Partner API Credentials**

        a. On this step, you can verify your MPN ID, Directory (Tenant ID), and Application ID. 

        b. Input your secret key.

        c. Click register credentials. This will open a new tab on which you will require to sign-in in to your account. The goal of this step is to obtain an authorization code which is needed on the next input.

        d. Input the code.

        e. Click confirm and register.

    

=== "Google Cloud"   

    To register your billing account in Octo, you must follow these steps.
    
    1. **Basic details**

        a. Input your preferred name for your billing account (Optional).

    2. **Export billing data to BigQuery**

        a. Follow the instructions, you can also read this [guide](https://labs.alphaus.cloud/docs/octo/account-registration-gcpbigquery/#export-billing-data-to-bigquery) for more detailed steps.

    3. **Add BigQuery permission**

        a. Follow the instructions, you can also read this [guide](https://labs.alphaus.cloud/docs/octo/account-registration-gcpbigquery/#add-bigquery-permission) for more detailed steps.

    4. **Register Billing Account**

        a. Input your billing account ID.

        b. Input your project ID (This is where you dataset is hosted).

        c. Input BigQuery dataset name.

        d. Input BigQuery dataset region.

        e. Click confirm and register.

## Account List

All registered accounts are displayed on the account page with the status of the account registration and their account type. To see account list, click `More` on the sidebar and select `Account Registration`.

Different account status are (Applicable to AWS accounts only):

`API` - API access is established. Applicable to Payer and Linked accounts.

`PAYER` - Payer account is set on the linked account. This is only applicable to linked accounts since payer accounts automatically sets itself as the payer account.

`CUR` - CUR and S3 bucket setup is successfuly setup. Applicable to payer accounts only.

`STACKSET` - Stackset for multiple accounts api access is successfully setup. Applicable to payer accounts only.

## Edit Settings

You can choose to edit you CSP account by clicking the account you want to edit and on the right side click the Kebab menu icon and select `Edit Settings`.

1. In the basic details section, you can only update the account name.

2. Next steps are specific on what CSP account vendor you are trying to edit. It is similar process on registering an account.



## Delete Account
Delete account removes the account from our database. To delete an account, click the account you want to delete and on the right side click the Kebab menu icon and select `Delete Account`