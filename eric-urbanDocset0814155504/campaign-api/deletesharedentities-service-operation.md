---
title: "DeleteSharedEntities Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5d07e85-0372-4ee0-a12e-3ed5a90eca07
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeleteSharedEntities Service Operation
Deletes negative keyword lists from the account's library.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>DeleteSharedEntitiesRequest Message

### Request Body
The *DeleteSharedEntitiesRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*SharedEntities*|The negative keyword lists to delete from the account's shared library, for example negative keyword lists.<br /><br />This array can contain a maximum of 20 elements.|[SharedEntity](../campaign-api/sharedentity-data-object.md) array|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">DeleteSharedEntities</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <DeleteSharedEntitiesRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <SharedEntities i:nil="false">
        <SharedEntity i:type="-- specify derived type here with the appropriate prefix --">
          <AssociationCount i:nil="false"></AssociationCount>
          <ForwardCompatibilityMap xmlns:e67="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e67:KeyValuePairOfstringstring>
              <e67:key i:nil="false"></e67:key>
              <e67:value i:nil="false"></e67:value>
            </e67:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <Name i:nil="false"></Name>
          <Type i:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to SharedList-->
          <ItemCount i:nil="false"></ItemCount>
        </SharedEntity>
      </SharedEntities>
    </DeleteSharedEntitiesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>DeleteSharedEntitiesResponse Message

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
    <DeleteSharedEntitiesResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e68="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e68:KeyValuePairOfstringstring>
              <e68:key p4:nil="false"></e68:key>
              <e68:value p4:nil="false"></e68:value>
            </e68:KeyValuePairOfstringstring>
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
    </DeleteSharedEntitiesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddSharedEntity](../campaign-api/addsharedentity-service-operation.md)  
[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)  
[GetSharedEntitiesByAccountId](../campaign-api/getsharedentitiesbyaccountid-service-operation.md)  
[GetSharedEntityAssociationsByEntityIds](../campaign-api/getsharedentityassociationsbyentityids-service-operation.md)  
[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)  
[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)  
[UpdateSharedEntities](../campaign-api/updatesharedentities-service-operation.md)  

