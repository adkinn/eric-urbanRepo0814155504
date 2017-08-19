---
title: "GetKeywordTrafficEstimates Service Operation"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 391b3880-faa7-4d63-9d4e-b3a122a49606
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetKeywordTrafficEstimates Service Operation
Provides traffic estimates for keywords e.g., average CPC, average position, clicks, CTR, impressions, and total cost. As input you provide the bid, language, location, and network, with optional campaign budget and negative keyword filters.

[!INCLUDE[adint_navigation_noremarks](../adinsight-api/includes/adint-navigation-noremarks.md)]

## <a name="request"></a>GetKeywordTrafficEstimatesRequest Message

### Request Body
The *GetKeywordTrafficEstimatesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*CampaignEstimators*|Defines your campaign, ad group, and keyword level criteria and filters for the requested keyword traffic estimates.|[CampaignEstimator](../adinsight-api/campaignestimator-data-object.md) array|Required|

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
    <Action mustUnderstand="1">GetKeywordTrafficEstimates</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetKeywordTrafficEstimatesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <CampaignEstimators xmlns:e32="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" i:nil="false">
        <e32:CampaignEstimator>
          <e32:AdGroupEstimators i:nil="false">
            <e32:AdGroupEstimator>
              <e32:AdGroupId i:nil="false"></e32:AdGroupId>
              <e32:KeywordEstimators i:nil="false">
                <e32:KeywordEstimator>
                  <Keyword xmlns:e33="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" i:nil="false">
                    <e33:Id i:nil="false"></e33:Id>
                    <e33:MatchType></e33:MatchType>
                    <e33:Text i:nil="false"></e33:Text>
                  </Keyword>
                  <e32:MaxCpc i:nil="false"></e32:MaxCpc>
                </e32:KeywordEstimator>
              </e32:KeywordEstimators>
              <e32:MaxCpc></e32:MaxCpc>
            </e32:AdGroupEstimator>
          </e32:AdGroupEstimators>
          <e32:CampaignId i:nil="false"></e32:CampaignId>
          <Criteria xmlns:e34="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" i:nil="false">
            <e34:Criterion i:type="-- specify derived type here with the appropriate prefix --">
              <!--Keep these fields if you set the i:type attribute to LocationCriterion-->
              <e34:LocationId></e34:LocationId>
              <!--Keep these fields if you set the i:type attribute to LanguageCriterion-->
              <e34:Language i:nil="false"></e34:Language>
              <!--Keep these fields if you set the i:type attribute to NetworkCriterion-->
              <e34:Network></e34:Network>
              <!--Keep these fields if you set the i:type attribute to DeviceCriterion-->
              <e34:DeviceName i:nil="false"></e34:DeviceName>
            </e34:Criterion>
          </Criteria>
          <e32:DailyBudget i:nil="false"></e32:DailyBudget>
          <NegativeKeywords xmlns:e35="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" i:nil="false">
            <e35:NegativeKeyword>
              <e35:Id i:nil="false"></e35:Id>
              <e35:MatchType></e35:MatchType>
              <e35:Text i:nil="false"></e35:Text>
            </e35:NegativeKeyword>
          </NegativeKeywords>
        </e32:CampaignEstimator>
      </CampaignEstimators>
    </GetKeywordTrafficEstimatesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetKeywordTrafficEstimatesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*CampaignEstimates*|The list of campaign estimates. Within each campaign estimate is a nested list of keyword traffic estimates for each ad group.|[CampaignEstimate](../adinsight-api/campaignestimate-data-object.md) array|

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
    <GetKeywordTrafficEstimatesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <CampaignEstimates xmlns:e36="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e36:CampaignEstimate>
          <e36:AdGroupEstimates p5:nil="false">
            <e36:AdGroupEstimate>
              <e36:AdGroupId p5:nil="false"></e36:AdGroupId>
              <e36:KeywordEstimates p5:nil="false">
                <e36:KeywordEstimate>
                  <Keyword xmlns:e37="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" p5:nil="false">
                    <e37:Id p5:nil="false"></e37:Id>
                    <e37:MatchType></e37:MatchType>
                    <e37:Text p5:nil="false"></e37:Text>
                  </Keyword>
                  <e36:Maximum p5:nil="false">
                    <e36:AverageCpc></e36:AverageCpc>
                    <e36:AveragePosition></e36:AveragePosition>
                    <e36:Clicks></e36:Clicks>
                    <e36:Ctr></e36:Ctr>
                    <e36:Impressions></e36:Impressions>
                    <e36:TotalCost></e36:TotalCost>
                  </e36:Maximum>
                  <e36:Minimum p5:nil="false">
                    <e36:AverageCpc></e36:AverageCpc>
                    <e36:AveragePosition></e36:AveragePosition>
                    <e36:Clicks></e36:Clicks>
                    <e36:Ctr></e36:Ctr>
                    <e36:Impressions></e36:Impressions>
                    <e36:TotalCost></e36:TotalCost>
                  </e36:Minimum>
                </e36:KeywordEstimate>
              </e36:KeywordEstimates>
            </e36:AdGroupEstimate>
          </e36:AdGroupEstimates>
          <e36:CampaignId p5:nil="false"></e36:CampaignId>
        </e36:CampaignEstimate>
      </CampaignEstimates>
    </GetKeywordTrafficEstimatesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
