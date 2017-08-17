---
title: "GetKeywordsByAdGroupId Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2c335f6c-763e-415f-9dc9-bd0eddfc16a2
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordsByAdGroupId Service Operation
Gets the keywords within an ad group.

||
|-|
|[!INCLUDE[camman_navigation_noremarks](../campaign-api/includes/camman-navigation-noremarks.md)]|

## <a name="request"></a>GetKeywordsByAdGroupIdRequest Message

### Request Body
The *GetKeywordsByAdGroupIdRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AdGroupId*|The identifier of the ad group that keywords are returned for.|*long*|Required|
|*ReturnAdditionalFields*|The list of additional properties that you want included within each returned [Keyword](../campaign-api/keyword-data-object.md) object. This set of flags enables you to get the latest features using the current version of Bing Ads Campaign Management API, and in the next version the corresponding elements will be included by default.|[KeywordAdditionalField](../campaign-api/keywordadditionalfield-value-set.md)|Optional|

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
    <Action mustUnderstand="1">GetKeywordsByAdGroupId</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetKeywordsByAdGroupIdRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupId></AdGroupId>
      <ReturnAdditionalFields i:nil="false"></ReturnAdditionalFields>
    </GetKeywordsByAdGroupIdRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetKeywordsByAdGroupIdResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keywords*|An array of [Keyword](../campaign-api/keyword-data-object.md) objects that represents the retrieved keywords. If no keywords exist, an empty array is returned.|[Keyword](../campaign-api/keyword-data-object.md) array|

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
    <GetKeywordsByAdGroupIdResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Keywords p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Keyword>
          <Bid p4:nil="false">
            <Amount p4:nil="false"></Amount>
          </Bid>
          <BiddingScheme p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            <Type p4:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to MaxClicksBiddingScheme-->
            <MaxCpc p4:nil="false">
              <Amount p4:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to MaxConversionsBiddingScheme-->
            <MaxCpc p4:nil="false">
              <Amount p4:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to TargetCpaBiddingScheme-->
            <MaxCpc p4:nil="false">
              <Amount p4:nil="false"></Amount>
            </MaxCpc>
            <TargetCpa p4:nil="false"></TargetCpa>
            <!--Keep these fields if you set the i:type attribute to ManualCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to EnhancedCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to InheritFromParentBiddingScheme-->
            <InheritedBidStrategyType p4:nil="false"></InheritedBidStrategyType>
          </BiddingScheme>
          <DestinationUrl p4:nil="false"></DestinationUrl>
          <EditorialStatus p4:nil="false"></EditorialStatus>
          <FinalAppUrls xmlns:e135="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e135:AppUrl>
              <e135:OsType p4:nil="false"></e135:OsType>
              <e135:Url p4:nil="false"></e135:Url>
            </e135:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <ForwardCompatibilityMap xmlns:e136="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e136:KeyValuePairOfstringstring>
              <e136:key p4:nil="false"></e136:key>
              <e136:value p4:nil="false"></e136:value>
            </e136:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <MatchType p4:nil="false"></MatchType>
          <Param1 p4:nil="false"></Param1>
          <Param2 p4:nil="false"></Param2>
          <Param3 p4:nil="false"></Param3>
          <Status p4:nil="false"></Status>
          <Text p4:nil="false"></Text>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e137="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e137:Parameters p4:nil="false">
              <e137:CustomParameter>
                <e137:Key p4:nil="false"></e137:Key>
                <e137:Value p4:nil="false"></e137:Value>
              </e137:CustomParameter>
            </e137:Parameters>
          </UrlCustomParameters>
        </Keyword>
      </Keywords>
    </GetKeywordsByAdGroupIdResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[AddKeywords](../campaign-api/addkeywords-service-operation.md)  
[DeleteKeywords](../campaign-api/deletekeywords-service-operation.md)  
[GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md)  
[GetKeywordsByIds](../campaign-api/getkeywordsbyids-service-operation.md)  
[UpdateKeywords](../campaign-api/updatekeywords-service-operation.md)  

