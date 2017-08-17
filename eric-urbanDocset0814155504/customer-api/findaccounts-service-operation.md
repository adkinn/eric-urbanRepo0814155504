---
title: "FindAccounts Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e475fbd6-92b9-4738-a0db-c674642ab1d0
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# FindAccounts Service Operation
Gets a list of accounts owned by the specified customer that match the specified filter criteria.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>FindAccountsRequest Message

### Request Body
The *FindAccountsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountFilter*|The criteria to use to filter the list of accounts. You can specify either an account name or an account number. If your filter value is of the form, X*nnnnn*, where *nnnnn* is a series of digits, the operation filters by account number.<br /><br />The filter value can contain a partial or full account name or number of the accounts that you want to get. The operation includes the account in the result if the name or number of the account begins with the specified filter value.<br /><br />The operation performs a case-insensitive comparison when it compares your filter value to the account name or number. For example, if you specify “t” as the filter value, the list will include accounts whose names begin with “t” or “T”.<br /><br />Setting this element to an empty string is the same as calling the [GetAccountsInfo](../customer-api/getaccountsinfo-service-operation.md).|*string*|
|*ApplicationScope*|A value that determines whether to return advertiser accounts or publisher accounts. If you do not specify the scope, the list may include both types of accounts.|[ApplicationType](../customer-api/applicationtype-value-set.md)|
|*CustomerId*|The identifier of the customer whose accounts you want to get.<br /><br />If null, the operation searches for a match among all of the accounts of the customers that the user manages and owns.|*long*|
|*TopN*|A nonzero positive integer that specifies the number of accounts to return in the result. You must specify a value from 1 through 5,000.|*int*|

### Request Headers
[!INCLUDE[header_intro](../customer-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[cusman_header_oauth](../customer-api/includes/cusman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[cusman_header_password](../customer-api/includes/cusman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <Action mustUnderstand="1">FindAccounts</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <FindAccountsRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomerId i:nil="false"></CustomerId>
      <AccountFilter i:nil="false"></AccountFilter>
      <TopN></TopN>
      <ApplicationScope i:nil="false"></ApplicationScope>
    </FindAccountsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>FindAccountsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountsInfo*|A list of *AccountInfo* objects of the accounts that match the specified filter criteria.<br /><br />To get the complete details of an account in the list, access the *Id* element of the *AccountInfo* object and use it to call [GetAccount](../customer-api/getaccount-service-operation.md).|[AccountInfo](../customer-api/accountinfo-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[cusman_response_header_table](../customer-api/includes/cusman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <FindAccountsResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <AccountsInfo xmlns:e5="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e5:AccountInfo>
          <e5:Id></e5:Id>
          <e5:Name p5:nil="false"></e5:Name>
          <e5:Number p5:nil="false"></e5:Number>
          <e5:AccountLifeCycleStatus></e5:AccountLifeCycleStatus>
          <e5:PauseReason p5:nil="false"></e5:PauseReason>
        </e5:AccountInfo>
      </AccountsInfo>
    </FindAccountsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
