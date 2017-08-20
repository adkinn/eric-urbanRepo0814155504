---
title: "GetNegativeKeywordsByEntityIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 146aa287-d649-4e52-93a9-d9c6c7cc8c32
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetNegativeKeywordsByEntityIds Service Operation
Gets the negative keywords that are only associated with the specified campaigns or ad groups.

> [!NOTE]
> The operation does not return negative keywords of a shared list.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetNegativeKeywordsByEntityIdsRequest Message

### Request Body
The *GetNegativeKeywordsByEntityIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityIds*|An array of entity identifiers to return the associated negative keywords.<br /><br />**Note:** The specified entities must all exist within the same parent entity, for example the ad group identifiers must all exist within the same campaign.<br /><br />This array can contain a maximum of 1 element.|*long* array|
|*EntityType*|The type of entity corresponding to the specified *EntityIds* element.<br /><br />Possible values include *AdGroup* and *Campaign*.|*string*|
|*ParentEntityId*|The identifier of the parent entity corresponding to the specified *EntityIds* element.<br /><br />If the entity type is AdGroup, this element should be set to the campaign identifier that contains all of the specified ad groups.<br /><br />If the entity type is Campaign, the service uses the *CustomerAccountId* header element and this element is ignored.|*long*|

### Request Headers
[!INCLUDE[header_intro](../campaign-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[camman_header_oauth](../campaign-api/includes/camman-header-oauth.md)]
#### Password Authentication
[!INCLUDE[camman_header_password](../campaign-api/includes/camman-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    <Action mustUnderstand="1">GetNegativeKeywordsByEntityIds</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetNegativeKeywordsByEntityIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<EntityIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </EntityIds>
      \<EntityType i:nil="false"></EntityType>
      \<ParentEntityId i:nil="false"></ParentEntityId>
    </GetNegativeKeywordsByEntityIdsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetNegativeKeywordsByEntityIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityNegativeKeywords*|An array of [EntityNegativeKeyword](../campaign-api/entitynegativekeyword-data-object.md) objects that corresponds directly to the entity identifiers that you specified in the request. Items of the list may be returned as null. For each list index where negative keywords for an entity were not retrieved, the corresponding element will be null.|[EntityNegativeKeyword](../campaign-api/entitynegativekeyword-data-object.md) array|
|*PartialErrors*|An array of [BatchError](../campaign-api/batcherror-data-object.md) objects that contain details for any request items that were not successful.<br /><br />The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchError](../campaign-api/batcherror-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[camman_response_header_table](../campaign-api/includes/camman-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <GetNegativeKeywordsByEntityIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<EntityNegativeKeywords p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <EntityNegativeKeyword>
          <EntityId></EntityId>
          \<EntityType p4:nil="false"></EntityType>
          \<NegativeKeywords p4:nil="false">
            <NegativeKeyword>
              \<Id p4:nil="false"></Id>
              <MatchType></MatchType>
              \<Text p4:nil="false"></Text>
            </NegativeKeyword>
          </NegativeKeywords>
        </EntityNegativeKeyword>
      </EntityNegativeKeywords>
      \<PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e135="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e135:KeyValuePairOfstringstring>
              \<e135:key p4:nil="false">\</e135:key>
              \<e135:value p4:nil="false">\</e135:value>
            \</e135:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          \<Message p4:nil="false"></Message>
          \<Type p4:nil="false"></Type>
          \<!--Keep these fields if you set the i:type attribute to EditorialError-->
          \<Appealable p4:nil="false"></Appealable>
          \<DisapprovedText p4:nil="false"></DisapprovedText>
          \<Location p4:nil="false"></Location>
          \<PublisherCountry p4:nil="false"></PublisherCountry>
          <ReasonCode></ReasonCode>
        </BatchError>
      </PartialErrors>
    </GetNegativeKeywordsByEntityIdsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md)  
[DeleteNegativeKeywordsFromEntities](../campaign-api/deletenegativekeywordsfromentities-service-operation.md)  

