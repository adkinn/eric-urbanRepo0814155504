---
title: "AddAds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 223bd85b-47d3-4156-8ce5-58f3ca34307f
caps.latest.revision: 13
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddAds Service Operation
Adds one or more ads to an ad group.

[!INCLUDE[deprecate_sta](../campaign-api/includes/deprecate-sta.md)]

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>AddAdsRequest Message

### Request Body
The *AddAdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The identifier of the ad group to add the ads to.|*long*|
|*Ads*|An array of up to 50 ads that you want added to the ad group.|[Ad](../campaign-api/ad-data-object.md) array|

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
    <Action mustUnderstand="1">AddAds</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <AddAdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupId></AdGroupId>
      \<Ads i:nil="false">
        \<Ad i:type="-- specify derived type here with the appropriate prefix --">
          \<AdFormatPreference i:nil="false"></AdFormatPreference>
          \<DevicePreference i:nil="false"></DevicePreference>
          \<EditorialStatus i:nil="false"></EditorialStatus>
          \<FinalAppUrls xmlns:e21="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e21:AppUrl>
              \<e21:OsType i:nil="false">\</e21:OsType>
              \<e21:Url i:nil="false">\</e21:Url>
            \</e21:AppUrl>
          </FinalAppUrls>
          \<FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalMobileUrls>
          \<FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            \<a1:string>\</a1:string>
          </FinalUrls>
          \<ForwardCompatibilityMap xmlns:e22="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            \<e22:KeyValuePairOfstringstring>
              \<e22:key i:nil="false">\</e22:key>
              \<e22:value i:nil="false">\</e22:value>
            \</e22:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          \<Id i:nil="false"></Id>
          \<Status i:nil="false"></Status>
          \<TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          \<Type i:nil="false"></Type>
          \<UrlCustomParameters xmlns:e23="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            \<e23:Parameters i:nil="false">
              \<e23:CustomParameter>
                \<e23:Key i:nil="false">\</e23:Key>
                \<e23:Value i:nil="false">\</e23:Value>
              \</e23:CustomParameter>
            \</e23:Parameters>
          </UrlCustomParameters>
          \<!--Keep these fields if you set the i:type attribute to TextAd-->
          \<DestinationUrl i:nil="false"></DestinationUrl>
          \<DisplayUrl i:nil="false"></DisplayUrl>
          \<Text i:nil="false"></Text>
          \<Title i:nil="false"></Title>
          \<!--Keep these fields if you set the i:type attribute to ProductAd-->
          \<PromotionalText i:nil="false"></PromotionalText>
          \<!--Keep these fields if you set the i:type attribute to AppInstallAd-->
          \<AppPlatform i:nil="false"></AppPlatform>
          \<AppStoreId i:nil="false"></AppStoreId>
          \<Text i:nil="false"></Text>
          \<Title i:nil="false"></Title>
          \<!--Keep these fields if you set the i:type attribute to ExpandedTextAd-->
          \<DisplayUrl i:nil="false"></DisplayUrl>
          \<Path1 i:nil="false"></Path1>
          \<Path2 i:nil="false"></Path2>
          \<Text i:nil="false"></Text>
          \<TitlePart1 i:nil="false"></TitlePart1>
          \<TitlePart2 i:nil="false"></TitlePart2>
          \<!--Keep these fields if you set the i:type attribute to DynamicSearchAd-->
          \<Path1 i:nil="false"></Path1>
          \<Path2 i:nil="false"></Path2>
          \<Text i:nil="false"></Text>
        </Ad>
      </Ads>
    </AddAdsRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>AddAdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdIds*|A list of unique system identifiers corresponding to the ads that were added.<br /><br />The list of identifiers corresponds directly to the list of ads in the request. Items of the list may be returned as null. For each list index where an ad was not added, the corresponding element will be null.|*long* array|
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
    <AddAdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      \<AdIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<a1:long>\</a1:long>
      </AdIds>
      \<PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        \<BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          \<Details p4:nil="false"></Details>
          \<ErrorCode p4:nil="false"></ErrorCode>
          \<FieldPath p4:nil="false"></FieldPath>
          \<ForwardCompatibilityMap xmlns:e24="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            \<e24:KeyValuePairOfstringstring>
              \<e24:key p4:nil="false">\</e24:key>
              \<e24:value p4:nil="false">\</e24:value>
            \</e24:KeyValuePairOfstringstring>
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
    </AddAdsResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteAds](../campaign-api/deleteads-service-operation.md)  
[GetAdsByAdGroupId](../campaign-api/getadsbyadgroupid-service-operation.md)  
[GetAdsByEditorialStatus](../campaign-api/getadsbyeditorialstatus-service-operation.md)  
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  
[UpdateAds](../campaign-api/updateads-service-operation.md)  

