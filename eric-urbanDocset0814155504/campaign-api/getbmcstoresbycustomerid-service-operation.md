---
title: "GetBMCStoresByCustomerId Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b4ad426-c60d-42be-a65f-1af05e23dd81
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBMCStoresByCustomerId Service Operation
Gets the [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] stores for the specified customer.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetBMCStoresByCustomerIdRequest Message

### Request Body
The *GetBMCStoresByCustomerId* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

The request does not contain additional body elements.

> [!NOTE]
> You must use the *CustomerId* header element to specify the customer identifier for the stores that are returned.

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetBMCStoresByCustomerId</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBMCStoresByCustomerIdRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11" />
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBMCStoresByCustomerIdResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BMCStores*|The list of [!INCLUDE[storebrand](../campaign-api/includes/storebrand.md)] stores for the specified customer.|[BMCStore](../campaign-api/bmcstore-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetBMCStoresByCustomerIdResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <BMCStores p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BMCStore>
          <HasCatalog></HasCatalog>
          <Id></Id>
          <IsActive></IsActive>
          <IsProductAdsEnabled></IsProductAdsEnabled>
          <Name p4:nil="false"></Name>
        </BMCStore>
      </BMCStores>
    </GetBMCStoresByCustomerIdResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
