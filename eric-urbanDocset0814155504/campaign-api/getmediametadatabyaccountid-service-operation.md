---
title: "GetMediaMetaDataByAccountId Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 38a791f4-9031-4dfe-87c6-8b171ed5280c
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetMediaMetaDataByAccountId Service Operation
Gets the media meta data of the specified entity type from an account’s media library.

> [!NOTE]
> This operation does not return media meta data for location ad extensions. For getting location ad extension media, you should use [GetMediaByIds](../campaign-api/getmediabyids-service-operation.md).

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetMediaMetaDataByAccountIdRequest Message

### Request Body
The *GetMediaMetaDataByAccountIdRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MediaEnabledEntities*|Determines the type of media enabled entity to get meta data. Currently only ImageAdExtension is supported.|[MediaEnabledEntityFilter](../campaign-api/mediaenabledentityfilter-value-set.md)|

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
    <Action mustUnderstand="1">GetMediaMetaDataByAccountId</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetMediaMetaDataByAccountIdRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <MediaEnabledEntities></MediaEnabledEntities>
    </GetMediaMetaDataByAccountIdRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetMediaMetaDataByAccountIdResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MediaMetaData*|The specified media meta data from the library.<br /><br />The meta data includes download Urls for one or more media representations. The number of representations depends on the type of media. For example media for image ad extensions  have multiple height and width representations, and you can access each individually. For more information see [MediaEnabledEntityFilter](../campaign-api/mediaenabledentityfilter-value-set.md).|[MediaMetaData](../campaign-api/mediametadata-data-object.md) array|

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
    <GetMediaMetaDataByAccountIdResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<MediaMetaData p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <MediaMetaData>
          <Id></Id>
          \<MediaType p4:nil="false"></MediaType>
          \<Representations p4:nil="false">
            \<MediaRepresentation p4:type="-- specify derived type here with the appropriate prefix --">
              \<Name p4:nil="false"></Name>
              \<Type p4:nil="false"></Type>
              \<Url p4:nil="false"></Url>
              \<!--Keep these fields if you set the i:type attribute to ImageMediaRepresentation-->
              <Height></Height>
              <Width></Width>
            </MediaRepresentation>
          </Representations>
          \<Type p4:nil="false"></Type>
        </MediaMetaData>
      </MediaMetaData>
    </GetMediaMetaDataByAccountIdResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddMedia](../campaign-api/addmedia-service-operation.md)  
[DeleteMedia](../campaign-api/deletemedia-service-operation.md)  
[GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md)  

