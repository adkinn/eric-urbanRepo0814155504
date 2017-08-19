---
title: "GetBidLandscapeByKeywordIds Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66989d51-8c17-44da-bd31-9d30fc4e83c9
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBidLandscapeByKeywordIds Service Operation
Given a list of existing keywords, this operation returns for each a list of suggested bids and estimated performance statistics from 1 to  7 days. This operation is not based on target position, rather it returns multiple bid options that yield different estimated clicks, impressions, and cost. You can use the landscape view of multiple bid points with estimated traffic for the same keyword to help make decisions about how to adjust your keyword bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve.

> [!NOTE]
> The estimates are based on the last 7 days of performance data, and not a prediction or guarantee of future performance.

[!INCLUDE[adint-service-namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetBidLandscapeByKeywordIdsRequest Message

### Request Body
The *GetBidLandscapeByKeywordIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*KeywordIds*|An array of identifiers of the keywords for which you want to get the list of suggested bid values with estimated performance statistics.<br /><br />You may specify a maximum of 1,000 keywords.|*long* array|Yes|
|*IncludeCurrentBid*|When set to **false**, the suggested bid values might not include the keyword's current bid. The default value is **false**.<br /><br />When set to **true**, one of the suggested bid values will be equal to the keyword's current bid.|*boolean*|No|

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
    <Action mustUnderstand="1">GetBidLandscapeByKeywordIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBidLandscapeByKeywordIdsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordIds i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:long></a1:long>
      </KeywordIds>
      <IncludeCurrentBid i:nil="false"></IncludeCurrentBid>
    </GetBidLandscapeByKeywordIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBidLandscapeByKeywordIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BidLandscape*|An array of *KeywordBidLandscape* objects. The array contains a *KeywordBidLandscape* corresponding to each keyword specified in the request.  Duplicate keyword identifiers are allowed in the same call and will return the same results.<br /><br />If the specified keyword identifier is invalid or has no associated data results, all elements within the *KeywordBidLandscape* will be nil except the *KeywordId* which reflects the keyword identifier specified in the request.<br /><br />If there is data available for the keyword, the *KeywordBidLandscape* object will provide a list of suggested bids and estimated performance statistics.|[KeywordBidLandscape](../adinsight-api/keywordbidlandscape-data-object.md) array|

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
    <GetBidLandscapeByKeywordIdsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <BidLandscape xmlns:e5="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e5:KeywordBidLandscape>
          <e5:KeywordId></e5:KeywordId>
          <e5:StartDate p5:nil="false">
            <e5:Day></e5:Day>
            <e5:Month></e5:Month>
            <e5:Year></e5:Year>
          </e5:StartDate>
          <e5:EndDate p5:nil="false">
            <e5:Day></e5:Day>
            <e5:Month></e5:Month>
            <e5:Year></e5:Year>
          </e5:EndDate>
          <e5:BidLandscapePoints p5:nil="false">
            <e5:BidLandscapePoint>
              <e5:Bid></e5:Bid>
              <e5:Clicks p5:nil="false"></e5:Clicks>
              <e5:Impressions></e5:Impressions>
              <e5:TopImpressions p5:nil="false"></e5:TopImpressions>
              <e5:Currency></e5:Currency>
              <e5:Cost p5:nil="false"></e5:Cost>
              <e5:MarginalCPC p5:nil="false"></e5:MarginalCPC>
            </e5:BidLandscapePoint>
          </e5:BidLandscapePoints>
        </e5:KeywordBidLandscape>
      </BidLandscape>
    </GetBidLandscapeByKeywordIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
|CampaignServiceKeywordIdsArrayShouldNotBeNullOrEmpty|
|CampaignServiceKeywordsArrayExceedsLimit|
