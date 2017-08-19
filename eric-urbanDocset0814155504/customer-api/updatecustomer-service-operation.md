---
title: "UpdateCustomer Service Operation"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0578251f-6601-4d9c-afb9-9767e5a97292
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateCustomer Service Operation
Updates the details of the specified customer.

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>UpdateCustomerRequest Message

### Request Body
The *UpdateCustomerRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Customer*|A customer object that contains the updated customer information.<br /><br />This operation overwrites the existing customer data with the contents of the customer object that you pass. This operation performs a full update, and not a partial update. The *Customer* object must contain the time stamp value from the last time that the *Customer* object was written to. To ensure that the time stamp contains the correct value, call the [GetCustomer](../customer-api/getcustomer-service-operation.md) operation. You can then update the customer data as appropriate, and call *UpdateCustomer*.|[Customer](../customer-api/customer-data-object.md)|

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
    <Action mustUnderstand="1">UpdateCustomer</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateCustomerRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <Customer xmlns:e31="https://bingads.microsoft.com/Customer/v11/Entities" i:nil="false">
        <e31:CustomerAddress i:nil="false">
          <e31:City i:nil="false"></e31:City>
          <e31:CountryCode i:nil="false"></e31:CountryCode>
          <e31:Id i:nil="false"></e31:Id>
          <e31:Line1 i:nil="false"></e31:Line1>
          <e31:Line2 i:nil="false"></e31:Line2>
          <e31:Line3 i:nil="false"></e31:Line3>
          <e31:Line4 i:nil="false"></e31:Line4>
          <e31:PostalCode i:nil="false"></e31:PostalCode>
          <e31:StateOrProvince i:nil="false"></e31:StateOrProvince>
          <e31:TimeStamp i:nil="false"></e31:TimeStamp>
        </e31:CustomerAddress>
        <e31:CustomerFinancialStatus i:nil="false"></e31:CustomerFinancialStatus>
        <e31:Id i:nil="false"></e31:Id>
        <e31:Industry i:nil="false"></e31:Industry>
        <e31:LastModifiedByUserId i:nil="false"></e31:LastModifiedByUserId>
        <e31:LastModifiedTime i:nil="false"></e31:LastModifiedTime>
        <e31:MarketCountry i:nil="false"></e31:MarketCountry>
        <ForwardCompatibilityMap xmlns:e32="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e32:KeyValuePairOfstringstring>
            <e32:key i:nil="false"></e32:key>
            <e32:value i:nil="false"></e32:value>
          </e32:KeyValuePairOfstringstring>
        </ForwardCompatibilityMap>
        <e31:MarketLanguage i:nil="false"></e31:MarketLanguage>
        <e31:Name i:nil="false"></e31:Name>
        <e31:ServiceLevel i:nil="false"></e31:ServiceLevel>
        <e31:CustomerLifeCycleStatus i:nil="false"></e31:CustomerLifeCycleStatus>
        <e31:TimeStamp i:nil="false"></e31:TimeStamp>
        <e31:Number i:nil="false"></e31:Number>
      </Customer>
    </UpdateCustomerRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateCustomerResponse Message

### <a name="Body_Elements"></a>Response Body
The response does not contain additional body elements.

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
    <UpdateCustomerResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <LastModifiedTime></LastModifiedTime>
    </UpdateCustomerResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
