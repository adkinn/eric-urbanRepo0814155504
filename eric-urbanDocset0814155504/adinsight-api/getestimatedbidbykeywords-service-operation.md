---
title: "GetEstimatedBidByKeywords Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9fcf4632-445c-4d10-aa50-ad87ddd1a2f9
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetEstimatedBidByKeywords Service Operation
Gets the estimated bid value of one or more keywords that could result in an ad appearing in the targeted position in the search results.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetEstimatedBidByKeywordsRequest Message

### Request Body
The *GetEstimatedBidByKeywordsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupId*|The identifier of the ad group whose performance data is used to help determine how well the keyword might perform in the context of the ad group. Specifying an ad group helps improve the accuracy of the suggested bid.<br /><br />If you specify an ad group, you must specify the campaign that it belongs to.|*long*|No|
|*CampaignId*|The identifier of the campaign that owns the ad group specified in *AdGroupId*. If you do not specify an ad group, the campaign’s performance data is used to help determine how well the keyword might perform in the context of the campaign.<br /><br />**Note:** Specifying a campaign and ad group helps improve the accuracy of the suggested bid. If neither *AdGroupId* or *CampaignId* are specified, the operation uses the specified *CustomerAccountId* header element to help determine how well the keyword might perform in the context of the account.|*long*|No|
|*Currency*|The monetary unit to use to calculate the cost estimates and suggested bid value.<br /><br />If not set, the service determines the currency from the account specified in the *CustomerAccountId* header element. If neither *Currency* or  *CustomerAccountId* is set, the service uses USDollar.|[Currency](../adinsight-api/currency-value-set.md)|No|
|*EntityLevelBid*|Determines whether to return estimates for keyword level bids, ad group level bids, or both.<br /><br />- Set *EntityLevelBid* to Keyword to get an array of [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md) corresponding to the specified keywords.<br /><br />- Set *EntityLevelBid* to AdGroup to get one [EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md) for the specified ad group.<br /><br />- Set *EntityLevelBid* to AllEntities to get an array of [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md) for keywords and one [EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md) for an ad group.<br /><br />If you do not set *EntityLevelBid*, the default is to return only an array of [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md), or the equivalent of setting *EntityLevelBid* to Keyword.<br /><br />If you set *EntityLevelBid* to any value other thanKeyword, AdGroup, or AllEntities, the service will return *Code 3501* with *ErrorCode CampaignServiceBidLevelInvalid*.|*string*|No|
|*Keywords*|A list of [KeywordAndMatchType](../adinsight-api/keywordandmatchtype-data-object.md) data objects for which you want to get suggested bid values. You may specify a maximum of 1,000 keywords, and each keyword can contain a maximum of 100 characters.|[KeywordAndMatchType](../adinsight-api/keywordandmatchtype-data-object.md) array|Yes|
|*Language*|The language used to help determine  the country to use as the source of data for estimating the bids, if the *PublisherCountries* element is not specified.<br /><br />**Note:** The language must be supported in each of the countries in the *PublisherCountries* element.<br /><br />For possible values and information about the relationship between languages and countries, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).<br /><br />The default value is determined by the *PublisherCountries* element and the location targets associated with the specified *AdGroupId* and *CampaignId*. For more information, see the [Remarks](#remarks) section below.|*string*|No|
|*PublisherCountries*|The country codes of the countries to use as the source of data for estimating the bids.<br /><br />**Note:** All of the countries must support the language specified in the *Language* element.<br /><br />You may specify one or more country codes. For possible values, see [Geographical Location Codes](http://go.microsoft.com/fwlink/?LinkId=691115).<br /><br />The default value is determined by the *Language* element and the location targets associated with the specified *AdGroupId* and *CampaignId*. For more information, see the [Remarks](#remarks) section below.|*string* array|No|
|*TargetPositionForAds*|The position where you want your ads to appear in the search results.<br /><br />The default value is *MainLine1*.|[TargetAdPosition](../adinsight-api/targetadposition-value-set.md)|No|

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
    <Action mustUnderstand="1">GetEstimatedBidByKeywords</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetEstimatedBidByKeywordsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Keywords xmlns:e10="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Message" i:nil="false">
        <e10:KeywordAndMatchType>
          <e10:KeywordText i:nil="false"></e10:KeywordText>
          <e10:MatchTypes i:nil="false">
            <MatchType></MatchType>
          </e10:MatchTypes>
        </e10:KeywordAndMatchType>
      </Keywords>
      <TargetPositionForAds></TargetPositionForAds>
      <Language i:nil="false"></Language>
      <PublisherCountries i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </PublisherCountries>
      <Currency i:nil="false"></Currency>
      <CampaignId i:nil="false"></CampaignId>
      <AdGroupId i:nil="false"></AdGroupId>
      <EntityLevelBid i:nil="false"></EntityLevelBid>
    </GetEstimatedBidByKeywordsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetEstimatedBidByKeywordsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupEstimatedBid*|Contains estimates of clicks, average cost per click (CPC), impressions, click-through rate (CTR), and total cost for the specified ad group if you would use the suggested bid.<br /><br />**Note:** The *MatchType* value within the [EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md) will always be Aggregate. In this context, it represents the default search bid for an ad group.|[EstimatedBidAndTraffic](../adinsight-api/estimatedbidandtraffic-data-object.md)|
|*KeywordEstimatedBids*|An array of [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md) data objects. The array contains an item for each keyword specified in the request.  If the keyword is not valid, the corresponding item in the array will be null.<br /><br />Each [KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md) contains a keyword and *EstimatedPositions* element. If data is available for the keyword, the [EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md) will provide the suggested bid value that could have resulted in an ad appearing in the targeted position of the search results. Otherwise, the *EstimatedPositions* element will be set to null.|[KeywordEstimatedBid](../adinsight-api/keywordestimatedbid-data-object.md) array|

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
    <GetEstimatedBidByKeywordsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordEstimatedBids xmlns:e11="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e11:KeywordEstimatedBid>
          <e11:Keyword p5:nil="false"></e11:Keyword>
          <e11:EstimatedBids p5:nil="false">
            <e11:EstimatedBidAndTraffic>
              <e11:MinClicksPerWeek p5:nil="false"></e11:MinClicksPerWeek>
              <e11:MaxClicksPerWeek p5:nil="false"></e11:MaxClicksPerWeek>
              <e11:AverageCPC p5:nil="false"></e11:AverageCPC>
              <e11:MinImpressionsPerWeek p5:nil="false"></e11:MinImpressionsPerWeek>
              <e11:MaxImpressionsPerWeek p5:nil="false"></e11:MaxImpressionsPerWeek>
              <e11:CTR p5:nil="false"></e11:CTR>
              <e11:MinTotalCostPerWeek p5:nil="false"></e11:MinTotalCostPerWeek>
              <e11:MaxTotalCostPerWeek p5:nil="false"></e11:MaxTotalCostPerWeek>
              <e11:Currency></e11:Currency>
              <e11:MatchType></e11:MatchType>
              <e11:EstimatedMinBid></e11:EstimatedMinBid>
            </e11:EstimatedBidAndTraffic>
          </e11:EstimatedBids>
        </e11:KeywordEstimatedBid>
      </KeywordEstimatedBids>
      <AdGroupEstimatedBid xmlns:e12="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e12:MinClicksPerWeek p5:nil="false"></e12:MinClicksPerWeek>
        <e12:MaxClicksPerWeek p5:nil="false"></e12:MaxClicksPerWeek>
        <e12:AverageCPC p5:nil="false"></e12:AverageCPC>
        <e12:MinImpressionsPerWeek p5:nil="false"></e12:MinImpressionsPerWeek>
        <e12:MaxImpressionsPerWeek p5:nil="false"></e12:MaxImpressionsPerWeek>
        <e12:CTR p5:nil="false"></e12:CTR>
        <e12:MinTotalCostPerWeek p5:nil="false"></e12:MinTotalCostPerWeek>
        <e12:MaxTotalCostPerWeek p5:nil="false"></e12:MaxTotalCostPerWeek>
        <e12:Currency></e12:Currency>
        <e12:MatchType></e12:MatchType>
        <e12:EstimatedMinBid></e12:EstimatedMinBid>
      </AdGroupEstimatedBid>
    </GetEstimatedBidByKeywordsResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|

## <a name="remarks"></a>Remarks
As a best practice for the most accurate bid estimates per country, you should specify only one country per service call. If no countries are specified or if multiple *PublisherCountries* are specified, then the service will use the first available set of the following properties to determine  the country to use as the source of data for estimating the bids.

-   Multiple countries corresponding to this operation's specified *PublisherCountries* element.

-   The service will use the set of all supported countries for the specified *Language*, and join with common supported countries in the location target associated with the specified *AdGroupId*.

    > [!NOTE]
    > If the target countries conflict with the specified *Language*, then the service will disregard the target countries and only use the set of all supported countries for the specified *Language*.

-   The service will use the set of all supported countries for the specified *Language*, and join with common supported countries in the location target associated with the specified *CampaignId*.

    > [!NOTE]
    > If the target countries conflict with the specified *Language*, then the service will disregard the target countries and only use the set of all supported countries for the specified *Language*.

-   *Language* element of the [AdGroup](~/campaign-api/adgroup-data-object.md) corresponding to this operation's specified *AdGroupId* element. The service will use the set of all supported countries for this language.

Given multiple countries from one of the property sets above, the service will then determine one country with the highest impression count to use as the source of data for estimating the bids. The response will not include details on the final filtered country.

