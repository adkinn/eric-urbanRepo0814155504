---
title: "DeleteListItemsFromSharedList Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 074237bd-c12d-4eed-93dd-e1b806680c57
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeleteListItemsFromSharedList Service Operation
Deletes negative keywords from a negative keyword list.

> [!NOTE]
> The operation is only used for shared negative keyword lists. To delete negative keywords that are exclusively used with one campaign or ad group, see [DeleteNegativeKeywordsFromEntities](../campaign-api/deletenegativekeywordsfromentities-service-operation.md). 

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>DeleteListItemsFromSharedListRequest Message

### Request Body
The *DeleteListItemsFromSharedListRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ListItemIds*|The list of identifiers of negative keywords to delete from the negative keyword list.<br /><br />This array can contain a maximum of 5,000 elements.|*long* array|
|*SharedList*|The negative keyword list within the account's shared library, from which to delete the specified negative keywords.|[SharedList](../campaign-api/sharedlist-data-object.md)|

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
    <Action mustUnderstand="1">DeleteListItemsFromSharedList</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <DeleteListItemsFromSharedListRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ListItemIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </ListItemIds>
      <SharedList i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
        <ItemCount i:nil="false"></ItemCount>
        <!--Keep these fields if you set the i:type attribute to NegativeKeywordList-->
      </SharedList>
    </DeleteListItemsFromSharedListRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>DeleteListItemsFromSharedListResponse Message

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
    <DeleteListItemsFromSharedListResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e63="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e63:KeyValuePairOfstringstring>
              <e63:key p4:nil="false"></e63:key>
              <e63:value p4:nil="false"></e63:value>
            </e63:KeyValuePairOfstringstring>
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
    </DeleteListItemsFromSharedListResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddListItemsToSharedList](../campaign-api/addlistitemstosharedlist-service-operation.md)  
[GetListItemsBySharedList](../campaign-api/getlistitemsbysharedlist-service-operation.md)  

