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

    4. Run **terraform init**, this initializes a working directory containing Terraform configuration files, **terraform plan** to check what resources will be created, and **terraform apply** to create those resources. You can also check [here](https://developer.hashicorp.com/terraform/cli) for more information about the Terraform CLI.
    5. After running those commands above, check if the deployments are successful, if so, click **Check and confirm** to verify. You can also check in your AWS account console to see if the resources are properly created.

    6. On Octo, you can see the status of the deployments for API Access, CUR and S3 bucket (For payer account only), and multiple account API access - optional (For payer account only).

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
        ??? info "Click to view image"
            ![billing](https://lh3.googleusercontent.com/fife/ALs6j_H1WpOJipisOMznEY9mL2TQyppGwFLDzfBB-Rb5Cz3e5hFUbdAPiMd9XMchjAON0XxY4UMxJWFMX0l0vlRAHd5T7WyFEAzsB9SvcSVMORkJw_Q4WM-WiVtf3xdTOeMU00m8k9U0JcAnEyuuCPbnUMZV0a8WUQtW3TlcYLauRulgW4I24ugZg9io-G4Pg_SS4QuyO1pAQRsFHyag6cDpVDHKCBsjd4YEJkqt6R3CzqeA0-K1RbVWcE0GNCIyhhwIJu3cxxjVZKDAyMoJlAnpF66JFMKBkIweBVBjOWV1rq6GwQR2H3saemtZsohGb4F1kuWRO0XdolWn-qHiZQRgsQLcUTE1n8TRdckP4PQ7viMnj4l4sxB5Vl0mobx6m_1SXFqLsymgDxqQ629h_W9Vbn8w7iOGT-Kc4r3FGm0jANb89fKdh8uEuSMB0Ihzzp6IQSWMc4W1lvkBnz4k_f6xgEJCCdNMVyWlTN3NQFlSGzVul7YDlXLS3bZ0w_oztX5mzZqeLiOodnq85QQacICa0-d2MK9Vpu0ps7PQMYiEuafueH4y1FqFo0JW8u7B1v6oGtLTIh9-q6kR4t-HqoJQeqhV1ZNYbZbMRF0h8CMG_TpobNY7DWhzmAm0bi1h-GdvMTmdOZlLWjOICrC28EJR3uAOLxLOBKx95JIFMHr2JSz_7OAgpUv7PSa-aZRBDo4sge1RRJvX3VlvK-b7TmwaTGPmNdTRlOtFc66sYU7fUrf7sNVtybJagHO_33HPu3ONj2hg9ej4MwzfF-vykLbZc0dEEqSmHyLhhTR0lCy04FuD3dk0GKa6U8vF3OGKeYAKU9RGZOgUHUXPYbz04X-iojPUV_GoH2VbEPrTEKNaANL684U5lIYf9l5oot2vnYrqWRo2yvTbVHC39iI0kX-SUiJXfODfHsW6A1v2YVOD38dis5ecHG4S_BKb9jClvYvZDBeAoIhkuWVWGt391WQHNh5X3Q3vTqIR8vFgqvjXigAlR5jPdVSFgxrrjYNuYD_9vQRBvcE6X7hPYzzPWccn17yAUb5Z3eESa-CoFdDN0U5Vu0N2v9zH50pOmpf41y7qSubcsIeXXvPO2yNGrDZEmGmzGZR-EhVd8_I8v0xqbmDjXDD3chVkX4ZPWTYm22IzEmAcP-5DWnLbAo_u3Q65H7awo1kMOlGb10LcGar_330mTQXpRassYix4qc-p57r3B3Cm9Ji3TTmWz4Ns5NrJu7kWSriv_vnTuh1DkjsIxhGNbgJmTh9mbjfS8zRp_o_4yqovB68nQZkMfzsE0ZrFL3Z3E-5KLL0ZEBY5hvpvxceKrOikA7a4BYoGskIqFGo1jaC8wRI9RLypWdMtHGWlADNEqrmvWF_WJ9E9xzDZuwBd-6ogqlxnRRT32nAOmprlYVkIemkHy8xJxtSjW-brsgs9NBoOlXalPQs_fSFegEtlSqzNZKzVJ56x_z957BSkaLdVLpfjSdWNGnLk8OrjgMxWHAEifnJGENgUdOxZ4CV0RvuaJhRSx-WUL3L4_9P4YlWmvGVBeUU1NeyRntM7Lc-n9AvEtMGuj02JEg2pHLptNAojXIq-fnh9OoTdbJzVkXgJ3wBPwd7fxnP-xO-TuMcwsn-SSUO89xXOapKHBIZG92boXttTsL8UZJ1coMDiCcLE_z0zNsIp2pTSFgGH_JOLoZe_Oett1idUvIXJJCleo1zYta5BHCkO1mwlAA=w1509-h769)

        b. Input your project ID (This is where you dataset is hosted).

        c. Input BigQuery dataset name.

        d. Input BigQuery dataset region.
        ??? info "Click to view image"
            ![billing](https://lh3.googleusercontent.com/fife/ALs6j_H28foXRu-CGtTQ2E1lpTvakY4AuocDj7whb9RZQtmz37t7XJl3vwZv-YiXtDyNrRLHB0PqQ-VmbJxvL1ljY8VWw_x5gYdV6ne8vUUMNMOWUM1dcl4wSztgbXnDtY3ukzUUPPcW9NJ0VJ1IOjMV5x9sMOhopHQu_3P5S57ogIprhoDlBfEWonGuLlG4WdjxBKdA-ywcSk-QbLDN9C1qwZKTVVaEr2tKIoJ6BWPUB-Hq7EawpQXecPboGWeoK0MTToGdfqy_BRkdE6g53VF_GAK6nuptq1vAB3fDO5jqQYiXsGwSJ7CXwX_0bOQnfwIGAYmjdc39E2OqDtnxthiU1Eq6B1y3d-ubGnLgl9wIDuF7DWAH2I19pRBR006Mu2lSFa7XII0wKtQX__QdyMPlVlp0-AeZ2HWkIXXJdsPeM8y3mq7JApaO3r-oIWYk_9074UHM6uSIrxsgrHKNvd8ZnmIiGd9LYds25B5m7DezbPsV-fK-LzitF7kaK0SkmFpTjkc3vMhsfm-owSetrFFstE4EdCC4si-bFjZNj-qLBQ_Uc3kOKY6-sJIYN7T9CsQi5323Y0J2FFhLU5JcCHKKqoeyPD1bbAmdNHlawOqJPQhsFqWURZ3RDaDU-hRJhjDSvoPPmir0ux1UyytttXtNauAR9PU_r61ddPD-MdzyEoRRBtw88CN1uz5ZPuMSklktQSUd3LX74DDEGnXVUq7EsQpsfhx-VnRAxf9BHxItymsukWRRZ8K-XPJxFjd8zUy3L-S6T5jlX3iI_95_yMdjlenEt5RSKBSlNqUYfmTpfitD1DMUt8F6JLanr96r80HLZMvV_2TKS3NWdCgSF9bVa0bApNsvs44AmYvKU98X-g_R24alGuh_ITVP5ulmzJD6eO1s6rwTeuieSWgefvDw9gsi5ndDZnXj-vgMtzPtKu1ySVmMiuax06Ag-EubyLira4IUTeY008aOB4xCWtW4CEQ8sOgD0c5vFX0am_Vq8FcF5FOupjfsw6NXmCvY62YlBtxcowjnBjzHfAf3b_GFcbbisi98Rp8rXwqRcJOggZalRjH06P1ksodnILqtnK2-qzRFeewdlpB2xZNU_qLVqyCVTwfZ_C1NwZRuwX5lwcJAC7vN7XuisrAohIJkaYFyrI9OCaSYT2Sz4WVlNawSOB6TQql9EU9B0aTWUw3gA3JMb3VVdqsKPU_NsHtfgp3ul0kvTNCZ6VQKMjCMPF-QhKAmQnU1PxUXZBVps3ggdnjb5v-qN4xmENanRWP_LCHs1ZWONxoBfvLOnU9dud3axugh6ckRsHqHCa66EDTZGK1VmIGKi70tkIYOEOuufJdaRS2tprv0CavehsmtkJhEjNK9fXvk_3pvA02cPG9JLI70ChsM_Q7IiKA95679kPTaEvZW35sU_vNXXl8jSYh-e4XPuEB5drGQKvZZkyNZM9vBP0YKAe0Rk937coYm_lPqYFkL-EK1nt4PPSmwo2llU0dse7f-6wZGBnF9v38rvW5OIXOLecZEHTb9V7TkjYRYrZuBl55F92pLuvjXSzYpVcPoySDEKUstmBehIRgCCSvUIYneorUopq0f76yroP17RPyRKtr9AS5A0Zp8LiVgoIqzzxyEek05K5t7Cih2NQH6LvnJFpP8Mxm7wydCjny3jIEUyLjtbn8WoOVqmtPfcEoT1OBDCxwt6lft6qwZAC95HQKLQk10X9Ttw7GqXg=w1509-h769)


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