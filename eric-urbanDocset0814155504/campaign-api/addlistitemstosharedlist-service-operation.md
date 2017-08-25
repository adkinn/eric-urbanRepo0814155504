---
title: "AddListItemsToSharedList Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 133836e7-e87b-4cf1-a3bf-44509a12272f
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddListItemsToSharedList Service Operation
Adds negative keywords to the shared negative keyword list.

> [!NOTE]
> The operation is only used for shared negative keyword lists. To add negative keywords that are exclusively used with one campaign or ad group, see [AddNegativeKeywordsToEntities](../campaign-api/addnegativekeywordstoentities-service-operation.md). 

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>AddListItemsToSharedListRequest Message

### Request Body
The *AddListItemsToSharedListRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ListItems*|The negative keywords to add to the negative keyword list.<br /><br />The list can contain a maximum of 5,000 items.|[SharedListItem](../campaign-api/sharedlistitem-data-object.md) array|
|*SharedList*|The negative keyword list to add to the account's shared library.|[SharedList](../campaign-api/sharedlist-data-object.md)|

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
    <Action mustUnderstand="1">AddListItemsToSharedList</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AddListItemsToSharedListRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ListItems i:nil="false">
        <SharedListItem i:type="-- specify derived type here with the appropriate prefix --">
          <ForwardCompatibilityMap xmlns:e38="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e38:KeyValuePairOfstringstring>
              <e38:key i:nil="false"></e38:key>
              <e38:value i:nil="false"></e38:value>
            </e38:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Type i:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to NegativeKeyword-->
          <Id i:nil="false"></Id>
          <MatchType></MatchType>
          <Text i:nil="false"></Text>
        </SharedListItem>
      </ListItems>
      <SharedList i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
        <ItemCount i:nil="false"></ItemCount>
        <!--Keep these fields if you set the i:type attribute to NegativeKeywordList-->
      </SharedList>
    </AddListItemsToSharedListRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AddListItemsToSharedListResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ListItemIds*|A list of *long* values that represents the identifiers for the list items that were added.<br /><br />Items of the list may be returned as null. For each list index where a list item was not added, the corresponding element will be null.|*long* array|
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
    <AddListItemsToSharedListResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ListItemIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </ListItemIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e39="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e39:KeyValuePairOfstringstring>
              <e39:key p4:nil="false"></e39:key>
              <e39:value p4:nil="false"></e39:value>
            </e39:KeyValuePairOfstringstring>
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
    </AddListItemsToSharedListResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteListItemsFromSharedList](../campaign-api/deletelistitemsfromsharedlist-service-operation.md)  
[GetListItemsBySharedList](../campaign-api/getlistitemsbysharedlist-service-operation.md)  

