---
title: "GetListItemsBySharedList Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0f86077-f434-470c-ad4f-1d3911b49877
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetListItemsBySharedList Service Operation
Gets the negative keywords of a negative keyword list.

> [!NOTE]
> The operation is only used for shared negative keyword lists. To get negative keywords that are exclusively used with one campaign or ad group, see [GetNegativeKeywordsByEntityIds](../campaign-api/getnegativekeywordsbyentityids-service-operation.md). 

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetListItemsBySharedListRequest Message

### Request Body
The *GetListItemsBySharedListRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*SharedList*|The negative keyword list within the account's shared library, from which to get the negative keywords.|[SharedList](../campaign-api/sharedlist-data-object.md)|

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
    <Action mustUnderstand="1">GetListItemsBySharedList</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetListItemsBySharedListRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <SharedList i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
        <ItemCount i:nil="false"></ItemCount>
        <!--Keep these fields if you set the i:type attribute to NegativeKeywordList-->
      </SharedList>
    </GetListItemsBySharedListRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetListItemsBySharedListResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*ListItems*|The list of negative keywords. If no negative keywords exist in the negative keyword list, an empty array is returned.|[SharedListItem](../campaign-api/sharedlistitem-data-object.md) array|

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
    <GetListItemsBySharedListResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <ListItems p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <SharedListItem p4:type="-- specify derived type here with the appropriate prefix --">
          <ForwardCompatibilityMap xmlns:e132="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e132:KeyValuePairOfstringstring>
              <e132:key p4:nil="false"></e132:key>
              <e132:value p4:nil="false"></e132:value>
            </e132:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Type p4:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to NegativeKeyword-->
          <Id p4:nil="false"></Id>
          <MatchType></MatchType>
          <Text p4:nil="false"></Text>
        </SharedListItem>
      </ListItems>
    </GetListItemsBySharedListResponse>
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
[DeleteListItemsFromSharedList](../campaign-api/deletelistitemsfromsharedlist-service-operation.md)  

