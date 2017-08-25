---
title: "UpdateAds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 329a2b8c-e2ce-413a-a7a9-dcc20c38bc7c
caps.latest.revision: 12
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UpdateAds Service Operation
Updates the specified ads within an ad group.

[!INCLUDE[deprecate_sta](../campaign-api/includes/deprecate-sta.md)]

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>UpdateAdsRequest Message

### Request Body
The *UpdateAdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The ID of the ad group that contains the ads to update.|*long*|
|*Ads*|A list of ads to update. You may update a maximum of 50 ads.<br /><br />The *Id* element must specify the ID of the ad to update. Specify only those elements that you want to update. The call will fail if you specify a non-null value for a read-only element such as *Id*.|[Ad](../campaign-api/ad-data-object.md) array|

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
    <Action mustUnderstand="1">UpdateAds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <UpdateAdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupId></AdGroupId>
      <Ads i:nil="false">
        <Ad i:type="-- specify derived type here with the appropriate prefix --">
          <AdFormatPreference i:nil="false"></AdFormatPreference>
          <DevicePreference i:nil="false"></DevicePreference>
          <EditorialStatus i:nil="false"></EditorialStatus>
          <FinalAppUrls xmlns:e174="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            <e174:AppUrl>
              <e174:OsType i:nil="false"></e174:OsType>
              <e174:Url i:nil="false"></e174:Url>
            </e174:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <ForwardCompatibilityMap xmlns:e175="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e175:KeyValuePairOfstringstring>
              <e175:key i:nil="false"></e175:key>
              <e175:value i:nil="false"></e175:value>
            </e175:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <Status i:nil="false"></Status>
          <TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          <Type i:nil="false"></Type>
          <UrlCustomParameters xmlns:e176="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            <e176:Parameters i:nil="false">
              <e176:CustomParameter>
                <e176:Key i:nil="false"></e176:Key>
                <e176:Value i:nil="false"></e176:Value>
              </e176:CustomParameter>
            </e176:Parameters>
          </UrlCustomParameters>
          <!--Keep these fields if you set the i:type attribute to TextAd-->
          <DestinationUrl i:nil="false"></DestinationUrl>
          <DisplayUrl i:nil="false"></DisplayUrl>
          <Text i:nil="false"></Text>
          <Title i:nil="false"></Title>
          <!--Keep these fields if you set the i:type attribute to ProductAd-->
          <PromotionalText i:nil="false"></PromotionalText>
          <!--Keep these fields if you set the i:type attribute to AppInstallAd-->
          <AppPlatform i:nil="false"></AppPlatform>
          <AppStoreId i:nil="false"></AppStoreId>
          <Text i:nil="false"></Text>
          <Title i:nil="false"></Title>
          <!--Keep these fields if you set the i:type attribute to ExpandedTextAd-->
          <DisplayUrl i:nil="false"></DisplayUrl>
          <Path1 i:nil="false"></Path1>
          <Path2 i:nil="false"></Path2>
          <Text i:nil="false"></Text>
          <TitlePart1 i:nil="false"></TitlePart1>
          <TitlePart2 i:nil="false"></TitlePart2>
          <!--Keep these fields if you set the i:type attribute to DynamicSearchAd-->
          <Path1 i:nil="false"></Path1>
          <Path2 i:nil="false"></Path2>
          <Text i:nil="false"></Text>
        </Ad>
      </Ads>
    </UpdateAdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>UpdateAdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
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
    <UpdateAdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e171="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e171:KeyValuePairOfstringstring>
              <e171:key p4:nil="false"></e171:key>
              <e171:value p4:nil="false"></e171:value>
            </e171:KeyValuePairOfstringstring>
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
    </UpdateAdsResponse>
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
[GetAdsByIds](../campaign-api/getadsbyids-service-operation.md)  

