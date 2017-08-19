---
title: "GetBidLandscapeByAdGroupIds Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fbd131e6-2ebe-4ad0-a5b3-74e09b99dbb8
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBidLandscapeByAdGroupIds Service Operation
Given a list of existing ad groups, this operation returns for each a list of suggested bids and estimated performance statistics. You can use the landscape view of multiple bid points with estimated traffic for the same ad group to help make decisions about how to adjust your ad group level default bid to optimize for clicks, impressions, and cost. For example you might use the resulting data to visualize a clicks to cost curve or a bid to impressions curve.

> [!NOTE]
> The estimates are based on the last 7 days of performance data, and not a prediction or guarantee of future performance.

[!INCLUDE[adint-service-namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetBidLandscapeByAdGroupIdsRequest Message

### Request Body
The *GetBidLandscapeByAdGroupIdsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupBidLandscapeInputs*|An array of ad group identifiers with corresponding bid landscape type input. A list of suggested bid values with estimated performance statistics will be returned for each input.<br /><br />You may specify a maximum of 1,000 input elements.|[AdGroupBidLandscapeInput](../adinsight-api/adgroupbidlandscapeinput-data-object.md) array|Yes|

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
    <Action mustUnderstand="1">GetBidLandscapeByAdGroupIds</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBidLandscapeByAdGroupIdsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <AdGroupBidLandscapeInputs xmlns:e3="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" i:nil="false">
        <e3:AdGroupBidLandscapeInput>
          <e3:AdGroupBidLandscapeType></e3:AdGroupBidLandscapeType>
          <e3:AdGroupId></e3:AdGroupId>
        </e3:AdGroupBidLandscapeInput>
      </AdGroupBidLandscapeInputs>
    </GetBidLandscapeByAdGroupIdsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBidLandscapeByAdGroupIdsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*BidLandscape*|An array of *AdGroupBidLandscape* objects. The array contains a *AdGroupBidLandscape* corresponding to each ad group and bid landscape type input specified in the request.  Duplicate input are allowed in the same call and will return the same results.<br /><br />If the specified input is invalid or has no associated data results, all elements within the *AdGroupBidLandscape* will be nil except the *AdGroupId* which reflects the ad group identifier specified in the request.<br /><br />If there is data available for the ad group, the *AdGroupBidLandscape* object will provide a list of suggested bids and estimated performance statistics.|[AdGroupBidLandscape](../adinsight-api/adgroupbidlandscape-data-object.md) array|

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
    <GetBidLandscapeByAdGroupIdsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <BidLandscape xmlns:e4="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e4:AdGroupBidLandscape>
          <e4:AdGroupId></e4:AdGroupId>
          <e4:AdGroupBidLandscapeType></e4:AdGroupBidLandscapeType>
          <e4:StartDate p5:nil="false">
            <e4:Day></e4:Day>
            <e4:Month></e4:Month>
            <e4:Year></e4:Year>
          </e4:StartDate>
          <e4:EndDate p5:nil="false">
            <e4:Day></e4:Day>
            <e4:Month></e4:Month>
            <e4:Year></e4:Year>
          </e4:EndDate>
          <e4:BidLandscapePoints p5:nil="false">
            <e4:BidLandscapePoint>
              <e4:Bid></e4:Bid>
              <e4:Clicks p5:nil="false"></e4:Clicks>
              <e4:Impressions></e4:Impressions>
              <e4:TopImpressions p5:nil="false"></e4:TopImpressions>
              <e4:Currency></e4:Currency>
              <e4:Cost p5:nil="false"></e4:Cost>
              <e4:MarginalCPC p5:nil="false"></e4:MarginalCPC>
            </e4:BidLandscapePoint>
          </e4:BidLandscapePoints>
        </e4:AdGroupBidLandscape>
      </BidLandscape>
    </GetBidLandscapeByAdGroupIdsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).


|Error Code|
|--------------|
|InvalidCredentials|
