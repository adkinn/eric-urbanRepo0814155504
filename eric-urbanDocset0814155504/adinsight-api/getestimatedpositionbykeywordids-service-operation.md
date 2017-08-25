---
title: "GetEstimatedPositionByKeywordIds Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91a9a890-9789-43bb-b946-fbcb9444e44b
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetEstimatedPositionByKeywordIds Service Operation
Gets the estimated position in the search results if the specified bid value had been used for the keywords in the last 7 days. In addition, the operation provides estimates of clicks, average cost per click (CPC), and impressions that the keywords could have generated with the estimated bid.

> [!NOTE]
> The estimates are based on the last 7 days of performance data, and not a prediction or guarantee of future performance.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetEstimatedPositionByKeywordIdsRequest Message

### Request Body
The *GetEstimatedPositionByKeywordIdsRequest* object defines the elements of the request?s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*KeywordIds*|An array of identifiers of the keywords for which you want to get the estimated position in the search results, based on the specified bid value. You may specify a maximum of 1,000 keyword identifiers.|*long* array|Yes|
|*MaxBid*|The maximum bid value to use to determine the estimated position in the search results.<br /><br />You must specify the bid value in the currency of the account.|*double*|Yes|

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
    <Action mustUnderstand="1">GetEstimatedPositionByKeywordIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetEstimatedPositionByKeywordIdsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </KeywordIds>
      <MaxBid></MaxBid>
    </GetEstimatedPositionByKeywordIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetEstimatedPositionByKeywordIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordEstimatedPositions*|A list of [KeywordIdEstimatedPosition](../adinsight-api/keywordidestimatedposition-data-object.md) data objects. The array contains an item for each keyword specified in the request. If the keyword ID is not valid, the corresponding item in the array will be null.<br /><br />Each [KeywordIdEstimatedPosition](../adinsight-api/keywordidestimatedposition-data-object.md) contains a keyword identifier and a  [KeywordEstimatedPosition](../adinsight-api/keywordestimatedposition-data-object.md). If data is available for the keyword, the [EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md) will provide the estimated position in the search results, based on the specified bid value. Otherwise, the *EstimatedPositions* element will be set to null.|[KeywordIdEstimatedPosition](../adinsight-api/keywordidestimatedposition-data-object.md) array|

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
    <GetEstimatedPositionByKeywordIdsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordEstimatedPositions xmlns:e13="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e13:KeywordIdEstimatedPosition>
          <e13:KeywordId></e13:KeywordId>
          <e13:KeywordEstimatedPosition p5:nil="false">
            <e13:Keyword p5:nil="false"></e13:Keyword>
            <e13:EstimatedPositions p5:nil="false">
              <e13:EstimatedPositionAndTraffic>
                <e13:MatchType></e13:MatchType>
                <e13:MinClicksPerWeek></e13:MinClicksPerWeek>
                <e13:MaxClicksPerWeek></e13:MaxClicksPerWeek>
                <e13:AverageCPC></e13:AverageCPC>
                <e13:MinImpressionsPerWeek></e13:MinImpressionsPerWeek>
                <e13:MaxImpressionsPerWeek></e13:MaxImpressionsPerWeek>
                <e13:CTR></e13:CTR>
                <e13:MinTotalCostPerWeek></e13:MinTotalCostPerWeek>
                <e13:MaxTotalCostPerWeek></e13:MaxTotalCostPerWeek>
                <e13:Currency></e13:Currency>
                <e13:EstimatedAdPosition></e13:EstimatedAdPosition>
              </e13:EstimatedPositionAndTraffic>
            </e13:EstimatedPositions>
          </e13:KeywordEstimatedPosition>
        </e13:KeywordIdEstimatedPosition>
      </KeywordEstimatedPositions>
    </GetEstimatedPositionByKeywordIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
