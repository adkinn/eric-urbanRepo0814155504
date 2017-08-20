---
title: "GetBidOpportunities Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb61e4cc-4f38-4442-995a-e5ce0663e56d
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBidOpportunities Service Operation
Gets the keyword bid opportunities of the specified ad group.

> [!NOTE]
> Currently bid opportunities are only available in the United States. It is not recommended to use this service operation for accounts in other markets.

||
|-|
|[!INCLUDE[adint_navigation_noremarks](../adinsight-api/includes/adint-navigation-noremarks.md)]|

## <a name="request"></a>GetBidOpportunitiesRequest Message

### Request Body
The *GetBidOpportunitiesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupId*|The identifier of the ad group for which you want to determine keyword bid opportunities.<br /><br />If this element is nil or empty, the operation will return all bid opportunities for the specified campaign.|*long*|No|
|*CampaignId*|The identifier of the campaign that owns the ad group specified in the *AdGroupId* element.<br /><br />If this element is nil or empty, then the *AdGroupId* must also be nil or empty, and the operation will return all bid opportunities for the account.|*long*|No|
|*OpportunityType*|Determines the type or types of bid opportunities corresponding to your ad position goals.<br /><br />**Note:** The operation will only return opportunities if there’s a suggested increase within 100% of your current bid that will help you achieve the specified goal.|[BidOpportunityType](../adinsight-api/bidopportunitytype-value-set.md)|Yes|

### Request Headers
[!INCLUDE[header_intro](../adinsight-api/includes/header-intro.md)]
#### OAuth Authentication
[!INCLUDE[adint_header_oauth](../adinsight-api/includes/adint-header-oauth.md)]
#### Password Authentication
[!INCLUDE[adint_header_password](../adinsight-api/includes/adint-header-password.md)]
### <a name="request_soap"></a>Request SOAP
The following example shows the complete request envelope.

```xml
\<s:Envelope xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    <Action mustUnderstand="1">GetBidOpportunities</Action>
    \<ApplicationToken i:nil="false"></ApplicationToken>
    \<AuthenticationToken i:nil="false"></AuthenticationToken>
    \<CustomerAccountId i:nil="false"></CustomerAccountId>
    \<CustomerId i:nil="false"></CustomerId>
    \<DeveloperToken i:nil="false"></DeveloperToken>
    \<Password i:nil="false"></Password>
    \<UserName i:nil="false"></UserName>
  \</s:Header>
  \<s:Body>
    <GetBidOpportunitiesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<AdGroupId i:nil="false"></AdGroupId>
      \<CampaignId i:nil="false"></CampaignId>
      <OpportunityType></OpportunityType>
    </GetBidOpportunitiesRequest>
  \</s:Body>
\</s:Envelope>
```

## <a name="response"></a>GetBidOpportunitiesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Opportunities*|An array of *BidOpportunity* objects that identifies the keywords whose clicks and impressions may increase if you were to apply the suggested match-type bid value.<br /><br />Up to 500 opportunities of each *OpportunityType* will be returned for the account.|[BidOpportunity](../adinsight-api/bidopportunity-data-object.md) array|

### <a name="Header_Elements"></a>Response Header
[!INCLUDE[adint_response_header_table](../adinsight-api/includes/adint-response-header-table.md)]
### Response SOAP
The following example shows the complete response envelope.

```xml
\<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  \<s:Header xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
    \<TrackingId p4:nil="false" xmlns:p4="http://www.w3.org/2001/XMLSchema-instance"></TrackingId>
  \</s:Header>
  \<s:Body>
    <GetBidOpportunitiesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      \<Opportunities xmlns:e6="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        \<e6:BidOpportunity>
          \<e6:AdGroupId>\</e6:AdGroupId>
          \<e6:CampaignId>\</e6:CampaignId>
          \<e6:CurrentBid>\</e6:CurrentBid>
          \<e6:EstimatedIncreaseInClicks>\</e6:EstimatedIncreaseInClicks>
          \<e6:EstimatedIncreaseInCost>\</e6:EstimatedIncreaseInCost>
          \<e6:EstimatedIncreaseInImpressions>\</e6:EstimatedIncreaseInImpressions>
          \<e6:KeywordId>\</e6:KeywordId>
          \<e6:MatchType p5:nil="false">\</e6:MatchType>
          \<e6:SuggestedBid>\</e6:SuggestedBid>
        \</e6:BidOpportunity>
      </Opportunities>
    </GetBidOpportunitiesResponse>
  \</s:Body>
\</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
