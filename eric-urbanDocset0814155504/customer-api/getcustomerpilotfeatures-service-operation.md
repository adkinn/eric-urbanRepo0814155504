---
title: "GetCustomerPilotFeatures Service Operation"
ms.custom: ""
ms.date: "05/06/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62fd070e-4796-4ea1-be68-496ad7066f63
caps.latest.revision: 18
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetCustomerPilotFeatures Service Operation
Gets a list of the pilot programs in which the specified customer participates.

[!INCLUDE[customer_service_namespace](../customer-api/includes/customer-service-namespace.md)]

## <a name="request"></a>GetCustomerPilotFeaturesRequest Message

### Request Body
The *GetCustomerPilotFeaturesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CustomerId*|The identifier of the customer whose list of pilot programs you want to get.|*long*|

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
    <Action mustUnderstand="1">GetCustomerPilotFeatures</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetCustomerPilotFeaturesRequest xmlns="https://bingads.microsoft.com/Customer/v11">
      <CustomerId></CustomerId>
    </GetCustomerPilotFeaturesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetCustomerPilotFeaturesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*FeaturePilotFlags*|A list of integers that identifies the pilot programs in which the customer participates.<br /><br />For example the following values correspond to active feature pilots. For more information about pilot participation please contact your account manager.<br /><br />253 - Sitelink 2 Migration<br /><br />268 - Dynamic Search Ads<br /><br />288 - Ad Group Remarketing List Exclusions<br /><br />295 - Maximize Clicks Bid Strategy Type<br /><br />296 - Maximize Conversions Bid Strategy Type<br /><br />297 - Target CPA Bid Strategy Type<br /><br />310 - Campaign Languages<br /><br />340 - Bing Shopping Enhanced CPC Bid Strategy Type<br /><br />351 - Local Inventory Ads|*int* array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[cusman_response_header_table](../customer-api/includes/cusman-response-header-table.md)]
### <a name="response_soap"></a>Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/Customer/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetCustomerPilotFeaturesResponse xmlns="https://bingads.microsoft.com/Customer/v11">
      <FeaturePilotFlags p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:int></a1:int>
      </FeaturePilotFlags>
    </GetCustomerPilotFeaturesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cusmanerror](../customer-api/includes/cusmanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
