---
title: "UserLocationPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 65440e69-523e-465c-a20d-d5bc0a03faa8
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UserLocationPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [UserLocationPerformanceReportRequest](../reporting-api/userlocationperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="UserLocationPerformanceReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="AccountName"/>
    <xs:enumeration value="AccountNumber"/>
    <xs:enumeration value="AccountId"/>
    <xs:enumeration value="TimePeriod"/>
    <xs:enumeration value="CampaignName"/>
    <xs:enumeration value="CampaignId"/>
    <xs:enumeration value="AdGroupName"/>
    <xs:enumeration value="AdGroupId"/>
    <xs:enumeration value="Country"/>
    <xs:enumeration value="State"/>
    <xs:enumeration value="MetroArea"/>
    <xs:enumeration value="CurrencyCode"/>
    <xs:enumeration value="AdDistribution"/>
    <xs:enumeration value="Impressions"/>
    <xs:enumeration value="Clicks"/>
    <xs:enumeration value="Ctr"/>
    <xs:enumeration value="AverageCpc"/>
    <xs:enumeration value="Spend"/>
    <xs:enumeration value="AveragePosition"/>
    <xs:enumeration value="ProximityTargetLocation" />
    <xs:enumeration value="Radius" />
    <xs:enumeration value="Language"/>
    <xs:enumeration value="City"/>
    <xs:enumeration value="QueryIntentCountry"/>
    <xs:enumeration value="QueryIntentState"/>
    <xs:enumeration value="QueryIntentCity"/>
    <xs:enumeration value="QueryIntentDMA"/>
    <xs:enumeration value="BidMatchType"/>
    <xs:enumeration value="DeliveredMatchType"/>
    <xs:enumeration value="Network"/>
    <xs:enumeration value="TopVsOther"/>
    <xs:enumeration value="DeviceType"/>
    <xs:enumeration value="DeviceOS"/>
    <xs:enumeration value="Assists"/>
    <xs:enumeration value="Conversions"/>
    <xs:enumeration value="ConversionRate" />
    <xs:enumeration value="Revenue"/>
    <xs:enumeration value="ReturnOnAdSpend"/>
    <xs:enumeration value="CostPerConversion"/>
    <xs:enumeration value="CostPerAssist"/>
    <xs:enumeration value="RevenuePerConversion"/>
    <xs:enumeration value="RevenuePerAssist"/>
    <xs:enumeration value="County"/>
    <xs:enumeration value="PostalCode"/>
    <xs:enumeration value="QueryIntentCounty"/>
    <xs:enumeration value="QueryIntentPostalCode"/>
    <xs:enumeration value="LocationId"/>
    <xs:enumeration value="QueryIntentLocationId"/>
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountId|[!INCLUDE[reportcolumn_accountid](../reporting-api/includes/reportcolumn-accountid.md)]|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AdDistribution|[!INCLUDE[reportcolumn_addistribution](../reporting-api/includes/reportcolumn-addistribution.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|Assists|[!INCLUDE[reportcolumn_assists](../reporting-api/includes/reportcolumn-assists.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|AveragePosition|[!INCLUDE[reportcolumn_averageposition](../reporting-api/includes/reportcolumn-averageposition.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|BidMatchType|[!INCLUDE[reportcolumn_bidmatchtype](../reporting-api/includes/reportcolumn-bidmatchtype.md)]|
|City|The city where the user was physically located when they clicked the ad.<br/><br/>**Note**: The location where the user was in physically when they clicked the ad.|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|CostPerAssist|[!INCLUDE[reportcolumn_costperassist](../reporting-api/includes/reportcolumn-costperassist.md)]|
|CostPerConversion|[!INCLUDE[reportcolumn_costperconversion](../reporting-api/includes/reportcolumn-costperconversion.md)]|
|Country|The country where the user was physically located when they clicked the ad.|
|County|The county where the user was physically located when they clicked the ad. |
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CurrencyCode|[!INCLUDE[reportcolumn_currencycode](../reporting-api/includes/reportcolumn-currencycode.md)]|
|DeliveredMatchType|[!INCLUDE[reportcolumn_deliveredmatchtype](../reporting-api/includes/reportcolumn-deliveredmatchtype.md)]|
|DeviceOS|[!INCLUDE[reportcolumn_deviceos](../reporting-api/includes/reportcolumn-deviceos.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|LocationId|The Bing Ads identifier of the location where the user was physically located when they clicked the ad. For geographical location identifiers, see [Geographical Location Codes](https://msdn.microsoft.com/library/bing-ads-geographical-location-codes).|
|MetroArea|The metro area where the user was physically located when they clicked the ad.|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|PostalCode|The postal code where the user was physically located when they clicked the ad.|
|ProximityTargetLocation|[!INCLUDE[reportcolumn_proximitytargetlocation](../reporting-api/includes/reportcolumn-proximitytargetlocation.md)]|
|QueryIntentCity|The name of a city if the user's geographical intent can be determined. The city is set if the user's intent is a city, and not necessarily if they are physically located in the city.|
|QueryIntentCountry|The name of a country if the user’s geographical intent can be determined. The country is set if the user’s intent is related to a country, and not necessarily if they are physically located in the county.|
|QueryIntentCounty|The name of a county if the user’s geographical intent can be determined. The county is set if the user’s intent is related to a county, and not necessarily if they are physically located in the county. |
|QueryIntentDMA|The name of a metro area if the user's geographical intent can be determined. The metro area is set if the user's intent is a metro area or city within the metro area, and not necessarily if they are physically located in the metro area.|
|QueryIntentLocationId|The location identifier if the user's geographical intent can be determined. |
|QueryIntentPostalCode|The name of a postal code if the user's geographical intent can be determined. The postal code is set if the user's intent is a postal code, and not necessarily if they are physically located in the postal code. |
|QueryIntentState|The name of a state if the user's geographical intent can be determined. The state is set if the user's intent is a state or sub geography of the state, and not necessarily if they are physically located in the state.|
|Radius|[!INCLUDE[reportcolumn_radius](../reporting-api/includes/reportcolumn-radius.md)]|
|ReturnOnAdSpend|[!INCLUDE[reportcolumn_returnonadspend](../reporting-api/includes/reportcolumn-returnonadspend.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerAssist|[!INCLUDE[reportcolumn_revenueperassist](../reporting-api/includes/reportcolumn-revenueperassist.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|State|The state where the user was physically located when they clicked the ad.<br/><br/>**Note**: The location where the user was in physically when they clicked the ad.|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|TopVsOther|[!INCLUDE[reportcolumn_topvsother](../reporting-api/includes/reportcolumn-topvsother.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|AccountName|
|TimePeriod<br /><br />**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]
## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[UserLocationPerformanceReportRequest](../reporting-api/userlocationperformancereportrequest-data-object.md)

