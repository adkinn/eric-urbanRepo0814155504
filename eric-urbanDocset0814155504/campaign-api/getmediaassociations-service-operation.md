---
title: "GetMediaAssociations Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a6d6012-160e-4e94-ada1-ea6649a80746
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetMediaAssociations Service Operation
Gets the media associations of the specified entity type from an account’s media library.

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetMediaAssociationsRequest Message

### Request Body
The *GetMediaAssociationsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MediaEnabledEntities*|Filters the results to only return media associations with the specified type of media enabled entity.<br /><br />Currently only ImageAdExtension is supported.|[MediaEnabledEntityFilter](../campaign-api/mediaenabledentityfilter-value-set.md)|
|*MediaIds*|The identifiers of the media to get corresponding entity associations.<br /><br />You can specify a maximum of 10 media identifiers in a single call.|*long* array|

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
    <Action mustUnderstand="1">GetMediaAssociations</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetMediaAssociationsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <MediaEnabledEntities></MediaEnabledEntities>
      \<MediaIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        \<a1:long>\</a1:long>
      </MediaIds>
    </GetMediaAssociationsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetMediaAssociationsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MediaMetaData*|An array of [MediaAssociation](../campaign-api/mediaassociation-data-object.md) objects that corresponds directly to the media identifiers that you specified in the request. Items of the list may be returned as null. For each list index where media associations were not retrieved, the corresponding element will be null.|[MediaAssociation](../campaign-api/mediaassociation-data-object.md) array|
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
    <GetMediaAssociationsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<MediaAssociations p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <ArrayOfMediaAssociation>
          <MediaAssociation>
            <EntityId></EntityId>
            <MediaEnabledEntity></MediaEnabledEntity>
            <MediaId></MediaId>
          </MediaAssociation>
        </ArrayOfMediaAssociation>
      </MediaAssociations>
      \<PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e133="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e133:KeyValuePairOfstringstring>
              \<e133:key p4:nil="false">\</e133:key>
              \<e133:value p4:nil="false">\</e133:value>
            \</e133:KeyValuePairOfstringstring>
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
    </GetMediaAssociationsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)

