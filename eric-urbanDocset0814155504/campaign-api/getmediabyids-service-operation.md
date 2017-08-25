---
title: "GetMediaByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00549a1a-a918-4a02-b560-08c9db91d69f
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetMediaByIds Service Operation
Gets the specified media from an account?s media library.

> [!NOTE]
> This operation only supports media identifiers for location ad extensions. For getting image ad extension media, you should use [GetMediaMetaDataByIds](../campaign-api/getmediametadatabyids-service-operation.md).

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetMediaByIdsRequest Message

### Request Body
The *GetMediaByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AccountId*|The identifier of the account that owns the media library.|*long*|
|*MediaIds*|The identifiers of the media to get.<br /><br />You can specify a maximum of 10 media identifiers in a single call.|*long* array|

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
    <Action mustUnderstand="1">GetMediaByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetMediaByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AccountId></AccountId>
      <MediaIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </MediaIds>
    </GetMediaByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetMediaByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Media*|The specified media from the library.|[Media](../campaign-api/media-data-object.md) array|

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
    <GetMediaByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Media p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Media p4:type="-- specify derived type here with the appropriate prefix --">
          <Id p4:nil="false"></Id>
          <MediaType p4:nil="false"></MediaType>
          <Type p4:nil="false"></Type>
          <!--Keep these fields if you set the i:type attribute to Image-->
          <Data p4:nil="false"></Data>
        </Media>
      </Media>
    </GetMediaByIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddMedia](../campaign-api/addmedia-service-operation.md)

