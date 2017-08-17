---
title: "GetAccountsInfo Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7271e650-ef00-4378-b132-8599ccbd9326
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAccountsInfo Service Operation
Gets a list of objects that contains account identification information, for example the name and identifier of the account, for the specified customer.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>GetAccountsInfoRequest Message

### Request Body
The *GetAccountsInfoRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*CustomerId*|The identifier of the customer who owns the accounts to get. If not set, the user’s credentials are used to determine the customer.|*long*|No|
|*OnlyParentAccounts*|Determines whether to return only the accounts that belong to the customer or to also return the accounts that the customer manages for other customers. To return all accounts (those that belong to the customer and those that the customer manages), set this element to **false**; otherwise, set to **true** to return account information for only the specified customer. The default is **false**.|*boolean*|No|

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
    <Action mustUnderstand="1">GetAccountsInfo</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetAccountsInfoRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      \<CustomerId i:nil="false"></CustomerId>
      <OnlyParentAccounts></OnlyParentAccounts>
    </GetAccountsInfoRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetAccountsInfoResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountsInfo*|An array of *AccountInfo* objects that identifies the list of accounts that the customer owns.<br /><br />To get the account data for an account in the list, access the *Id* element of the *AccountInfo* object and use it to call [GetAccount](../customer-api/getaccount-service-operation.md).<br /><br />Note that there can be a delay of up to five minutes from the time that you add an account until the [GetAccountsInfo](../customer-api/getaccountsinfo-service-operation.md) returns the account in the response.|[AccountInfo](../customer-api/accountinfo-data-object.md) array|

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
    <GetAccountsInfoResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      \<AccountsInfo xmlns:e11="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e11:AccountInfo>
          \<e11:Id>\</e11:Id>
          \<e11:Name p5:nil="false">\</e11:Name>
          \<e11:Number p5:nil="false">\</e11:Number>
          \<e11:AccountLifeCycleStatus>\</e11:AccountLifeCycleStatus>
          \<e11:PauseReason p5:nil="false">\</e11:PauseReason>
        \</e11:AccountInfo>
      </AccountsInfo>
    </GetAccountsInfoResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
