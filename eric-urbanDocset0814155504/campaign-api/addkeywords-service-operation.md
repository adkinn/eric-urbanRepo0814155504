---
title: "AddKeywords Service Operation"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 957a7fce-ed33-4bf4-a3c2-a1411e1573a0
caps.latest.revision: 10
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AddKeywords Service Operation
Adds one or more keywords to an ad group.

[!INCLUDE[campaign_service_namespace](../campaign-api/includes/campaign-service-namespace.md)]

## <a name="request"></a>AddKeywordsRequest Message

### Request Body
The *AddKeywordsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|The identifier of the ad group to add the keywords to.|*long*|
|*Keywords*|The list of keywords to add to the ad group.<br /><br />You can add a maximum of 1,000 keywords to an ad group per service request.|[Keyword](../campaign-api/keyword-data-object.md) array|

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
    <Action mustUnderstand="1">AddKeywords</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <AddKeywordsRequest xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <AdGroupId></AdGroupId>
      <Keywords i:nil="false">
        <Keyword>
          <Bid i:nil="false">
            <Amount i:nil="false"></Amount>
          </Bid>
          <BiddingScheme i:nil="false" i:type="-- specify derived type here with the appropriate prefix --">
            <Type i:nil="false"></Type>
            <!--Keep these fields if you set the i:type attribute to MaxClicksBiddingScheme-->
            <MaxCpc i:nil="false">
              <Amount i:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to MaxConversionsBiddingScheme-->
            <MaxCpc i:nil="false">
              <Amount i:nil="false"></Amount>
            </MaxCpc>
            <!--Keep these fields if you set the i:type attribute to TargetCpaBiddingScheme-->
            <MaxCpc i:nil="false">
              <Amount i:nil="false"></Amount>
            </MaxCpc>
            <TargetCpa i:nil="false"></TargetCpa>
            <!--Keep these fields if you set the i:type attribute to ManualCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to EnhancedCpcBiddingScheme-->
            <!--Keep these fields if you set the i:type attribute to InheritFromParentBiddingScheme-->
            <InheritedBidStrategyType i:nil="false"></InheritedBidStrategyType>
          </BiddingScheme>
          <DestinationUrl i:nil="false"></DestinationUrl>
          <EditorialStatus i:nil="false"></EditorialStatus>
          <FinalAppUrls xmlns:e37="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            <e37:AppUrl>
              <e37:OsType i:nil="false"></e37:OsType>
              <e37:Url i:nil="false"></e37:Url>
            </e37:AppUrl>
          </FinalAppUrls>
          <FinalMobileUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalMobileUrls>
          <FinalUrls i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
            <a1:string></a1:string>
          </FinalUrls>
          <ForwardCompatibilityMap xmlns:e38="http://schemas.datacontract.org/2004/07/System.Collections.Generic" i:nil="false">
            <e38:KeyValuePairOfstringstring>
              <e38:key i:nil="false"></e38:key>
              <e38:value i:nil="false"></e38:value>
            </e38:KeyValuePairOfstringstring>
          </ForwardCompatibilityMap>
          <Id i:nil="false"></Id>
          <MatchType i:nil="false"></MatchType>
          <Param1 i:nil="false"></Param1>
          <Param2 i:nil="false"></Param2>
          <Param3 i:nil="false"></Param3>
          <Status i:nil="false"></Status>
          <Text i:nil="false"></Text>
          <TrackingUrlTemplate i:nil="false"></TrackingUrlTemplate>
          <UrlCustomParameters xmlns:e39="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false">
            <e39:Parameters i:nil="false">
              <e39:CustomParameter>
                <e39:Key i:nil="false"></e39:Key>
                <e39:Value i:nil="false"></e39:Value>
              </e39:CustomParameter>
            </e39:Parameters>
          </UrlCustomParameters>
        </Keyword>
      </Keywords>
    </AddKeywordsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>AddKeywordsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordIds*|A list of unique system identifiers corresponding to the keywords that were added.<br /><br />The list of identifiers corresponds directly to the list of keywords in the request. Items of the list may be returned as null. For each list index where a keyword was not added, the corresponding element will be null.|*long* array|
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
    <AddKeywordsResponse xmlns="https://bingads.microsoft.com/CampaignManagement/v11">
      <KeywordIds p4:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <a1:long></a1:long>
      </KeywordIds>
      <PartialErrors p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance">
        <BatchError p4:type="-- specify derived type here with the appropriate prefix --">
          <Code></Code>
          <Details p4:nil="false"></Details>
          <ErrorCode p4:nil="false"></ErrorCode>
          <FieldPath p4:nil="false"></FieldPath>
          <ForwardCompatibilityMap xmlns:e40="http://schemas.datacontract.org/2004/07/System.Collections.Generic" p4:nil="false">
            <e40:KeyValuePairOfstringstring>
              <e40:key p4:nil="false"></e40:key>
              <e40:value p4:nil="false"></e40:value>
            </e40:KeyValuePairOfstringstring>
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
    </AddKeywordsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[cammanerror](../campaign-api/includes/cammanerror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884)[Bing Ads Operation Error Codes](http://msdn.microsoft.com/library/bing-ads-operation-error-codes.aspx).

|Error Code|
|--------------|
|InvalidCredentials|

## See Also
[DeleteKeywords](../campaign-api/deletekeywords-service-operation.md)  
[GetKeywordsByAdGroupId](../campaign-api/getkeywordsbyadgroupid-service-operation.md)  
[GetKeywordsByEditorialStatus](../campaign-api/getkeywordsbyeditorialstatus-service-operation.md)  
[GetKeywordsByIds](../campaign-api/getkeywordsbyids-service-operation.md)  
[UpdateKeywords](../campaign-api/updatekeywords-service-operation.md)  

