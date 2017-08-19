---
title: "GetKeywordOpportunities Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b6ef9a22-d068-46d0-b9ca-34cc83bbc216
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordOpportunities Service Operation
Gets a list of keyword suggestions that are relevant to the specified ad group. The keyword suggestion also includes a suggested bid value.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetKeywordOpportunitiesRequest Message

### Request Body
The *GetKeywordOpportunitiesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupId*|The identifier of the ad group to get keyword suggestions for.<br /><br />The following restrictions apply to the specified ad group:<br /><br />- Its language must be set to English.<br /><br />- Its distribution medium must include Search.<br /><br />- It should contain keywords and ads. The operation will suggest keywords only if the ad group contains one or more ads and keywords; the more keywords and ads that the ad group contains, the richer the set of suggested keywords will be.<br /><br />If *AdGroupId* is nil or empty, the operation will return all keyword opportunities for the specified campaign.|*long*|No|
|*CampaignId*|The identifier of the campaign that owns the specified ad group.<br /><br />If the *CampaignId* element is nil or empty, then the *AdGroupId* must also be nil or empty, and the operation will return all keyword opportunities for the account.|*long*|No|
|*OpportunityType*|Determines the type or types of keyword opportunities that you want.|[KeywordOpportunityType](../adinsight-api/keywordopportunitytype-value-set.md)|Yes|

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
    <Action mustUnderstand="1">GetKeywordOpportunities</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetKeywordOpportunitiesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <AdGroupId i:nil="false"></AdGroupId>
      <CampaignId i:nil="false"></CampaignId>
      <OpportunityType></OpportunityType>
    </GetKeywordOpportunitiesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetKeywordOpportunitiesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Opportunities*|A list of [KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md) data objects that identifies a suggested keyword and bid value. The list will be empty if there are no suggestions, which may occur if the ad group does not contain existing ads and keywords.<br /><br />Up to 500 opportunities of each *OpportunityType* will be returned for the account.|[KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md) array|

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
    <GetKeywordOpportunitiesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Opportunities xmlns:e31="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e31:KeywordOpportunity p5:type="-- specify derived type here with the appropriate prefix --">
          <e31:AdGroupId></e31:AdGroupId>
          <e31:AdGroupName p5:nil="false"></e31:AdGroupName>
          <e31:CampaignId></e31:CampaignId>
          <e31:CampaignName p5:nil="false"></e31:CampaignName>
          <e31:Competition></e31:Competition>
          <e31:EstimatedIncreaseInClicks></e31:EstimatedIncreaseInClicks>
          <e31:EstimatedIncreaseInCost></e31:EstimatedIncreaseInCost>
          <e31:EstimatedIncreaseInImpressions></e31:EstimatedIncreaseInImpressions>
          <e31:MatchType></e31:MatchType>
          <e31:MonthlySearches></e31:MonthlySearches>
          <e31:SuggestedBid></e31:SuggestedBid>
          <e31:SuggestedKeyword p5:nil="false"></e31:SuggestedKeyword>
          <!--Keep these fields if you set the i:type attribute to BroadMatchKeywordOpportunity-->
          <e31:AverageCPC></e31:AverageCPC>
          <e31:AverageCTR></e31:AverageCTR>
          <e31:ClickShare></e31:ClickShare>
          <e31:ImpressionShare></e31:ImpressionShare>
          <e31:ReferenceKeywordBid></e31:ReferenceKeywordBid>
          <e31:ReferenceKeywordId></e31:ReferenceKeywordId>
          <e31:ReferenceKeywordMatchType></e31:ReferenceKeywordMatchType>
          <e31:SearchQueryKPIs p5:nil="false">
            <e31:BroadMatchSearchQueryKPI>
              <e31:AverageCTR></e31:AverageCTR>
              <e31:Clicks></e31:Clicks>
              <e31:Impressions></e31:Impressions>
              <e31:SRPV></e31:SRPV>
              <e31:SearchQuery p5:nil="false"></e31:SearchQuery>
            </e31:BroadMatchSearchQueryKPI>
          </e31:SearchQueryKPIs>
        </e31:KeywordOpportunity>
      </Opportunities>
    </GetKeywordOpportunitiesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
