---
title: "GetEstimatedBidByKeywordIds Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0e11ddc-17aa-4c5e-9872-c5673b109cc4
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetEstimatedBidByKeywordIds Service Operation
Gets the estimated bid value of one or more keywords - specified by keyword identifier - that could have resulted in an ad appearing in the targeted position in the search results in the last  7 days. In addition, the operation provides estimates of clicks, average cost per click (CPC), and impressions that the keywords could have generated with the estimated bid.

> [!NOTE]
> The estimates are based on the last 7 days of performance data, and not a prediction or guarantee of future performance.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetEstimatedBidByKeywordIdsRequest Message

### Request Body
The *GetEstimatedBidByKeywordIdsRequest* object defines the elements of the request's body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*KeywordIds*|An array of identifiers of the keywords for which you want to get the suggested bid values that could have resulted in your ad appearing in the targeted position in the search results. You may specify a maximum of 1,000 keywords.|*long* array|Yes|
|*TargetPositionForAds*|The position in which you want your ads to appear in the search results.<br /><br />The default value is MainLine1.|[TargetAdPosition](../adinsight-api/targetadposition-value-set.md)|No|

### Request Headers
[!INCLUDE[header_intro](../adinsight-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[adint_header_oauth](../adinsight-api/includes/adint-header-oauth.md)]
#### Password Authentication
[!INCLUDE[adint_header_password](../adinsight-api/includes/adint-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <Action mustUnderstand="1">GetEstimatedBidByKeywordIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetEstimatedBidByKeywordIdsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </KeywordIds>
      <TargetPositionForAds></TargetPositionForAds>
    </GetEstimatedBidByKeywordIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetEstimatedBidByKeywordIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordEstimatedBids*|An array of [KeywordIdEstimatedBid](../adinsight-api/keywordidestimatedbid-data-object.md) data objects. The array contains a corresponding item for each keyword specified in the request. If the keyword ID is not valid, the corresponding item in the array will be null.<br /><br />Each [KeywordIdEstimatedBid](../adinsight-api/keywordidestimatedbid-data-object.md) contains a keyword identifier and a  [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md). If there is data available for the keyword, the [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md) will provide a suggested bid value that could have resulted in an ad appearing in the targeted position of the search results. Otherwise, the [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md) element will be set to null.|[KeywordIdEstimatedBid](../adinsight-api/keywordidestimatedbid-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[adint_response_header_table](../adinsight-api/includes/adint-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  </s:Header>
  <s:Body>
    <GetEstimatedBidByKeywordIdsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordEstimatedBids xmlns:e9="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e9:KeywordIdEstimatedBid>
          <e9:KeywordId></e9:KeywordId>
          <e9:KeywordEstimatedBid p5:nil="false">
            <e9:Keyword p5:nil="false"></e9:Keyword>
            <e9:EstimatedBids p5:nil="false">
              <e9:EstimatedBidAndTraffic>
                <e9:MinClicksPerWeek p5:nil="false"></e9:MinClicksPerWeek>
                <e9:MaxClicksPerWeek p5:nil="false"></e9:MaxClicksPerWeek>
                <e9:AverageCPC p5:nil="false"></e9:AverageCPC>
                <e9:MinImpressionsPerWeek p5:nil="false"></e9:MinImpressionsPerWeek>
                <e9:MaxImpressionsPerWeek p5:nil="false"></e9:MaxImpressionsPerWeek>
                <e9:CTR p5:nil="false"></e9:CTR>
                <e9:MinTotalCostPerWeek p5:nil="false"></e9:MinTotalCostPerWeek>
                <e9:MaxTotalCostPerWeek p5:nil="false"></e9:MaxTotalCostPerWeek>
                <e9:Currency></e9:Currency>
                <e9:MatchType></e9:MatchType>
                <e9:EstimatedMinBid></e9:EstimatedMinBid>
              </e9:EstimatedBidAndTraffic>
            </e9:EstimatedBids>
          </e9:KeywordEstimatedBid>
        </e9:KeywordIdEstimatedBid>
      </KeywordEstimatedBids>
    </GetEstimatedBidByKeywordIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
