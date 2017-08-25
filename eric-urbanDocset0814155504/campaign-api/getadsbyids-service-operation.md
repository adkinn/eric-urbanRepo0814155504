---
title: "GetAdsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6142536-9eda-47aa-a2d2-f30eb8931e85
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetAdsByIds Service Operation
Retrieves the specified ads from the specified ad group.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetAdsByIdsRequest Message

### Request Body
The *GetAdsByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AdGroupId*|The identifier of the ad group that contains the ads to get.|*long*|Yes|
|*AdIds*|A maximum of 20 identifiers of the requested ads.<br/><br/>**Note**: If the ad identifiers do not match the requested ad types, then the operation will return a batch error for each requested ad.|*long* array|Yes|
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
    <Action mustUnderstand="1">GetAdsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetAdsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupId></AdGroupId>
      <AdIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </AdIds>
      <AdTypes i:nil="false">
        <AdType></AdType>
      </AdTypes>
    </GetAdsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetAdsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Ads*|An array of [Ad](../campaign-api/ad-data-object.md) objects that corresponds directly to the ad identifiers that you specified in the request. Items of the list may be returned as null. For each list index where an ad was not retrieved, the corresponding element will be null.|[Ad](../campaign-api/ad-data-object.md) array|
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
    <GetAdsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Ads p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Ad p4:type="-- specify derived type here with the appropriate prefix --">
          <AdFormatPreference p4:nil="false"></AdFormatPreference>
          <DevicePreference p4:nil="false"></DevicePreference>
          <EditorialStatus p4:nil="false"></EditorialStatus>
          <FinalAppUrls xmlns:e109="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e109:AppUrl>
              <e109:OsType p4:nil="false"></e109:OsType>
              <e109:Url p4:nil="false"></e109:Url>
            </e109:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <ForwardCompatibilityMap xmlns:e110="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e110:KeyValuePairOfstringstring>
              <e110:key p4:nil="false"></e110:key>
              <e110:value p4:nil="false"></e110:value>
            </e110:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <Status p4:nil="false"></Status>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <Type p4:nil="false"></Type>
          <UrlCustomParameters xmlns:e111="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e111:Parameters p4:nil="false">
              <e111:CustomParameter>
                <e111:Key p4:nil="false"></e111:Key>
                <e111:Value p4:nil="false"></e111:Value>
              </e111:CustomParameter>
            </e111:Parameters>
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
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e112="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e112:KeyValuePairOfstringstring>
              <e112:key p4:nil="false"></e112:key>
              <e112:value p4:nil="false"></e112:value>
            </e112:KeyValuePairOfstringstring>
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
    </GetAdsByIdsResponse>
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
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  

