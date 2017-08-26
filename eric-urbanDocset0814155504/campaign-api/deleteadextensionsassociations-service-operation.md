---
title: "DeleteAdExtensionsAssociations Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34191ef1-8bb5-4f9e-b3e0-28a6db365e7a
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeleteAdExtensionsAssociations Service Operation
Removes the specified association from the respective campaigns or ad groups.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>DeleteAdExtensionsAssociationsRequest Message

### Request Body
The *DeleteAdExtensionsAssociationsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account that owns the extensions.|*long*|
|*AdExtensionIdToEntityIdAssociations*|The list of ad extensions that are associated with campaigns or ad groups before calling this  operation.<br /><br />You can specify a maximum of 100 associations to delete or remove.|[AdExtensionIdToEntityIdAssociation](../campaign-api/adextensionidtoentityidassociation-data-object.md) array|
|*AssociationType*|The entity type or types associated with an ad extension.|[AssociationType](../campaign-api/associationtype-value-set.md)|

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
    <Action mustUnderstand="1">DeleteAdExtensionsAssociations</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <DeleteAdExtensionsAssociationsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <AdExtensionIdToEntityIdAssociations i:nil="false">
        <AdExtensionIdToEntityIdAssociation>
          <AdExtensionId></AdExtensionId>
          <EntityId></EntityId>
        </AdExtensionIdToEntityIdAssociation>
      </AdExtensionIdToEntityIdAssociations>
      <AssociationType></AssociationType>
    </DeleteAdExtensionsAssociationsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>DeleteAdExtensionsAssociationsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
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
    <DeleteAdExtensionsAssociationsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e54="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e54:KeyValuePairOfstringstring>
              <e54:key p4:nil="false"></e54:key>
              <e54:value p4:nil="false"></e54:value>
            </e54:KeyValuePairOfstringstring>
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
    </DeleteAdExtensionsAssociationsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddAdExtensions](../campaign-api/addadextensions-service-operation.md)  
[DeleteAdExtensions](../campaign-api/deleteadextensions-service-operation.md)  
[GetAdExtensionIdsByAccountId](../campaign-api/getadextensionidsbyaccountid-service-operation.md)  
[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  
[GetAdExtensionsEditorialReasons](../campaign-api/getadextensionseditorialreasons-service-operation.md)  
[SetAdExtensionsAssociations](../campaign-api/setadextensionsassociations-service-operation.md)  
[UpdateAdExtensions](../campaign-api/updateadextensions-service-operation.md)  

