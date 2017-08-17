---
title: "AddSharedEntity Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa2aa6c2-c119-4931-b89f-a140937a21af
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddSharedEntity Service Operation
Adds a negative keyword list to the account's library. Items in the account's library can be associated with any campaign within the account.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddSharedEntityRequest Message

### Request Body
The *AddSharedEntityRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ListItems*|The negative keywords to add to the negative keyword list.<br /><br />The list can contain a maximum of 5,000 items.<br /><br />**Note:** You cannot add existing negative keywords with assigned identifiers. You can add the same negative keyword and match type to a negative keyword list, and it will be assigned a new identifier.|[SharedListItem](../campaign-api/sharedlistitem-data-object.md) array|
|*SharedEntity*|The negative keyword list to add to the account's shared library.|[SharedEntity](../campaign-api/sharedentity-data-object.md)|

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
    <Action mustUnderstand="1">AddSharedEntity</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AddSharedEntityRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <SharedEntity i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
        <AssociationCount i:nil="false"></AssociationCount>
        <ForwardCompatibilityMap xmlns:e42="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
          <e42:KeyValuePairOfstringstring>
            <e42:key i:nil="false"></e42:key>
            <e42:value i:nil="false"></e42:value>
          </e42:KeyValuePairOfstringstring>
        </ForwardCompatibilityMap>
        <Id i:nil="false"></Id>
        <Name i:nil="false"></Name>
        <Type i:nil="false"></Type>
        <!--Keep these fields if you set the i:type attribute to SharedList-->
        <ItemCount i:nil="false"></ItemCount>
      </SharedEntity>
      <ListItems i:nil="false">
        <SharedListItem i:type="-- specify derived type here with the appropriate prefix --">
          <ForwardCompatibilityMap xmlns:e43="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e43:KeyValuePairOfstringstring>
              <e43:key i:nil="false"></e43:key>
              <e43:value i:nil="false"></e43:value>
            </e43:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Type i:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to NegativeKeyword-->
          <Id i:nil="false"></Id>
          <MatchType></MatchType>
          <Text i:nil="false"></Text>
        </SharedListItem>
      </ListItems>
    </AddSharedEntityRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AddSharedEntityResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ListItemIds*|A list of *long* values that represents the identifiers for the list items that were added.<br /><br />Items of the list may be returned as null. For each list index where a list item was not added, the corresponding element will be null.|*long* array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|
|*SharedEntityId*|The identifier for the shared entity that was added.|*long*|

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
    <AddSharedEntityResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ListItemIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </ListItemIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e44="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e44:KeyValuePairOfstringstring>
              <e44:key p4:nil="false"></e44:key>
              <e44:value p4:nil="false"></e44:value>
            </e44:KeyValuePairOfstringstring>
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
      <SharedEntityId></SharedEntityId>
    </AddSharedEntityResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteSharedEntities](../campaign-api/deletesharedentities-service-operation.md)  
[DeleteSharedEntityAssociations](../campaign-api/deletesharedentityassociations-service-operation.md)  
[GetSharedEntitiesByAccountId](../campaign-api/getsharedentitiesbyaccountid-service-operation.md)  
[GetSharedEntityAssociationsByEntityIds](../campaign-api/getsharedentityassociationsbyentityids-service-operation.md)  
[GetSharedEntityAssociationsBySharedEntityIds](../campaign-api/getsharedentityassociationsbysharedentityids-service-operation.md)  
[SetSharedEntityAssociations](../campaign-api/setsharedentityassociations-service-operation.md)  
[UpdateSharedEntities](../campaign-api/updatesharedentities-service-operation.md)  

