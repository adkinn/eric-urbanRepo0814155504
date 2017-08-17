---
title: "Customer Management Service Operations"
ms.custom: ""
ms.date: "05/06/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2843120b-56c7-4995-809a-42a292f8342b
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Customer Management Service Operations
The Customer Management service defines the following service operations.

> [!NOTE]
> Operations reserved for internal use are not documented.

|Service Operation|Description|Request Limits|
|---------------------|---------------|------------------|
|[AddClientLinks](../customer-api/addclientlinks-service-operation.md)|Initiates the client link process to manage the account of another customer. Sends an invitation from an agency to a potential client.|10 *ClientLink*|
|[DeleteAccount](../customer-api/deleteaccount-service-operation.md)|Deletes an account.|1 *AccountId*|
|[DeleteCustomer](../customer-api/deletecustomer-service-operation.md)|Deletes a customer.|1 *CustomerId*|
|[DeleteUser](../customer-api/deleteuser-service-operation.md)|Deletes a user.|1 *UserId*|
|[FindAccounts](../customer-api/findaccounts-service-operation.md)|Gets a list of accounts owned by the specified customer that match the specified filter criteria.|1 *CustomerId*|
|[FindAccountsOrCustomersInfo](../customer-api/findaccountsorcustomersinfo-service-operation.md)|Gets a list of the accounts and customers that match the specified filter criteria.|Not applicable.|
|[GetAccount](../customer-api/getaccount-service-operation.md)|Gets the details of an account.|1 *AccountId*|
|[GetAccountsInfo](../customer-api/getaccountsinfo-service-operation.md)|Gets a list of objects that contains account identification information (for example, the name and identifier of the account) for the specified customer.|1 *CustomerId*|
|[GetCustomer](../customer-api/getcustomer-service-operation.md)|Gets the details of a customer.|1 *CustomerId*|
|[GetCustomerPilotFeatures](../customer-api/getcustomerpilotfeatures-service-operation.md)|Gets a list of the pilot programs in which the specified customer participates.|1 *CustomerId*|
|[GetCustomersInfo](../customer-api/getcustomersinfo-service-operation.md)|Gets a list of objects that contain customer identification information, for example the name and identifier of the customer.|Not applicable.|
|[GetUser](../customer-api/getuser-service-operation.md)|Gets the details of a user.|1 *UserId*|
|[GetUsersInfo](../customer-api/getusersinfo-service-operation.md)|Gets a list of objects that contains user identification information, for example the user name and identifier of the user.|1 *CustomerId*|
|[SearchAccounts](../customer-api/searchaccounts-service-operation.md)|Searches for accounts that match a specified criteria.|1 *Predicates*|
|[SearchClientLinks](../customer-api/searchclientlinks-service-operation.md)|Searches for the client links for the customer of the current authenticated user, filtered by the search criteria.|1 *Predicates*|
|[SearchCustomers](../customer-api/searchcustomers-service-operation.md)|Searches for customers that match a specified criteria.|10 *Predicates*|
|[SearchUserInvitations](../customer-api/searchuserinvitations-service-operation.md)|Searches for user invitations that match a specified criteria.|1 *Predicates*|
|[SendUserInvitation](../customer-api/senduserinvitation-service-operation.md)|Sends an invitation for  a Microsoft account user to manage one or more [!INCLUDE[brand](../customer-api/includes/brand.md)] customer accounts.|1 *UserInvitation*|
|[SignupCustomer](../customer-api/signupcustomer-service-operation.md)|Signs up a customer with [!INCLUDE[brand](../customer-api/includes/brand.md)].|1 *Customer*<br /><br />1 *Account*|
|[UpdateAccount](../customer-api/updateaccount-service-operation.md)|Updates the details of the specified account.|1 *Account*|
|[UpdateClientLinks](../customer-api/updateclientlinks-service-operation.md)|Updates the status of the specified client links.|10 *ClientLink*|
|[UpdateCustomer](../customer-api/updatecustomer-service-operation.md)|Updates the details of the specified customer.|1 *Customer*|
|[UpdateUser](../customer-api/updateuser-service-operation.md)|Updates the details of the specified user.|1 *User*|
|[UpdateUserRoles](../customer-api/updateuserroles-service-operation.md)|Updates the roles of the specified user.|1 *NewRoleId*<br /><br />1 *UserId*|
