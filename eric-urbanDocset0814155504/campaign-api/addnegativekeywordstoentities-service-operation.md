---
title: "AddNegativeKeywordsToEntities Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25da735e-4979-4bf4-8ab7-d72609359b0c
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddNegativeKeywordsToEntities Service Operation
Adds negative keywords to the specified campaign or ad group.

> [!NOTE]
> The operation does not modify shared negative keyword lists.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddNegativeKeywordsToEntitiesRequest Message

### Request Body
The *AddNegativeKeywordsToEntitiesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*EntityNegativeKeywords*|An array of negative keyword with associated entity such as a campaign or ad group.<br /><br />The specified negative keywords will be appended to any existing negative keywords if the limit of 20,000 negative keywords per associated campaign or ad group would not be exceeded.<br /><br />**Note:** The *EntityType* specified within each *EntityNegativeKeyword* must be set to the same value.<br /><br />This array can contain a maximum of 1 *EntityNegativeKeyword* element, which contains up to 20,000 negative keywords.|[EntityNegativeKeyword](../campaign-api/entitynegativekeyword-data-object.md) array|

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
    <Action mustUnderstand="1">AddNegativeKeywordsToEntities</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddNegativeKeywordsToEntitiesRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<EntityNegativeKeywords i:nil="false">
        <EntityNegativeKeyword>
          <EntityId></EntityId>
          \<EntityType i:nil="false"></EntityType>
          \<NegativeKeywords i:nil="false">
            <NegativeKeyword>
              \<Id i:nil="false"></Id>
              <MatchType></MatchType>
              \<Text i:nil="false"></Text>
            </NegativeKeyword>
          </NegativeKeywords>
        </EntityNegativeKeyword>
      </EntityNegativeKeywords>
    </AddNegativeKeywordsToEntitiesRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddNegativeKeywordsToEntitiesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*NegativeKeywordIds*|A list of [IdCollection](../campaign-api/idcollection-data-object.md) corresponding to the negative keywords that were added for the corresponding entity.<br /><br />Within an [IdCollection](../campaign-api/idcollection-data-object.md), the list of *Ids* corresponds directly to the list of negative keywords in the request. Items of the list may be returned as null. For each list index where a negative keyword was not added, the corresponding element will be null.|[IdCollection](../campaign-api/idcollection-data-object.md) array|
|*NestedPartialErrors*|An array of [BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) objects that contain details for any negative keyword that were not successfully added. The top level error within each [BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) object corresponds to potential campaign or ad group errors. The nested list of [BatchError](../campaign-api/batcherror-data-object.md) objects would include any errors specific to the negative keywords that you attempted to add to the campaign or ad group.<br/><br/>The list of errors do not correspond directly to the list of items in the request. The list can be empty if there were no errors, or can include one or more error objects corresponding to each unsuccessful list item in the request.|[BatchErrorCollection](../campaign-api/batcherrorcollection-data-object.md) array|

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
    <AddNegativeKeywordsToEntitiesResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<NegativeKeywordIds p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <IdCollection>
          \<Ids p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:long>\</a1:long>
          </Ids>
        </IdCollection>
      </NegativeKeywordIds>
      \<NestedPartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchErrorCollection>
          \<BatchErrors p4:nil="false">
            \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
              <Code></Code>
              \<Details p4:nil="false"></Details>
              \<ErrorCode p4:nil="false"></ErrorCode>
              \<FieldPath p4:nil="false"></FieldPath>
              \<ForwardCompatibilityMap xmlns:e40="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
                \<e40:KeyValuePairOfstringstring>
                  \<e40:key p4:nil="false">\</e40:key>
                  \<e40:value p4:nil="false">\</e40:value>
                \</e40:KeyValuePairOfstringstring>
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
          </BatchErrors>
          \<Code p4:nil="false"></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e41="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e41:KeyValuePairOfstringstring>
              \<e41:key p4:nil="false">\</e41:key>
              \<e41:value p4:nil="false">\</e41:value>
            \</e41:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Index></Index>
          \<Message p4:nil="false"></Message>
          \<Type p4:nil="false"></Type>
        </BatchErrorCollection>
      </NestedPartialErrors>
    </AddNegativeKeywordsToEntitiesResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteNegativeKeywordsFromEntities](../campaign-api/deletenegativekeywordsfromentities-service-operation.md)  
[GetNegativeKeywordsByEntityIds](../campaign-api/getnegativekeywordsbyentityids-service-operation.md)  

