---
title: "GetKeywordsByIds Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac971635-561b-4db7-9d27-fc5d979a125d
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordsByIds Service Operation
Retrieves the specified keywords.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>GetKeywordsByIdsRequest Message

### Request Body
The *GetKeywordsByIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|-------------|
|*AdGroupId*|The identifier of the ad group whose keywords you want to get.|*long*|Required|
|*KeywordIds*|A maximum of 1,000 identifiers of the keywords to get.|*long* array|Required|
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
    <Action mustUnderstand="1">GetKeywordsByIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetKeywordsByIdsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupId></AdGroupId>
      <KeywordIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </KeywordIds>
      <ReturnAdditionalFields i:nil="false"></ReturnAdditionalFields>
    </GetKeywordsByIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetKeywordsByIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Keywords*|An array of [Keyword](../campaign-api/keyword-data-object.md) objects that corresponds directly to the keyword identifiers that you specified in the request. Items of the list may be returned as null. For each list index where a keyword was not retrieved, the corresponding element will be null.|[Keyword](../campaign-api/keyword-data-object.md) array|
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
    <GetKeywordsByIdsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <Keywords p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <Keyword>
          <Bid p4:nil="false">
            <Amount p4:nil="false"></Amount>
          </Bid>
          <BiddingScheme p4:nil="false" p4:type="-- specify derived type here with the appropriate prefix --">
            <InheritedBidStrategyType p4:nil="false"></InheritedBidStrategyType>
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
          </BiddingScheme>
          <DestinationUrl p4:nil="false"></DestinationUrl>
          <EditorialStatus p4:nil="false"></EditorialStatus>
          <FinalAppUrls xmlns:e141="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e141:AppUrl>
              <e141:OsType p4:nil="false"></e141:OsType>
              <e141:Url p4:nil="false"></e141:Url>
            </e141:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <ForwardCompatibilityMap xmlns:e142="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e142:KeyValuePairOfstringstring>
              <e142:key p4:nil="false"></e142:key>
              <e142:value p4:nil="false"></e142:value>
            </e142:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id p4:nil="false"></Id>
          <MatchType p4:nil="false"></MatchType>
          <Param1 p4:nil="false"></Param1>
          <Param2 p4:nil="false"></Param2>
          <Param3 p4:nil="false"></Param3>
          <Status p4:nil="false"></Status>
          <Text p4:nil="false"></Text>
          <TrackingUrlTemplate p4:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e143="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" p4:nil="false">
            <e143:Parameters p4:nil="false">
              <e143:CustomParameter>
                <e143:Key p4:nil="false"></e143:Key>
                <e143:Value p4:nil="false"></e143:Value>
              </e143:CustomParameter>
            </e143:Parameters>
          </UrlCustomParameters>
        </Keyword>
      </Keywords>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e144="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e144:KeyValuePairOfstringstring>
              <e144:key p4:nil="false"></e144:key>
              <e144:value p4:nil="false"></e144:value>
            </e144:KeyValuePairOfstringstring>
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
    </GetKeywordsByIdsResponse>
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
[GetKeywordsByAdGroupId](../campaign-api/getkeywordsbyadgroupid-service-operation.md)  
[GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md)  
[UpdateKeywords](../campaign-api/updatekeywords-service-operation.md)  

