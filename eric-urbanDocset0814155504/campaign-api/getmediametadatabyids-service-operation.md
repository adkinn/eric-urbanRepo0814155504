---
title: "GetMediaMetaDataByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19581d11-3650-4d91-9a93-655012782d67
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetMediaMetaDataByIds Service Operation
Gets the specified media meta data from an account?s media library.

> [!NOTE]
> This operation does not return media meta data for location ad extensions. For getting location ad extension media, you should use [GetMediaByIds](../campaign-api/getmediabyids-service-operation.md).

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetMediaMetaDataByIdsRequest Message

### Request Body
The *GetMediaMetaDataByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MediaIds*|The identifiers of the media to get.<br /><br />You can specify a maximum of 100 media identifiers in a single call.|*long* array|

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
    <Action mustUnderstand="1">GetMediaMetaDataByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetMediaMetaDataByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <MediaIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </MediaIds>
    </GetMediaMetaDataByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetMediaMetaDataByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*MediaMetaData*|An array of [MediaMetaData](../campaign-api/mediametadata-data-object.md) objects that corresponds directly to the media identifiers that you specified in the request. Items of the list may be returned as null. For each list index where media meta data was not retrieved, the corresponding element will be null.<br /><br />The meta data includes download Urls for one or more media representations. The number of representations depends on the type of media. For example media for image ad extensions  have multiple height and width representations, and you can access each individually. For more information see [MediaEnabledEntityFilter](../campaign-api/mediaenabledentityfilter-value-set.md).|[MediaMetaData](../campaign-api/mediametadata-data-object.md) array|
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
    <GetMediaMetaDataByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <MediaMetaData p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <MediaMetaData>
          <Id></Id>
          <MediaType p4:nil="false"></MediaType>
          <Representations p4:nil="false">
            <MediaRepresentation p4:type="-- specify derived type here with the appropriate prefix --">
              <Name p4:nil="false"></Name>
              <Type p4:nil="false"></Type>
              <Url p4:nil="false"></Url>
              <!--Keep these fields if you set the i:type attribute to ImageMediaRepresentation-->
              <Height></Height>
              <Width></Width>
            </MediaRepresentation>
          </Representations>
          <Type p4:nil="false"></Type>
        </MediaMetaData>
      </MediaMetaData>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e134="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e134:KeyValuePairOfstringstring>
              <e134:key p4:nil="false"></e134:key>
              <e134:value p4:nil="false"></e134:value>
            </e134:KeyValuePairOfstringstring>
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
    </GetMediaMetaDataByIdsResponse>
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
[DeleteMedia](../campaign-api/deletemedia-service-operation.md)  
[GetMediaMetaDataByAccountId](../campaign-api/getmediametadatabyaccountid-service-operation.md)  

