---
layout: page 
title: "Box Panel Customer Accounts" 
featured: true 
weight: 1 
tags: [getting started, Box Panel] 
author: Mao Jia
dateAdded: June 22, 2016 
---

## Box Panel Administrator and User

The IBM Cloud Object Storage Dedicated IBM Managed (COS Dedicated IBM Managed) supports two types of user accounts on Box Panel: Administrator and User.

The Administrator is the primary contact of your organization. Upon setup of your COS Dedicated IBM Managed environment, the Administrator account is created. If you are a secondary contact and do not have access to Box Panel yet, you can ask the Administrator to [create a Box Panel user account](../Box_Panel/index.html#create-user) for you. 

For both Administrator and User, once your account is created, you will receive an email from Blue Box, which contains the following information:

![Confirm Account Email](../../../img/confirm_account.png)

Click the link in the email to confirm your account and set a password. Now you can log in Box Panel with your account:

* URL: [https://boxpanel.bluebox.net](https://boxpanel.bluebox.net)
* Username: your email address
* Password: the password that you set

After logging in, you’ll be directed automatically to the Box Panel Dashboard.

### Administrator and User Roles

The Administrator and Users are granted different access rights in Box Panel. 


|    |Create Box Panel user |	Create COS user | Support, chat and create tickets |	View infrastructure | Receive weekly and monthly reports |	Manage all user accounts	| Manage one's own account|
|--|--|--|--|--|--|--|
| Administrator | Y | Y | Y |	Y |	Y |	Y |	Y  |
| User	| | | Y | Y | |  | Y |

<!---
The Administrator has the highest access right, while Users are further divided based on whether they have technical roles.


|    |Add new User |	Support, chat and create tickets |	View infrastructure | Receive weekly and monthly reports |	Manage all User accounts	| Manage his/her own account|
|--|--|--|--|--|--|--|
| Administrator | Y |	Y |	Y |	Y |	Y |	Y  |
| User with technical role	| | Y | Y |  |  | Y |
| User without technical role | | Y | | | | Y |
--->

## Obtain Access Credentials
{: #AccessCredentials} 


After you log into Box Panel, you can obtain your Access Credentials and endpoint URL from the Lock Box. The credentials and enpoint URL are required when you access the COS Dedicated IBM Managed service by using the API or CLI.

1. From the Dashboard page, click the **Account** navigation menu on the top of the page.
2. Then click **Lock Box** from the drop-down list.
3. Click the **Subject** of your Lock Box message to open and obtain your Access Credentials.

**Note:** If a COS user does not have Box Panel access, the administrator will be responsible for providing the credentials to the user.