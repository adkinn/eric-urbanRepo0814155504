---
title: "SetAccountProperties Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 279fb61e-58d9-48a8-82c0-2fa1b25f0981
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
---
# SetAccountProperties Service Operation
Sets account level properties by name.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>SetAccountPropertiesRequest Message

### Request Body
The *SetAccountPropertiesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountProperties*|The list of account properties that you want to set.<br/><br/>For example you can enable Microsoft Click Id auto-tagging for tracking offline conversions.<br/><br/>Partial success is not supported i.e., if any account property cannot be set, then none of the account properties will be set.<br/><br/>**Required**: Yes|[AccountProperty](../campaign-api/accountproperty-data-object.md) array|


### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The response does not contain additional body elements.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">SetAccountProperties</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <SetAccountPropertiesRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountProperties i:nil="false">
        <AccountProperty>
          <Name></Name>
          <Value i:nil="false"></Value>
        </AccountProperty>
      </AccountProperties>
    </SetAccountPropertiesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>SetAccountPropertiesResponse Message

### <a name="Body_Elements"></a>Response Body

The response does not contain additional body elements.

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
    <SetAccountPropertiesResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11" />
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetAccountProperties](../campaign-api/getaccountproperties-service-operation.md)  
