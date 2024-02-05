# Account Registration
Octo's cost and usage data rely on the registered cloud service provider's account. In the account page, CSP's accounts are registered, listed, updated and deleted.

![Account Registration](https://lh3.googleusercontent.com/drive-viewer/AEYmBYTLM5YNrA_zbqxqIVvZ1tjs4wZB-MERQiUAI7sKPqxWAuHBChlD3YnxMAbbQMlEBZAM8JPvZaYmQqU6ja1UNMIjYDlcpg=s1600)

## Registering an account
Account registration enables the user to register the source of data in Octo. As of now, Octo supports AWS, Azure and GCP vendors. This is only accessible to admin users.

After successful account registration, it will take up to a day for Octo to retrieve the data from your CSP account for them to be displayed in Octo.


=== "AWS"
    ![AWS Account Registration](https://lh3.googleusercontent.com/drive-viewer/AEYmBYT1LhwmtZZBayUETNbqFOowbNMytIljtocEpHFZGeBqZf1mElpOV9Xwl4zMbKZxdTRudRMcS7vKlkLJUNmSjiTTUBl8yg=s2560)
    
    The following are the steps for AWS account registration:
    
    1. Register AWS ID and Name.
        - This is the start of the account registration. Please input the 12-digit AWS account number. For the account name, this is optional. You can set any name for easy management of the accounts.
    
    2. Setup API access.
        - Setting up the API access, let's Octo pull some data from your AWS account through API access. 

        a. Click the "Open AWS launch page" button. The AWS launch page will open in a new tab. Enter the required information and launch. This will open a cloudformation template for deployment into your AWS account. Required details for the deployment are already pre-filled.

        b. After launching, please return to the account registration page and press the "Confirm" button. Once everything is successful, status of the API access is set to `Completed`.
    
    3. [Setup CUR and S3 Bucket](https://labs.alphaus.cloud/docs/octo/curs3payer/) (for payer accounts only).
    
    4. Setup Payer Account (for linked accounts only).
        - For linked accounts, you have to specify the payer account. There is no need to do this on payer accounts.


=== "Microsoft Azure"

=== "Google Cloud"

## Account List
![Account List](https://lh3.googleusercontent.com/drive-viewer/AEYmBYT1IPm3XU8t6urabmxI792E76HsWDIo-lM8mXELdxwAsAtKrRGRKiBNFIz2fvqYbFRV4BKg-iLccEGBB4_S5VFyBR6Ilg=s1600)
All registered accounts are displayed on the account page with the status of the account registration.

`API` - API access is established. Applicable to Payer and Linked accounts.

`PAYER` - Payer account is set on the linked account. This is only applicable to linked accounts since payer accounts automatically sets itself as the payer account.

`CUR` - CUR and S3 bucket setup is successfuly setup. Applicable to payer accounts only.

## Edit Account Details
```
Available to AWS for now
```
If there are changes on the setup of your CSP account, Octo provides a setting to update the details. 

### Edit Account Name
Account names can be changed any time. These are used to easily manage the accounts. 
![Edit Account Details](https://lh3.googleusercontent.com/drive-viewer/AEYmBYS6b3Vvxi-u6M4Dv5cnLL_9pYU9VGz-NnDrDoOvnZG3gTsxEYHl1nAUDxvZHbrXz4Y4-5yuSW-qaLQCTzzl_7NvfqFLVw=s1600)

### Edit Setting
Edit setting enables the user to update the account settings. 

For linked accounts, API access and payer setting can be done.

For payer accounts, API access and setting up the CUR and S3 bucket are applicable.

## Delete Account
Delete account removes the account from our database.