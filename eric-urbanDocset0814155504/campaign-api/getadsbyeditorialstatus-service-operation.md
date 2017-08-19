---
title: "GetAdsByEditorialStatus Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0faf6178-4fc8-40b4-9ba5-9e5cdd21ce96
caps.latest.revision: 11
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAdsByEditorialStatus Service Operation
Retrieves the ads that belong to the specified ad group and have the specified editorial review status.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAdsByEditorialStatusRequest Message

### Request Body
The *GetAdsByEditorialStatusRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AdGroupId*|The identifier of the ad group to retrieve the ads from.|*long*|Yes|
|*EditorialStatus*|The editorial review status that the ads must have to be returned.|[AdEditorialStatus](../campaign-api/adeditorialstatus-value-set.md)|Yes|
|*AdTypes*|One or more types of ads to return.|[AdType](../campaign-api/adtype-value-set.md) array|Yes|

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
    <Action mustUnderstand="1">GetAdsByEditorialStatus</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAdsByEditorialStatusRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupId></AdGroupId>
      <EditorialStatus></EditorialStatus>
      <AdTypes i:nil="false">
        <AdType></AdType>
      </AdTypes>
    </GetAdsByEditorialStatusRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAdsByEditorialStatusResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Ads*|The list of ads that have been retrieved. If the ad group doesn't contain ads that meet the criteria, this array is empty.|[Ad](../campaign-api/ad-data-object.md) array|

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
    <GetAdsByEditorialStatusResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Ads p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Ad p4:type="-- specify derived type here with the appropriate prefix --">
          <AdFormatPreference p4:nil="false"></AdFormatPreference>
          <DevicePreference p4:nil="false"></DevicePreference>
          <EditorialStatus p4:nil="false"></EditorialStatus>
          <FinalAppUrls xmlns:e106="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e106:AppUrl>
              <e106:OsType p4:nil="false"></e106:OsType>
              <e106:Url p4:nil="false"></e106:Url>
            </e106:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <ForwardCompatibilityMap xmlns:e107="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e107:KeyValuePairOfstringstring>
              <e107:key p4:nil="false"></e107:key>
              <e107:value p4:nil="false"></e107:value>
            </e107:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <Status p4:nil="false"></Status>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <Type p4:nil="false"></Type>
          <UrlCustomParameters xmlns:e108="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e108:Parameters p4:nil="false">
              <e108:CustomParameter>
                <e108:Key p4:nil="false"></e108:Key>
                <e108:Value p4:nil="false"></e108:Value>
              </e108:CustomParameter>
            </e108:Parameters>
          </UrlCustomParameters>
          <!--Keep these fields if you set the i:type attribute to TextAd-->
          <DestinationUrl p4:nil="false"></DestinationUrl>
          <DisplayUrl p4:nil="false"></DisplayUrl>
          <Text p4:nil="false"></Text>
          <Title p4:nil="false"></Title>
          <!--Keep these fields if you set the i:type attribute to ProductAd-->
          <PromotionalText p4:nil="false"></PromotionalText>
          <!--Keep these fields if you set the i:type attribute to AppInstallAd-->
          <AppPlatform p4:nil="false"></AppPlatform>
          <AppStoreId p4:nil="false"></AppStoreId>
          <Text p4:nil="false"></Text>
          <Title p4:nil="false"></Title>
          <!--Keep these fields if you set the i:type attribute to ExpandedTextAd-->
          <DisplayUrl p4:nil="false"></DisplayUrl>
          <Path1 p4:nil="false"></Path1>
          <Path2 p4:nil="false"></Path2>
          <Text p4:nil="false"></Text>
          <TitlePart1 p4:nil="false"></TitlePart1>
          <TitlePart2 p4:nil="false"></TitlePart2>
          <!--Keep these fields if you set the i:type attribute to DynamicSearchAd-->
          <Path1 p4:nil="false"></Path1>
          <Path2 p4:nil="false"></Path2>
          <Text p4:nil="false"></Text>
        </Ad>
      </Ads>
    </GetAdsByEditorialStatusResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddAds](../campaign-api/addads-service-operation.md)  
[DeleteAds](../campaign-api/deleteads-service-operation.md)  
[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)  
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  

