# User Sync to Customer Engagement Instance

**Why we are doing this?** 

To prevent User sync issue during AppSource – Testdrive for Dynamics 365 Customer engagement for customers on partner tenant instance, We would like to start using Online Management API to force sync the user when there is a delay in the back ground user sync process.
As part of Testdrive process, we will be using Online Management API to force sync the user using ApplyUser method when there is a delay in the user sync (Customers who wants try Testdrive on AppSoure Apps) during Testdrive. To use Online Management API, we need Tenant permission to invoke the ApplyUser method. To achieve that, we want all the AppSource App owners to register/whitelist their Azure AD Apps (Azure AD APPID) with Online Management API so that User force sync would work when Testdrive service tries to force sync the user in the partners tenant.

**What is CDS Testdrive Utility?**

To register/whitelist an app (Aure AD AppID) with Online Management API, we have created small automated utility to run against Online Management API and registers the App. To avail AppSource test drive option, you must be already creating all the below details and publishing in AppSource. Additionally, we would request you to run the tool to register your Azure AD App with Online Management API. <br />

**Download CDSUtility** : CDSUtility is avaible on [link](https://testdrivesalesprod.blob.core.windows.net/cds-utility-forceusersync/CDSTestdriveUtility.zip). <br /> <br />
**Step-1 :** Update Config: - locate this file CDSTestdriveUtility.dll.config <br />
<br />
 ![](https://github.com/microsoft/AppSource/blob/master/Images/CDSUtiltyXMLConfig.png)
 
 <br />
 
ConfigName	

**AadApplicationId :**
	Please use the same Azure AD AppId that you are submitting in AppSource Testdrive.

**AadAppSecret :**
	Please use the same Azure AD AppKey that you are submitting in AppSource Testdrive.

**AadAppTenantId :**
	Please use the same Azure Tenant that you are submitting in AppSource Testdrive.

**AadAppCreatedOn :**
	Optional

**ServiceURL**
	**Note:** You need to pick the region URL based on the Testdrive Dynamics 365 Instance region.
Example : testdrive.crm.dynamics.com is your instance then use https://admin.services.crm.dynamics.com
Please use your appropriate region URL
More information to choose the URL based on different regions.

North America : 	https://admin.services.crm.dynamics.com

North America 2 : 	https://admin.services.crm9.dynamics.com

Europe, Middle East and Africa (EMEA) : 	https://admin.services.crm4.dynamics.com

Asia Pacific (APAC) : 	https://admin.services.crm5.dynamics.com

Oceania : 	https://admin.services.crm6.dynamics.com

Japan (JPN) : 	https://admin.services.crm7.dynamics.com

South America	:  https://admin.services.crm2.dynamics.com

India (IND) : 	https://admin.services.crm8.dynamics.com

Canada : 	https://admin.services.crm3.dynamics.com

United Kingdom (UK) : 	https://admin.services.crm11.dynamics.com

France : 	https://admin.services.crm12.dynamics.com

<br />
<br />

**How to register Azure AD AppId with Online Management API**

Pre-Requisites:  Office 365 Admin roles
To use the Online Management API, you must have one of the following admin roles assigned to you in your Office 365 tenant:

•	Global administrator

•	Service administrator

For information about these roles, see About Office 365 admin roles

**Step – 2:** Register/Whitelist App with Online Management API

1.	Open Command Prompt
2.	Locate the downloaded folder CDSTestdriveUtility.exe
3.	Execute command CDSTestdriveUtility.exe whitelistapp
4.	Press Enter Key
5.	It will prompt you to enter your Tenant username and password
6.	Press enter key again
7.	You will see the below message <br /><br />
![](https://github.com/microsoft/AppSource/blob/master/Images/WhiteListApp.png)
 

**Validate your Azure AD App is registered/whitelisted with Online Management API**

1.	Open Command Prompt
2.	Locate the downloaded folder CDSTestdriveUtility
3.	Execute command CDSTestdriveUtility.exe listallapps
4.	Press Enter Key
5.	It will prompt you to enter your Tenant username and password
6.	Press enter key again
7.	You will see the below message <br /><br />
![](https://github.com/microsoft/AppSource/blob/master/Images/CheckWhitelistedAppStatus.png)
