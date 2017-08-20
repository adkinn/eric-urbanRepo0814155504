---
title: "FindAccountsOrCustomersInfo Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afc08b05-f393-46b7-9fc7-d5646a70cf29
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# FindAccountsOrCustomersInfo Service Operation
Gets a list of the accounts and customers that match the specified filter criteria.

||
|-|
|[!INCLUDE[cusman_navigation_noremarks](../customer-api/includes/cusman-navigation-noremarks.md)]|

## <a name="request"></a>FindAccountsOrCustomersInfoRequest Message

### Request Body
The *FindAccountsOrCustomersInfoRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ApplicationScope*|A value that determines whether to return advertiser accounts or publisher accounts. If you do not specify the scope, the list may include both types of accounts.|[ApplicationType](../customer-api/applicationtype-value-set.md)|
|*Filter*|The criteria to use to filter the list of accounts and customers. You can specify either an account name, account number, or customer name.<br /><br />The filter value can contain a partial or full name or number. The operation includes the account or customer in the result if the name or number begins with the specified filter value.<br /><br />The operation performs a case-insensitive comparison when it compares your filter value to the name or number. For example, if you specify “t” as the filter value, the list will include accounts and customers whose names begin with “t” or “T”.<br /><br />The operation filters first for accounts that match the filter criteria. If the number of accounts that match the filter criteria is less than the specified *TopN* value, the operation searches for customers whose name matches the filter criteria.<br /><br />Setting this element to an empty string is the same as calling the [GetAccountsInfo](../customer-api/getaccountsinfo-service-operation.md) followed by calling the [GetCustomersInfo](../customer-api/getcustomersinfo-service-operation.md).|*string*|
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
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <Action mustUnderstand="1">FindAccountsOrCustomersInfo</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <FindAccountsOrCustomersInfoRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      \<Filter i:nil="false"></Filter>
      <TopN></TopN>
      \<ApplicationScope i:nil="false"></ApplicationScope>
    </FindAccountsOrCustomersInfoRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>FindAccountsOrCustomersInfoResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountInfoWithCustomerData*|A list of *AccountInfoWithCustomerData* objects of the accounts and customers that match the specified filter criteria.<br /><br />The objects contain information that identifies the account and customer. To get the complete details of an account in the list, access the *AccountId* element of the *AccountInfoWithCustomerData* object and use it to call [GetAccount](../customer-api/getaccount-service-operation.md) operation.<br /><br />To get the complete details of a customer in the list, access the *CustomerId* element of the *AccountInfoWithCustomerData* object and use it to call [GetCustomer](../customer-api/getcustomer-service-operation.md).|[AccountInfoWithCustomerData](../customer-api/accountinfowithcustomerdata-data-object.md) array|

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
    <FindAccountsOrCustomersInfoResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      \<AccountInfoWithCustomerData xmlns:e6="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e6:AccountInfoWithCustomerData>
          \<e6:CustomerId p5:nil="false">\</e6:CustomerId>
          \<e6:CustomerName p5:nil="false">\</e6:CustomerName>
          \<e6:AccountId>\</e6:AccountId>
          \<e6:AccountName p5:nil="false">\</e6:AccountName>
          \<e6:AccountNumber p5:nil="false">\</e6:AccountNumber>
          \<e6:AccountLifeCycleStatus>\</e6:AccountLifeCycleStatus>
          \<e6:PauseReason p5:nil="false">\</e6:PauseReason>
        \</e6:AccountInfoWithCustomerData>
      </AccountInfoWithCustomerData>
    </FindAccountsOrCustomersInfoResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
