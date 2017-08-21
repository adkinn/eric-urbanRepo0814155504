---
title: "GetEstimatedPositionByKeywords Service Operation"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f829582a-815f-4a75-9116-8ece65fa3d4f
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetEstimatedPositionByKeywords Service Operation
Gets the estimated position in the search results if the specified bid value would be used for the specified keywords. In addition, the operation provides estimates of clicks, average cost per click (CPC), and impressions that the keywords could be generated with the estimated bid.

> [!NOTE]
> The estimates are not a prediction or guarantee of future performance.

[!INCLUDE[adint_service_namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetEstimatedPositionByKeywordsRequest Message

### Request Body
The *GetEstimatedPositionByKeywordsRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupId*|The identifier of the ad group whose performance data is used to help determine how well the keyword might perform in the context of the ad group. Specifying an ad group helps improve the accuracy of the suggested position.<br /><br />If you specify an ad group, you must specify the campaign that it belongs to.|*long*|No|
|*CampaignId*|The identifier of the campaign that owns the ad group specified in *AdGroupId*. If you do not specify an ad group, the campaign’s performance data is used to help determine how well the keyword might perform in the context of the campaign.<br /><br />**Note:** Specifying a campaign and ad group helps improve the accuracy of the suggested position. If neither *AdGroupId* or *CampaignId* are specified, the operation uses the specified *CustomerAccountId* header element to help determine how well the keyword might perform in the context of the account.|*long*|No|
|*Currency*|The monetary unit to use to calculate the cost estimates and suggested bid value.<br /><br />If not set, the service determines the currency from the account specified in the CustomerAccountId header element. If neither is set, the service uses USDollar.|[Currency](../adinsight-api/currency-value-set.md)|No|
|*Keywords*|An array of keywords for which you want to get the estimated position in the search results, based on the specified bid value. You may specify a maximum of 1,000 keywords and each keyword can contains a maximum of 100 characters.|*string* array|Yes|
|*Language*|The language used to help determine  the country to use as the source of data for estimating the bids, if the *PublisherCountries* element is not specified.<br /><br />**Note:** The language must be supported in each of the countries in the *PublisherCountries* element.<br /><br />For possible values and information about the relationship between languages and countries, see [Ad Languages](http://go.microsoft.com/fwlink/?LinkId=691113).<br /><br />The default value is determined by the *PublisherCountries* element and the location targets associated with the specified *AdGroupId* and *CampaignId*. For more information, see the [Remarks](#remarks) section below.|*string*|No|
|*MatchTypes*|An array of unique match types for which you want to get estimates.<br /><br />You may not specify the Content match type.|[MatchType](../adinsight-api/matchtype-value-set.md) array|Yes|
|*MaxBid*|The maximum bid value to use to determine the estimated position in the search results.|*double*|Yes|
|*PublisherCountries*|The country codes of the countries to use as the source of data for estimating the bids.<br /><br />**Note:** All of the countries must support the language specified in the *Language* element.<br /><br />You may specify one or more country codes. For possible values, see [Geographical Location Codes](http://go.microsoft.com/fwlink/?LinkId=691115).<br /><br />The default value is determined by the *Language* element and the location targets associated with the specified *AdGroupId* and *CampaignId*. For more information, see the [Remarks](#remarks) section below.|*string* array|No|

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
    <Action mustUnderstand="1">GetEstimatedPositionByKeywords</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetEstimatedPositionByKeywordsRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Keywords i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </Keywords>
      <MaxBid></MaxBid>
      <Language i:nil="false"></Language>
      <PublisherCountries i:nil="false" xmlns:a1="http://schemas.microsoft.com/2003/10/Serialization/Arrays">
        <a1:string></a1:string>
      </PublisherCountries>
      <Currency i:nil="false"></Currency>
      <MatchTypes i:nil="false">
        <MatchType></MatchType>
      </MatchTypes>
      <CampaignId i:nil="false"></CampaignId>
      <AdGroupId i:nil="false"></AdGroupId>
    </GetEstimatedPositionByKeywordsRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetEstimatedPositionByKeywordsResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*KeywordEstimatedPositions*|An array of [KeywordEstimatedPosition](../adinsight-api/keywordestimatedposition-data-object.md) data objects. The array contains an item for each keyword specified in the request. If the keyword is not valid, the corresponding item in the array will be null.<br /><br />If data is available for the keyword, the [EstimatedPositionAndTraffic](../adinsight-api/estimatedpositionandtraffic-data-object.md)  will provide the estimated position in the search results where your ads could appear, based on the specified bid value. Otherwise, the *EstimatedPositions* element will be set to null.|[KeywordEstimatedPosition](../adinsight-api/keywordestimatedposition-data-object.md) array|

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
    <GetEstimatedPositionByKeywordsResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <KeywordEstimatedPositions xmlns:e14="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e14:KeywordEstimatedPosition>
          <e14:Keyword p5:nil="false"></e14:Keyword>
          <e14:EstimatedPositions p5:nil="false">
            <e14:EstimatedPositionAndTraffic>
              <e14:MatchType></e14:MatchType>
              <e14:MinClicksPerWeek></e14:MinClicksPerWeek>
              <e14:MaxClicksPerWeek></e14:MaxClicksPerWeek>
              <e14:AverageCPC></e14:AverageCPC>
              <e14:MinImpressionsPerWeek></e14:MinImpressionsPerWeek>
              <e14:MaxImpressionsPerWeek></e14:MaxImpressionsPerWeek>
              <e14:CTR></e14:CTR>
              <e14:MinTotalCostPerWeek></e14:MinTotalCostPerWeek>
              <e14:MaxTotalCostPerWeek></e14:MaxTotalCostPerWeek>
              <e14:Currency></e14:Currency>
              <e14:EstimatedAdPosition></e14:EstimatedAdPosition>
            </e14:EstimatedPositionAndTraffic>
          </e14:EstimatedPositions>
        </e14:KeywordEstimatedPosition>
      </KeywordEstimatedPositions>
    </GetEstimatedPositionByKeywordsResponse>
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

