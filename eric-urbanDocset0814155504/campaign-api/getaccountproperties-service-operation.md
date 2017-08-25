---
title: "GetAccountProperties Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c059681b-1f29-442a-959b-cd93d27cf656
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
---
# GetAccountProperties Service Operation
Gets account level properties by name.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAccountPropertiesRequest Message

### Request Body
The *GetAccountPropertiesRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountPropertyNames*|The names of account properties that you want to get.<br/><br/>To determine whether or not Microsoft Click Id auto-tagging is enabled, include the *MSCLKIDAutoTaggingEnabled* value in your request.<br/><br/>**Required**: Yes|[AccountPropertyName](../campaign-api/accountpropertyname-value-set.md) array|

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
    <Action mustUnderstand="1">GetAccountProperties</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAccountPropertiesRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountPropertyNames i:nil="false">
        <AccountPropertyName></AccountPropertyName>
      </AccountPropertyNames>
    </GetAccountPropertiesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAccountPropertiesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountProperties*|An array of account properties.<br /><br />For each account property name specified in the request, an [AccountProperty](../campaign-api/accountproperty-data-object.md) object is returned.|[AccountProperty](../campaign-api/accountproperty-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

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
    <GetAccountPropertiesResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountProperties p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <AccountProperty>
          <Name></Name>
          <Value p4:nil="false"></Value>
        </AccountProperty>
      </AccountProperties>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e76="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e76:KeyValuePairOfstringstring>
              <e76:key p4:nil="false"></e76:key>
              <e76:value p4:nil="false"></e76:value>
            </e76:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          <Message p4:nil="false"></Message>
          <Type p4:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to EditorialError-->
          <Appealable p4:nil="false"></Appealable>
          <DisapprovedText p4:nil="false"></DisapprovedText>
          <Location p4:nil="false"></Location>
          <PublisherCountry p4:nil="false"></PublisherCountry>
          <ReasonCode></ReasonCode>
        </BatchError>
      </PartialErrors>
    </GetAccountPropertiesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[SetAccountProperties](../campaign-api/setaccountproperties-service-operation.md)  
