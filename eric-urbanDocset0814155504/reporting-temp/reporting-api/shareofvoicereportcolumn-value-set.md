---
title: "ShareOfVoiceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfdf110a-f9c1-411f-b78e-465c90162f4b
caps.latest.revision: 9
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ShareOfVoiceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [ShareOfVoiceReportRequest](../reporting-api/shareofvoicereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
\<xs:simpleType name="ShareOfVoiceReportColumn">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="AccountName" />
    \<xs:enumeration value="TimePeriod" />
    \<xs:enumeration value="CampaignName" />
    \<xs:enumeration value="AdGroupName" />
    \<xs:enumeration value="Keyword" />
    \<xs:enumeration value="DeliveredMatchType" />
    \<xs:enumeration value="BidMatchType" />
    \<xs:enumeration value="Language" />
    \<xs:enumeration value="AccountNumber" />
    \<xs:enumeration value="AccountId" />
    \<xs:enumeration value="KeywordId" />
    \<xs:enumeration value="AdGroupId" />
    \<xs:enumeration value="CampaignId" />
    \<xs:enumeration value="Impressions" />
    \<xs:enumeration value="Clicks" />
    \<xs:enumeration value="Ctr" />
    \<xs:enumeration value="AverageCpc" />
    \<xs:enumeration value="Spend" />
    \<xs:enumeration value="AveragePosition" />
    \<xs:enumeration value="ImpressionSharePercent" />
    \<xs:enumeration value="ImpressionLostToBudgetPercent" />
    \<xs:enumeration value="ImpressionLostToRankPercent" />
    \<xs:enumeration value="ImpressionLostToAdRelevancePercent" />
    \<xs:enumeration value="ImpressionLostToExpectedCtrPercent" />
    \<xs:enumeration value="ImpressionLostToRelevancePercent" />
    \<xs:enumeration value="ImpressionLostToBidPercent" />
    \<xs:enumeration value="CurrentMaxCpc" />
    \<xs:enumeration value="QualityScore" />
    \<xs:enumeration value="ExpectedCtr" />
    \<xs:enumeration value="AdRelevance" />
    \<xs:enumeration value="LandingPageExperience" />
    \<xs:enumeration value="Conversions" />
    \<xs:enumeration value="ConversionRate" />
    \<xs:enumeration value="CostPerConversion" />
    \<xs:enumeration value="AdDistribution" />
    \<xs:enumeration value="ClickSharePercent" />
    \<xs:enumeration value="DeviceType" />
    \<xs:enumeration value="Network"/>
    \<xs:enumeration value="AccountStatus"/>
    \<xs:enumeration value="CampaignStatus"/>
    \<xs:enumeration value="AdGroupStatus"/>
    \<xs:enumeration value="KeywordStatus"/>
    \<xs:enumeration value="BidStrategyType"/>
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AccountStatus|[!INCLUDE[reportcolumn_accountstatus](../reporting-api/includes/reportcolumn-accountstatus.md)]|
|AdDistribution|[!INCLUDE[reportcolumn_addistribution](../reporting-api/includes/reportcolumn-addistribution.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AdRelevance|[!INCLUDE[reportcolumn_adrelevance](../reporting-api/includes/reportcolumn-adrelevance.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|BidMatchType|[!INCLUDE[reportcolumn_bidmatchtype](../reporting-api/includes/reportcolumn-bidmatchtype.md)]|
|BidStrategyType|[!INCLUDE[reportcolumn_bidstrategytype](../reporting-api/includes/reportcolumn-bidstrategytype.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ClickSharePercent|The percentage of clicks that went to your ads. It is the share of the prospective customer's mindshare and buying intent you captured.<br/><br/>**Note:** For Reporting API version 11, the column name in the downloaded report is *ClickSharePct*, not *ClickSharePercent* as defined by the Reporting service. In Reporting API version 12 the column header will be updated to match the Reporting service definition.|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CurrentMaxCpc|[!INCLUDE[reportcolumn_currentmaxcpc](../reporting-api/includes/reportcolumn-currentmaxcpc.md)]|
|DeliveredMatchType|[!INCLUDE[reportcolumn_deliveredmatchtype](../reporting-api/includes/reportcolumn-deliveredmatchtype.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|ExpectedCtr|[!INCLUDE[reportcolumn_expectedctr](../reporting-api/includes/reportcolumn-expectedctr.md)]|
|ImpressionLostToAdRelevancePercent|[!INCLUDE[reportcolumn_impressionlosttoadrelevancepercent](../reporting-api/includes/reportcolumn-impressionlosttoadrelevancepercent.md)]|
|ImpressionLostToBidPercent|[!INCLUDE[reportcolumn_impressionlosttobidpercent](../reporting-api/includes/reportcolumn-impressionlosttobidpercent.md)]|
|ImpressionLostToBudgetPercent|[!INCLUDE[reportcolumn_impressionlosttobudgetpercent](../reporting-api/includes/reportcolumn-impressionlosttobudgetpercent.md)]|
|ImpressionLostToExpectedCtrPercent|[!INCLUDE[reportcolumn_impressionlosttoexpectedctrpercent](../reporting-api/includes/reportcolumn-impressionlosttoexpectedctrpercent.md)]|
|ImpressionLostToRankPercent|[!INCLUDE[reportcolumn_impressionlosttorankpercent](../reporting-api/includes/reportcolumn-impressionlosttorankpercent.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|ImpressionSharePercent|[!INCLUDE[reportcolumn_impressionsharepercent](../reporting-api/includes/reportcolumn-impressionsharepercent.md)]|
|Keyword|[!INCLUDE[reportcolumn_keyword](../reporting-api/includes/reportcolumn-keyword.md)]|
|KeywordId|[!INCLUDE[reportcolumn_keywordid](../reporting-api/includes/reportcolumn-keywordid.md)]<br /><br />**IMPORTANT**: If *KeywordId* is not specified the report will not fail, but impression share data will be inaccurate unless *KeywordId* is specified.|
|KeywordStatus|[!INCLUDE[reportcolumn_keywordstatus](../reporting-api/includes/reportcolumn-keywordstatus.md)]|
|LandingPageExperience|[!INCLUDE[reportcolumn_landingpageexperience](../reporting-api/includes/reportcolumn-landingpageexperience.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|QualityScore|[!INCLUDE[reportcolumn_qualityscore](../reporting-api/includes/reportcolumn-qualityscore.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|ImpressionSharePercent|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types *except* Summary.|
|KeywordId<br /><br />**IMPORTANT**: If *KeywordId* is not specified the report will not fail, but impression share data will be inaccurate unless *KeywordId* is specified.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ShareOfVoiceReportRequest](../reporting-api/shareofvoicereportrequest-data-object.md)

