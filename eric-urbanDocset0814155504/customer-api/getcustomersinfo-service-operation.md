---
title: "GetCustomersInfo Service Operation"
ms.custom: ""
ms.date: "04/03/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b44dde93-94f0-4dd6-a5f5-c448a637ed06
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetCustomersInfo Service Operation
Gets a list of objects that contain customer identification information, for example the name and identifier of the customer.

The list that this operation returns is based on the customers that the user that you specify in the *UserName* header element of the request, has access to. If the user is a member of the reseller’s user group, the list will contain all customers that the reseller has signed up or a subset of customers if the user is limited to a subset of customers by a user role.

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>GetCustomersInfoRequest Message

### Request Body
The *GetCustomersInfoRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ApplicationScope*|A value that determines whether to return results for advertising customers or publishing customers. If you do not specify the scope, the list may include both types of customers.|[ApplicationType](../customer-api/applicationtype-value-set.md)|
|*CustomerNameFilter*|A partial or full name of the customers that you want to get. The operation includes the customer in the result if the customer’s name begins with the specified filter name. If you do not want to filter by customer name, set this element to an empty string.<br /><br />The operation performs a case-insensitive comparison when it compares your name filter value to the customer names. For example, if you specify “t” as the name filter, the list will include customers whose names begin with “t” or “T”.|*string*|
|*TopN*|A nonzero positive integer that specifies the number of customers to return in the result.|*int*|

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
    <Action mustUnderstand="1">GetCustomersInfo</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetCustomersInfoRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomerNameFilter i:nil="false"></CustomerNameFilter>
      <TopN></TopN>
      <ApplicationScope></ApplicationScope>
    </GetCustomersInfoRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetCustomersInfoResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomersInfo*|An array of *CustomerInfo* objects that identifies the list of customers that meet the filter criteria.<br /><br />To get the customer data for a customer in the list, access the *Id* element of the *CustomerInfo* object and use it to call [GetCustomer](../customer-api/getcustomer-service-operation.md).|[CustomerInfo](../customer-api/customerinfo-data-object.md) array|

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
    <GetCustomersInfoResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomersInfo xmlns:e15="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e15:CustomerInfo>
          <e15:Id p5:nil="false"></e15:Id>
          <e15:Name p5:nil="false"></e15:Name>
        </e15:CustomerInfo>
      </CustomersInfo>
    </GetCustomersInfoResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
