---
title: "AddMedia Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8af84c44-bd01-45fd-b834-96bd2958a2ed
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddMedia Service Operation
Adds the specified media to an account’s media library. Depending on the type of [Media](../campaign-api/media-data-object.md), you can then add the media to one or more [ImageAdExtension](../campaign-api/imageadextension-data-object.md) or [LocationAdExtension](../campaign-api/locationadextension-data-object.md) objects.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddMediaRequest Message

### Request Body
The *AddMediaRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account that owns the media library.|*long*|
|*Media*|An array of *Media* to add to the account’s media library.<br /><br />You can add a maximum of 10 media in a single call.|[Media](../campaign-api/media-data-object.md) array|

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
    <Action mustUnderstand="1">AddMedia</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddMediaRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      \<Media i:nil="false">
        \<Media i:type="-- specify derived type here with the appropriate prefix --">
          \<Id i:nil="false"></Id>
          \<MediaType i:nil="false"></MediaType>
          \<Type i:nil="false"></Type>
          \<!--Keep these fields if you set the i:type attribute to Image-->
          \<Data i:nil="false"></Data>
        </Media>
      </Media>
    </AddMediaRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddMediaResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MediaIds*|The identifiers of the media that you added to the library. You use the identifier to set the appropriate media ID field in the [ImageAdExtension](../campaign-api/imageadextension-data-object.md) or [LocationAdExtension](../campaign-api/locationadextension-data-object.md) object.<br /><br />You can get the media for image ad extensions with the [GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md) and [GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md) operations.<br /><br />You can get the media for location ad extensions with the [GetMediaByIds](../campaign-api/getmediabyids-service-operation.md). operation.|*long* array|

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
    <AddMediaResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<MediaIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<a1:long>\</a1:long>
      </MediaIds>
    </AddMediaResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteMedia](../campaign-api/deletemedia-service-operation.md)  
[GetMediaByIds](../campaign-api/getmediabyids-service-operation.md)  
[GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md)  
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)  

