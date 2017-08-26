---
title: "GetSharedEntityAssociationsByEntityIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9812312b-2845-4144-964d-33dbb23a38ca
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetSharedEntityAssociationsByEntityIds Service Operation
Gets negative keyword list associations for the specified campaigns.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetSharedEntityAssociationsByEntityIdsRequest Message

### Request Body
The *GetSharedEntityAssociationsByEntityIdsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityIds*|The list of campaign identifiers to return shared negative keyword list associations.<br /><br />This array can contain a maximum of 100 elements.|*long* array|
|*EntityType*|The type of entity corresponding to the specified *EntityIds* element.<br /><br />Currently the only supported value is *Campaign*.|*string*|
|*SharedEntityType*|The type of shared entity to get associations from the account's library.<br /><br />Currently the only supported value is *NegativeKeywordList*.|*string*|

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
    <Action mustUnderstand="1">GetSharedEntityAssociationsByEntityIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetSharedEntityAssociationsByEntityIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <EntityIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </EntityIds>
      <EntityType i:nil="false"></EntityType>
      <SharedEntityType i:nil="false"></SharedEntityType>
    </GetSharedEntityAssociationsByEntityIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetSharedEntityAssociationsByEntityIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Associations*|An array of [SharedEntityAssociation](../campaign-api/sharedentityassociation-data-object.md) objects that corresponds directly to the entity identifiers that you specified in the request. Items of the list may be returned as null. For each list index where an association was not retrieved, the corresponding element will be null.|[SharedEntityAssociation](../campaign-api/sharedentityassociation-data-object.md) array|
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
    <GetSharedEntityAssociationsByEntityIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Associations p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <SharedEntityAssociation>
          <EntityId></EntityId>
          <EntityType p4:nil="false"></EntityType>
          <SharedEntityId></SharedEntityId>
          <SharedEntityType p4:nil="false"></SharedEntityType>
        </SharedEntityAssociation>
      </Associations>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e139="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e139:KeyValuePairOfstringstring>
              <e139:key p4:nil="false"></e139:key>
              <e139:value p4:nil="false"></e139:value>
            </e139:KeyValuePairOfstringstring>
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
    </GetSharedEntityAssociationsByEntityIdsResponse>
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
[DeleteSharedEntities](../campaign-api/deletesharedentities-service-operation.md)  
[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)  
[GetSharedEntitiesByAccountId](../campaign-api/getsharedentitiesbyaccountid-service-operation.md)  
[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)  
[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)  
[UpdateSharedEntities](../campaign-api/updatesharedentities-service-operation.md)  

