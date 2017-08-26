---
title: "GetGeoLocationsFileUrl Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53786496-5566-4296-9d18-cfda69cb98a8
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetGeoLocationsFileUrl Service Operation
Gets a temporary URL that you can use to download a file that contains the supported geographical location targeting codes.

> [!NOTE]
> You must specify the account identifier in the *CustomerAccountId* header element.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetGeoLocationsFileUrlRequest Message

### Request Body
The *GetGeoLocationsFileUrlRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*Version*|The version of the location file that you want to download.<br/><br/>Currently the only supported version is 1.0. You must set this value to *1.0*. |*string*|Yes|
|*LanguageLocale*|The language and locale of the geographical location code descriptions. The supported language locale values are *zh-Hant* (Traditional Chinese), *en* (English), *fr* (French), *de* (German), *it* (Italian), *pt-BR* (Brazilian Portuguese), and *es* (Spanish).|*string*|Yes|

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
    <Action mustUnderstand="1">GetGeoLocationsFileUrl</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetGeoLocationsFileUrlRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Version i:nil="false"></Version>
      <LanguageLocale i:nil="false"></LanguageLocale>
    </GetGeoLocationsFileUrlRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetGeoLocationsFileUrlResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*FileUrl*|The file URL that you can use to download the geographical location targeting codes for the version, language, and locale that you requested.<br/><br/>Before you download the file, check whether the date and time of the *LastModifiedTimeUtc* element is later than the date and time of your previous download. You should only download the file if necessary.|*string*|
|*FileUrlExpiryTimeUtc*|The date and time that the provided file URL will expire.<br/><br/>If you do not download the file prior to the expiration time, then you can call the operation again to request a new file URL. You might observe that the URL is set to expire 15 minutes from the time this operation completes; however, you should not depend on a fixed duration. Future calls to this operation might result in a shorter or longer expiration time. <br/><br/>The value is in Coordinated Universal Time (UTC). The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://docs.microsoft.com/en-us/dotnet/framework/data/index).|*dateTime*|
|*LastModifiedTimeUtc*|The date and time that the geographical locations file for the specified version, language, and locale was last updated.<br/><br/>As a best practice you should store this date and time, and going forward only download the file if this value is updated to a later date and time.<br/><br/>The value is in Coordinated Universal Time (UTC). The date and time value reflects the date and time at the server, not the client. For information about the format of the date and time, see the dateTime entry in [Primitive XML Data Types](https://docs.microsoft.com/en-us/dotnet/framework/data/index).|*dateTime*|

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
    <GetGeoLocationsFileUrlResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <FileUrl p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></FileUrl>
      <FileUrlExpiryTimeUtc p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></FileUrlExpiryTimeUtc>
      <LastModifiedTimeUtc></LastModifiedTimeUtc>
    </GetGeoLocationsFileUrlResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[Geographical Location Codes](~/concepts/geographical-location-codes.md)
