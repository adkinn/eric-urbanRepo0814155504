---
title: "GetBudgetOpportunities"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1cad7317-7f04-4d8e-8584-99fc245c184d
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GetBudgetOpportunities Service Operation
Gets the campaign budget opportunities of the specified campaign.

[!INCLUDE[adint-service-namespace](../adinsight-api/includes/adint-service-namespace.md)]

## <a name="request"></a>GetBudgetOpportunitiesRequest Message

### Request Body
The *GetBudgetOpportunitiesRequest* object defines the elements of the request’s body. The elements must be in the same order as shown in the SOAP [Request SOAP](#request_soap).

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*CampaignId*|The identifier of the campaign for which you want to discover possible campaign budget opportunities.<br /><br />If this element is nil or empty, then the operation will return all budget opportunities for the account.|*long*|No|

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
    <Action mustUnderstand="1">GetBudgetOpportunities</Action>
    <ApplicationToken i:nil="false"></ApplicationToken>
    <AuthenticationToken i:nil="false"></AuthenticationToken>
    <CustomerAccountId i:nil="false"></CustomerAccountId>
    <CustomerId i:nil="false"></CustomerId>
    <DeveloperToken i:nil="false"></DeveloperToken>
    <Password i:nil="false"></Password>
    <UserName i:nil="false"></UserName>
  </s:Header>
  <s:Body>
    <GetBudgetOpportunitiesRequest xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <CampaignId i:nil="false"></CampaignId>
    </GetBudgetOpportunitiesRequest>
  </s:Body>
</s:Envelope>
```

## <a name="response"></a>GetBudgetOpportunitiesResponse Message

### <a name="Body_Elements"></a>Response Body

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Opportunities*|An array of [BudgetOpportunity](../adinsight-api/budgetopportunity-data-object.md) data objects that identify the campaigns whose clicks and impressions may increase if you were to apply the suggested budget.<br /><br />The list will not include opportunities for campaigns that are currently paused by the user.<br /><br />Up to 500 opportunities will be returned for the account.|[BudgetOpportunity](../adinsight-api/budgetopportunity-data-object.md) array|

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
    <GetBudgetOpportunitiesResponse xmlns="Microsoft.Advertiser.AdInsight.Api.Service.V11">
      <Opportunities xmlns:e7="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity" p5:nil="false" xmlns:p5="http://www.w3.org/2001/XMLSchema-instance">
        <e7:BudgetOpportunity>
          <e7:BudgetPoints p5:nil="false">
            <e7:BudgetPoint>
              <e7:BudgetAmount></e7:BudgetAmount>
              <e7:BudgetPointType></e7:BudgetPointType>
              <e7:EstimatedWeeklyClicks></e7:EstimatedWeeklyClicks>
              <e7:EstimatedWeeklyCost></e7:EstimatedWeeklyCost>
              <e7:EstimatedWeeklyImpressions></e7:EstimatedWeeklyImpressions>
            </e7:BudgetPoint>
          </e7:BudgetPoints>
          <e7:BudgetType></e7:BudgetType>
          <e7:CampaignId></e7:CampaignId>
          <e7:CurrentBudget></e7:CurrentBudget>
          <e7:IncreaseInClicks></e7:IncreaseInClicks>
          <e7:IncreaseInImpressions></e7:IncreaseInImpressions>
          <e7:PercentageIncreaseInClicks></e7:PercentageIncreaseInClicks>
          <e7:PercentageIncreaseInImpressions></e7:PercentageIncreaseInImpressions>
          <e7:RecommendedBudget></e7:RecommendedBudget>
        </e7:BudgetOpportunity>
      </Opportunities>
    </GetBudgetOpportunitiesResponse>
  </s:Body>
</s:Envelope>
```

## <a name="errors"></a>Error Codes
[!INCLUDE[adinterror](../adinsight-api/includes/adinterror.md)]The following are example  error codes that the error objects can include when using this service operation. For all documented error codes, please see [Bing Ads Operation Error Codes](http://go.microsoft.com/fwlink/?LinkId=511884).

|Error Code|
|--------------|
|InvalidCredentials|
