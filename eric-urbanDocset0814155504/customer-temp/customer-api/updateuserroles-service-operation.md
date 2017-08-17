---
title: "UpdateUserRoles Service Operation"
ms.custom: ""
ms.date: "04/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8de1b3e7-8310-4546-a640-b28e3b08a918
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateUserRoles Service Operation
Updates the roles of the specified user.

||
|-|
|[!INCLUDE[cusman_navigation](../customer-api/includes/cusman-navigation.md)]|

## <a name="request"></a>UpdateUserRolesRequest Message

### Request Body
The *UpdateUserRolesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomerId*|The identifier of the customer to which the user belongs.|*long*|
|*DeleteAccounts*|An array of identifiers of the accounts to remove from the list of accounts that the user can manage.<br /><br />For usage, see the [Remarks](#remarks) section below.|*long* array|
|*DeleteCustomers*|An array of identifiers of the customers to remove from the list of customers that the user can manage.<br /><br />For usage, see the [Remarks](#remarks) section below.|*long* array|
|*DeleteRoleId*|The identifier of the role to which the values specified in the *DeleteAccounts* or *DeleteCustomers* element applies, if set.<br /><br />For more information about possible role values, see the corresponding **Integer Value** column within the [UserRole](../customer-api/userrole-value-set.md).|*int*|
|*NewAccounts*|An array of identifiers of the accounts to restrict the user to. The user will be able to manage only these accounts.<br /><br />If the user is currently restricted to a set of accounts, set this element to the new accounts that you want the user to also manage. For example, if the user currently manages accounts 123 and 456, and you want the user to also manage account 789, set this element to 789.<br /><br />For usage, see the [Remarks](#remarks) section below.|*long* array|
|*NewCustomers*|An array of identifiers of the customers to restrict the user to. The user will be able to manage only these customers.<br /><br />For usage, see the [Remarks](#remarks) section below.|*long* array|
|*NewRoleId*|The identifier of the role to which the values specified in the *NewAccounts* or *NewCustomers* element applies to, if set.<br /><br />For more information about possible role values, see the corresponding **Integer Value** column within the [UserRole](../customer-api/userrole-value-set.md).|*int*|
|*UserId*|The identifier of the user whose role you want to update.|*long*|

### Request Headers
[!INCLUDE[header_intro](../customer-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[cusman_header_oauth](../customer-api/includes/cusman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[cusman_header_password](../customer-api/includes/cusman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <Action mustUnderstand="1">UpdateUserRoles</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <UpdateUserRolesRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomerId></CustomerId>
      <UserId></UserId>
      \<NewRoleId i:nil="false"></NewRoleId>
      \<NewAccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </NewAccountIds>
      \<NewCustomerIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </NewCustomerIds>
      \<DeleteRoleId i:nil="false"></DeleteRoleId>
      \<DeleteAccountIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </DeleteAccountIds>
      \<DeleteCustomerIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </DeleteCustomerIds>
    </UpdateUserRolesRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>UpdateUserRolesResponse Message

### <a name="Body_Elements"></a>Response Body
The response does not contain additional body elements.

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[cusman_response_header_table](../customer-api/includes/cusman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <UpdateUserRolesResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <LastModifiedTime></LastModifiedTime>
    </UpdateUserRolesResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## <a name="remarks"></a>Remarks
As an example use case if an advertiser campaign manager is limited to managing accounts 123, 456, and 789, and you no longer want the user to manage 456, set the following elements accordingly:

-   Set the *NewRoleId* element to 16 (advertiser campaign manager role).

-   Set the *NewAccounts* element to an array that contains 123 and 789.

-   Set the *DeleteRoleId* element to 16 (advertiser campaign manager role).

-   Set the *DeleteAccounts* element to an array that contains 456.

If an advertiser campaign manager is limited to managing accounts 123 and 789, and you now want the user to manage all accounts, set the following elements accordingly:

-   Set the *NewRoleId* element to 16 (advertiser campaign manager role).

-   Set the *NewAccounts* element to NULL.

-   Set the *DeleteRoleId* element to 16 (advertiser campaign manager role).

-   Set the *DeleteAccounts* element to an array that contains 123, 456, and 789.

Users with account level roles can be restricted to specific accounts. Users with customer level roles can access all accounts within the user’s customer, and their access cannot be restricted to specific accounts.

> [!NOTE]
> When attempting to restrict customer level user roles to specific accounts the *UpdateUserRoles* operation will not fail, and the user will retain access for all accounts within the user’s customer.

