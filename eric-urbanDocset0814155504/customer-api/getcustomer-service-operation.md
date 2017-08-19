---
title: "GetCustomer Service Operation"
ms.custom: ""
ms.date: "08/01/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53ca69df-8129-4940-a16f-1cfd4398df4b
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetCustomer Service Operation
Gets the details of a customer.

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>GetCustomerRequest Message

### Request Body
The *GetCustomerRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomerId*|The identifier of the customer whose information you want to get.|*long*|

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
    <Action mustUnderstand="1">GetCustomer</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetCustomerRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomerId></CustomerId>
    </GetCustomerRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetCustomerResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Customer*|A *Customer* object that contains information about the customer.|[Customer](../customer-api/customer-data-object.md)|

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
    <GetCustomerResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <Customer xmlns:e13="https://bingads.microsoft.com/Customer/v11/Entities" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e13:CustomerAddress p5:nil="false">
          <e13:City p5:nil="false"></e13:City>
          <e13:CountryCode p5:nil="false"></e13:CountryCode>
          <e13:Id p5:nil="false"></e13:Id>
          <e13:Line1 p5:nil="false"></e13:Line1>
          <e13:Line2 p5:nil="false"></e13:Line2>
          <e13:Line3 p5:nil="false"></e13:Line3>
          <e13:Line4 p5:nil="false"></e13:Line4>
          <e13:PostalCode p5:nil="false"></e13:PostalCode>
          <e13:StateOrProvince p5:nil="false"></e13:StateOrProvince>
          <e13:TimeStamp p5:nil="false"></e13:TimeStamp>
        </e13:CustomerAddress>
        <e13:CustomerFinancialStatus p5:nil="false"></e13:CustomerFinancialStatus>
        <e13:Id p5:nil="false"></e13:Id>
        <e13:Industry p5:nil="false"></e13:Industry>
        <e13:LastModifiedByUserId p5:nil="false"></e13:LastModifiedByUserId>
        <e13:LastModifiedTime p5:nil="false"></e13:LastModifiedTime>
        <e13:MarketCountry p5:nil="false"></e13:MarketCountry>
        <ForwardCompatibilityMap xmlns:e14="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p5:nil="false">
          <e14:KeyValuePairOfstringstring>
            <e14:key p5:nil="false"></e14:key>
            <e14:value p5:nil="false"></e14:value>
          </e14:KeyValuePairOfstringstring>
        </ForwardCompatibilityMap>
        <e13:MarketLanguage p5:nil="false"></e13:MarketLanguage>
        <e13:Name p5:nil="false"></e13:Name>
        <e13:ServiceLevel p5:nil="false"></e13:ServiceLevel>
        <e13:CustomerLifeCycleStatus p5:nil="false"></e13:CustomerLifeCycleStatus>
        <e13:TimeStamp p5:nil="false"></e13:TimeStamp>
        <e13:Number p5:nil="false"></e13:Number>
      </Customer>
    </GetCustomerResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
