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
    <p>&nbsp;</p>
    ![Azure Account Registration](https://lh3.googleusercontent.com/fife/AGXqzDlaEPU40RTOAIm3zoDyfyEKNlwTPxhDSkJMlKJRZlM-q8I57ni710BHfxvpwrZ6-o3poT-16sLTdV9TMXXpv5V4E-VxoP4T5NiCECAlUFVRropPVM52t-IkogUR73I3SuIBLAjZhKogL-DzwaU_i95fZI-lyZpKS_SJRSzgZg8nqEtegOziLvE33mSuYw6mxgDX08XypfLUbrRHKbxSzgTAWekqkjcNPT8d9B915Hrg6CchgS-vF1ZH7w9wQ1gC0FbMIYFdRXW29s7uY_ysEveP7K4hEXCF5ph35TijuIN8QtCSWzQARn9bck4gbbhvLEFQwR_vdm409kTZz9da-Fl7go967jvNZqVR_FLZUw63YRDJKH84Atn7Oaw4o2ngcP0lZOg2_-AfucbtOQmptuvDKqwjIjURlzTEAL-UQZTtNvZqOMo3cv_-16HAB2Ht86nObjuZr1JndY0Rhip0UfC-9L9EDxNhxSNdEXK0e0O58RJaV5HpQIG7CNKEQv1kJ1w5TYbqclUA7JEzqI5GU7JrvaGUWISg-IA36EeLpsvPQ7_1BiG3aDPt5yPN7D-M1hQCgY617KGlJ07mRlsvdWaYXmGEkBcHbpWwjDT3tI0BsEYecY_AE-NhciwLAq5dcWphqQSZqrS-QsFQPIXWiHCBI8-NJWiOYfezdQJ_1HpIQ-puTT-pvtrQu5x2q0VqQjZ7-kdfSmaKhnriI_BFqbzlyEh30m7I1-b95wOf3S75LY3Z8yg0bzy37FURN8qLWksKuKPBJnokGcqhFWiro6ag3vnmSLugmxFqlZv7KRe16yZ-ATaOocF3X-A7-XDlPgdtv8g5c7s6YZ8uWQHGbLui9dnWKV1uoC90i7CpBVnQ3y0i2SG205MYJI330Tp7Hb3TJsZ0GjFR_RACq76VA7a6xEzcRnN2Od7b5qD42oUUqrcB1xx-x8utKBlXeRd25ERYZ3A4Qyhq1PvtmGlM2HsqHzd8Nby-CG4sCet6197T0QJeKFYq0H1kOQaVX-KKeDnnUpgNgwXyrYXk_mKP-SzaP47EHkXxDqkFl-pB4XfESE2vHZbkdUqcWiue9pJJgLG7t6-ptm0zgOElLnDdvJj4YzFnPQ1joqodJEeb6a8GdAWX-71mqPyQ3JfVIs1XFB8ELiShCRoTgD9cAFhIayJWsRrSulN6tuYWc7sXuTvqac4qt7-h6mLa2acN8zNr2z0v9wBKuAobNeLDevLXb4t9WYYFiBX5AX6kyNYDu6oNGkDfOqHK9jGwxCHP0-hnNIXriCk_9joB1GLZ7NqsX4Fbw8IwhW7ZPNMLopBfPw_8-1epP5UyEE9so58eBhX5raeuekUcbRQsXJxcBaq7QOlMisOKVs5e4MqqQBvsO7YwpSah3NxZDuIfvEC3mkJmI-Xj8qukA6rLZW_Op66IchYXAC86fhXJbPtrEFFKCKEjZ-61U8urMEiXPTS02pvN5oJxBTtoBQJYd9ilf59bLMCgbDCfHGO6XaeS6A2zjVFSHPhBiben3QhotkaOOVrmrBORDSjSSRyMzVQ=w1870-h959)
    <p>&nbsp;</p>
    <b>The following are the steps for Azure Csp account registration:</b>
    <p>&nbsp;</p>
    1. Input your Microsoft Partner ID, then click Submit.\
    ![Partner Id](https://lh3.googleusercontent.com/fife/AGXqzDlYOT6I8knCl8UPOZ7vpvsAsVXwnsRdkDVEcYeLaHhxMoVNWzAKmRMDB3rXT-n_ECJ7VgvBXQVuzkR4vzZOZHVAVJ-P6Rt7S8L17ePifku7qW5_SavgWQCRIjjKwPNn2l2TDdlVq3MLl4oXdagr-Xd3V5IQfuaC37IvUEH1vOFEl5nLCOlFIuAszJVYTn1g4jH7_2khG5tSlkcknwRil0vwsz5ylN3jrVgkbdUEPxfkYTLkgGeVqZ3dCUxFGWX2BXGrf4YNeAStORFb7Cw4Aqa3SNnuArs0OqZ7P150209KfENbdE38jObXGn9YchjI5C5C4ZgipBklR97TzBYsDKZfnqw_tGQaDAlB_7iJosq7tiXvw8FeWDSkt-p0R0_AtYnJkVf5I6sgLq01ebBJN4xx4-iMs0Q0cAdCwDkP6llQv1-wVKdjdXJ82xGU1L_94wgj5noT-DwDwXl5Yvc09qiV10KiNZqo3xvGC9Z4dOtH6Jd8ce1CTf2LvRR4TfoPFPBwDAGMNy3cktf-QMK86yJKAdH1FPZY0eGiRSAuxTL_ojfqxwDNUCIDtsBc1a-MlDZYhVepnb_Z_9x6Yi43A8rRykPmFnfVoJsLdLq5e5tmQ-V1RoQWWXaAebD30dBzgfTENYK39Lg0umLkCWqRYNdy7ulIhdCbcaBz6IL8yBv8YP5Uk_zht0fQjvUIDBk7DGYawz443WxeV1xRrXaYClTqXJHTaaApKIrO-58Rh8tF4xR2Iq0wQFWiP6cjA-esgpSAiaJzrGp8KmtgSF40oKTPmRc4eF2SzchzxQOK8g5o10LFThlyK48NlqQxp86uxiY2vVH8ah_b-rHYvlxhjNvKPaaBACVdntwCkD3Cx6MS8AmTXqm_DUGrfgrK5cWpezE7W216255-bTuRnkBV7WppdrfWew0pNqfDfYZQc04p5raMQLw1KAuDoLGHOk02Vapx9fFBAtD5HqyYg5Ai6k_0k6rkbaKHAxhQtgbRhFQiTeqxjPY0ea5MN1v-kXiA1rNcqdW1T9TASHOeriBC-d0heLLvFjxEHcHXXBaYG8CqxpQuu9Vd0l7EipsBcjfcBgOQmPoD-ehZtj8XHSClJ0HGl_vuq_9F-wAzhdQZLkSMYptuRY3a47jk8QfXqYMTz19qGu3Umf7rHgFXWTp5w-lqiwQM2ozdLf1fDauW2SMIrei2GtJ26Luv7t02U0akiuHdkG_x0Bp6uvHptAhPTimqDbZe7CA2oQgiqCFzUU_EvXj7gdA6axlDFAiqvTblVuXNp8gUTgMFyfmpnoaoEQQDc08PriJYVpV3R91Yup-woYqm6gulLhhTRpkMM_EQGZ3ODlcR8b9N6KLMUVaqisw9umR6bu4T47O6-hZ3MfzP_nRLPfv3U1YnzgRRYvWX8kcgOC6qJaO6wvGfz91LMxmQ7dZynUoWt5KqYBIWMlbnZI99Vk529kDf-yR67bqvgWuROeYob0W68H9ZFFokmEizDevSWk6sLfLKQdS_qt4yPl1ky5SWu3epn-j3JnkPkOyqrXb5J0jmZGw=w1315-h959)
    <p>&nbsp;</p>
    2. Setup Partner Center Credentials:
        <p>&nbsp;</p>
        a. Click the toggle button to edit Partner Center Credentials form.
        <p>&nbsp;</p>
        b. Input the Client ID, Application ID, and Secret Key and hit Submit.
            <p>&nbsp;</p>
            ![Partner Center](https://lh3.googleusercontent.com/fife/AGXqzDnNgTo-de55bHAR1A2Y3PEbAFVaZPMspQrIUCqejZ7cgcpsdu5tcoArXkZzg245OWq3e_6mG1-zhyAxNTyvEm2hlKEXKVT8SyQOfoI952yDCM-347Z54rcfSc0z0Ot3HxtQ5xP7Z-X1axKEMWUN9nAHRCTmRjmhxEV6KhHJRd7reNOuiADgrKG_YKajruhyLnU1Ejfnf0bQcsqgbCSnM_rUpd6D5vg3vdIYioTsbsjQntWvUsO0-UiXN0-QCNPBAxDF_xh6LuWny1zSqRpZoJqrwZ4o67xFwFS7pAULa77j1SZke5I4yPpDMSULoyPlAGdyOCUanOQzEA5zlSjc3k2HtUo1TxF_ENZuKAJcNvsNuzKANteYXR7Bq-OwvHMHxPENbuHepdiHEr67Qim3S2pjxczwUgN93ZIcpYJ1OZp8HJH7h9XFuJnaJNBqHiz7N5HbcPamNknjt37NAvfgwR78xJngD4AwTgKKgCOejm1EEEQkv2RO28PNyAgzkOgOn_zfBkuF3BGA5fYMOq4hxdFwuVsm8lcmBiqa_PkcdMJKZ3mn9m2ZogSiHDGt8vmopCXolFnENHTbKjAk9jOpcpgKYp1FudpTIPO-tlk8uKKFK-iSbMy3uoP6gVmjCiDa1IyBSIdPISCAiXN0TDMrldZ5QGDwNF-YzL3uMvInNUs1ReLdYkeorhjDxJd32NZa6iXELogIN8gYCkbLxsCcVmi7V6W-RdI8aHDPRdi9i10nWBh8TfJPJEbJVc_9VeRy-grVv0dWfWUi7WMUsAfe9QfGnQ2cmcUK1K575ecRZ2tq681te199e9_1ysY6Bdi04AirYxREbNJZ_p6OH6uOA0LVU5NdcJ66QsuJy71AQJldteJQwDXCE1KT_5e33eYi982fNOQkrkMb3SP60qLxzHWy-HHsbnvEGjzSDZV8NibuzAHi6LocNZLoJfbiWAT2Uz0Ms54kn_nbUFLMeTylPmdt07GYVNABjnABFyigAchJjUfwMEvPlVozeRgsoopt3SAFryCaE3jAD_bayvMiBIFZgC-S3VfJ0PdCxGb4PmUurdr0F8szUXJv2hRWKbgMGtoPPTKTIW9IyoUudEjYICuNkE1KaYMa9TDs492y86q6dsv3T8VEju9Bb4JsVCRXg2M_0jvCIHJuOmWBpwCqKhq2VjzLg1JzybSz9GyeeDXTdBFiehjJDHUJ-szw-FpopvVudth7cb-SjvKqq9oD7DgIkeKNF3zUT5IlF1VXdQ7hi2ChUqDGQARPQIWihFQsIaJLKN2SyfkN9Y-FFsMzgE1hDfsXwGlcZfWZNjUOkk4iKChG70KCGmIyji0cM061keFkREeMmWXXa_ZT4_ukEW1sSN9vz0d7FRCXF3POnTXJ3GEfcbvR4BsrpB8jKF_GhXLyF2P1HK4w3OnQxV-v1rquwrimvRuuVGcnP1TiifC5Cqgzg7aVI_HKpmyRQA0sUNKQyFKy38Up8apPdwOU60pkk0Sg3dekdDeDcyVoRJiob718hjFGMmriSSQLz94OKS7CMB5Q-vr_-8k=w1315-h959)
        <p>&nbsp;</p>
    3. Setup Partner API Credentials:
            <p>&nbsp;</p>
        a. Click the toggle button to edit Partner API Credentials form.
            ![partner api 1st step](https://lh3.googleusercontent.com/fife/AGXqzDl13yjW7Qhf0I5EC16YYLIAyQOzRPO1enO6Sldfkl1I2ZzAKUphX78kxjsrZ68XcCvkozpqvWBabpjLn25578EbFl01wq2m2oJSNG-96EEOcanHg4Y-XrtjwzopvQu7tiSQaU7v5CuI4Gke6lf4piXxQsYGuHTCQ7HC5vCia-1dn2C--lrkvJyl7fvTutNfHJBQoXNwjQYyvhTbzHYV5EnyvspoPTNyQ6_HWWy9I1Kx7eRBqWnqdGgZ5a503bgMfp770GCARjbIYHi7dX-duqFaKN802pzGfuIJwViUAEEHJh74WKDsGPaN5uoZQvKBPFq-3EXH31lFUYFe1-Zhto9imBiv7FxD_JqnrEGQq_Ee0CNkcxgxrj8RWNTDdRP1ni6oL997mo2AsRZEXHE8s1chSWT0Pj6HTSL3kBHnS1Ax2PfxWaUOmd8bIs4Q2M8UxNhRiTFb__ZoUj4zt7TeML3RDJfB9zVj4akh14AhfYsc5qPyt9lriDP8NqkOmg7zg6g8sUf3ns3mAQA0Vleo6GXiVzozr3NJX9lz6oBLWoWm-ocXJ_oSFwPL-j-gicHflCeDjxCuNRF6t4jw8LuXtE1qthOjfDlSY3cfBrhUQeYZvrpshboFWrRxSQhVckv9e02FwQhe3tO5_mHMN0GMdvUQtaKnD8uNhBEkRiAgYxRt0CINvx197v12mseZ40XgEafsoWl5K3r_2EFBgF8LZMG9uxsYm9ncHNgCZuytigIVrKt8MlG4hKJmKMsyLVtLcGz4W5k0j61_Z3qvn3O4nxLYcehHTY18wIpnURn5gXTZA_dW0dYjztDnShuGQQzptw6FS86IYknzUsTrY0OzuZFsG7iQ_TwwMsLSgAuypw6m-ht-7pNZa4lAdy1xnwDi3Ciw6H53bm5Ix-kbROhCS4M-qwiNdEW2Tnec19JHf8aqSPC8nLqQtqQVfeEnit47XJ7132Y_3xy1KBR_POXODkJWjAgmLbRADFn1phEWOvrcsQCRABIvakzkIi-Aw4WJqpFer_ZnhfkgY57jLEkdtK9EsV-zeWOhgMgt8e06xvL-Pcgntsib0iLPP77NofraNYC3gfJTNENCWMb3-KswkCUN4o1UVxGSK6J-ZDaOZnrhq12jiKnfYGrlYPBfvARftAJC2Lrfi5xfhSyoaFQnNWcYYKVbAKQEeKRgbWOQhJbysRyQg2f46ZWoAs5UXoXcALNZfBQg3B8JKHarWt5SdHN7irwryn6IAqfrGBbIIWG04MGQ7Ikuuj2KRDMToCO282XcuGVpbcQ5eaxLZM8BrnIIjj0TU18gSpwrzD6bku4JntW0h9ZFIkHDiqpcdwV_n_C2VQ5M8sDZ3WsJSYLQRMSXL2riAA6rgExuhE7hmCU-epkchPqrfZe_gcjv1rmc9Ug-YdReC2yyByC2jD9k1suxUU3qNZb1LQJGLqSw4DlQXhCeukxd2pYK33IDdXQiDMoD966U6r2PgHekYcYA9x00nqtYIqNY30biFvN1f0mklkxeEGzmoYreviVMA1W07ywN8jQKdyA7zlA=w1870-h959)
            <p>&nbsp;</p>
        b. Input the Client ID, Application ID, and Secret Key and hit Next.
            <p>&nbsp;</p>
        c. A tab will open which needs you to log in to your Microsoft Azure account and input the required information. After this step this will redirect back to Octo with an authorization code.
            <p>&nbsp;</p>
        d. For the last step, review the information including the authorization code obtained from the previous step then hit Submit.
            <p>&nbsp;</p>
            ![partner api last step](https://lh3.googleusercontent.com/fife/AGXqzDnCFFhjXw0_88U14caSxX3LWSELh5zXhS0KUkevE2AucdeLRhEjI1EhCHorBbfOlj066Q67e_-Pu82ZxWTr77ibrYTJ20Iy44uKXoPhQ_6vbr9K6BAcJFjoKxAMjc8O_ZfF8Yehjzr20hbLppkZd2RuVF7x01C6i9EX5KHurwg3ZXFsdrVACqwX5d8UyUxxYvbqkil3WqD7HTEz-VongsKSunsQaymctI3teyK04wA3opKE3UVavFmEWQU0O8P5S9hpf3vCZbhbgsv7vG5M6-w8h6inZpyGq6VQpIiEez6OZ6R5uzJysCuLUf46rykkmAPWGHSAVI5omIVPC6zxLLCw4cKOP-n4Fb0kQ6s-ZaH6ZyLZiGqGZj8Zr5323vcrl2g82D23Qq7AvbxxCwuUwKUx_ZvVrUm_8zpaTYXsDNriMcl74pd1rbJmfd-niWVmHFJTfazYHX7pI7TIBd3zuK9XSJIWcqB6j4NbrSQFfLDPCCiMKeRnXFc-qoxLDIPRdKvSNHSrZ276ieJAj8sFRe9vwAnEuPCYMMZJrijlvcWFA9emUW--PcWJujfnTOC9tsGd4PPNP4xvHrOTbOb6euW81s2soE0YBhQlMlZTVXdnkNJaw01Fx82vwfxhit5PJlGrCSJgK3Y4h4yiVSagedmQxiOQLabWaaSA51ZQU1BCatHahKUZoEbYTRZVDkNBJd0ELk75yS6yFWjDPkltk5vdJmhJQe-ErT1A7LCoE3NJBiUmKQQ7AkMhahX8jipMIKVc2HdntA0DgfmLdxRHfMPdfe-OUkXBa_92wGPZms_RyEZrwBi55LFXDBUT8koly2UwflWwNWqGXYKmP1xrnubf0kltIepebQVg7xBloUKe0r_MjBcOO4c3gZiFoEZLUigV1QemTo-9rXMobyY0v1pOKX9t4V_n2WCiqs5GsUBxH7y9DuJuGBB74bMDSknGBAkKxlNoj_ykYa4DMy_Wz1isZl53nPGNGiYq0xq3seq61nJYapw31iFehG1rCk61W-SSgOJrG24P17v9q8y0BgpNFhXepoa3tlk_WRMp5sTeCW3qtJIpHOPCs4RIp_lNdc7Et6wUNpsMagrFPQJM7szNmmlmWK-cjFsCtDZ2QFPEZIfdw7lHLtKn05wfxpLG68E5u2a09RWGveaBKrbZk8TZKiPjIbhfdiqbGI56dXyTfWeK8TwPuQaPQStBI6XAUxGjSn2olkLCUz5zFLtKezwbOT9sWS2hwIRcvzolbIHCAtSe66iXggbONCtH9gRM0otmFURdwKJPeo9Su-7V-8JfXIXl2BE-EE85YyRfptb78LHuLuZXKYICf_CMdDeX1oIkgc3cWFQSiNCtDLJ6n53B0GArIDQ54H5rX6GFVXEo8nx8N4bSxDt6ljRX-bLbvm-BVTumKBea_143ve9pfXKSnai_jV4TZM6XtoyzDrE2Q0Z3JE2si7zdo78wJYcFLoZfkLAOEJd5GWwENQXozInSt1j4mKdwrkB7kdoQDax6frg_QTXJwCChNiwmyJxzj2W6ken9mRfGvQU=w1315-h959)
    

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