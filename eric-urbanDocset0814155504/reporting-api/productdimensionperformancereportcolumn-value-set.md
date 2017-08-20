---
title: "ProductDimensionPerformanceReportColumn Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23b81a36-743d-4c2d-b0d4-9bfaac78a538
caps.latest.revision: 14
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ProductDimensionPerformanceReportColumn Value Set
Defines the attributes and performance statistics columns that you can include in the [ProductDimensionPerformanceReportRequest](../reporting-api/productdimensionperformancereportrequest-data-object.md).

[!INCLUDE[reportcolumn_header](../reporting-api/includes/reportcolumn-header.md)]
## Syntax

```xml
<xs:simpleType name="ProductDimensionPerformanceReportColumn">
  <xs:restriction base="xs:string">
    <xs:enumeration value="TimePeriod"/>
    <xs:enumeration value="AccountName"/>
    <xs:enumeration value="AccountNumber"/>
    <xs:enumeration value="AdGroupName"/>
    <xs:enumeration value="AdGroupId"/>
    <xs:enumeration value="AdId"/>
    <xs:enumeration value="CampaignName"/>
    <xs:enumeration value="CurrencyCode"/>
    <xs:enumeration value="DeviceType"/>
    <xs:enumeration value="Language"/> 
    <xs:enumeration value="MerchantProductId"/> 
    <xs:enumeration value="Title"/>
    <xs:enumeration value="Condition"/>
    <xs:enumeration value="Brand"/>
    <xs:enumeration value="CustomLabel0"/>
    <xs:enumeration value="CustomLabel1"/>
    <xs:enumeration value="CustomLabel2"/>
    <xs:enumeration value="CustomLabel3"/>
    <xs:enumeration value="CustomLabel4"/>
    <xs:enumeration value="ProductType1"/>
    <xs:enumeration value="ProductType2"/>
    <xs:enumeration value="ProductType3"/>
    <xs:enumeration value="ProductType4"/>
    <xs:enumeration value="ProductType5"/>
    <xs:enumeration value="ProductCategory1"/>
    <xs:enumeration value="ProductCategory2"/>
    <xs:enumeration value="ProductCategory3"/>
    <xs:enumeration value="ProductCategory4"/>
    <xs:enumeration value="ProductCategory5"/>
    <xs:enumeration value="Impressions"/>
    <xs:enumeration value="Clicks"/>
    <xs:enumeration value="Ctr"/>
    <xs:enumeration value="AverageCpc"/>
    <xs:enumeration value="Spend"/>
    <xs:enumeration value="AccountStatus"/>
    <xs:enumeration value="CampaignStatus"/>
    <xs:enumeration value="AdGroupStatus"/>
    <xs:enumeration value="CampaignId"/>
    <xs:enumeration value="Conversions"/>
    <xs:enumeration value="ConversionRate"/>
    <xs:enumeration value="Network"/>
    <xs:enumeration value="Price"/>
    <xs:enumeration value="Revenue"/>
    <xs:enumeration value="RevenuePerConversion"/> 
    <xs:enumeration value="SellerName"/>
    <xs:enumeration value="OfferLanguage"/>
    <xs:enumeration value="CountryOfSale"/>
    <xs:enumeration value="AdStatus"/> 
    <xs:enumeration value="ImpressionSharePercent"/> 
    <xs:enumeration value="ImpressionLostToBudgetPercent"/> 
    <xs:enumeration value="ImpressionLostToRankPercent"/> 
    <xs:enumeration value="BenchmarkBid"/> 
    <xs:enumeration value="BenchmarkCtr"/> 
    <xs:enumeration value="TopVsOther"/> 
    <xs:enumeration value="AdDistribution"/> 
    <xs:enumeration value="ClickTypeId" />
    <xs:enumeration value="TotalClicksOnAdElements" />
    <xs:enumeration value="ClickType" />
    <xs:enumeration value="ReturnOnAdSpend" />
    <xs:enumeration value="BidStrategyType" />
    <xs:enumeration value="LocalStoreCode" />
    <xs:enumeration value="StoreId" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AccountName|[!INCLUDE[reportcolumn_accountname](../reporting-api/includes/reportcolumn-accountname.md)]|
|AccountNumber|[!INCLUDE[reportcolumn_accountnumber](../reporting-api/includes/reportcolumn-accountnumber.md)]|
|AccountStatus|[!INCLUDE[reportcolumn_accountstatus](../reporting-api/includes/reportcolumn-accountstatus.md)]|
|AdDistribution|[!INCLUDE[reportcolumn_addistribution](../reporting-api/includes/reportcolumn-addistribution.md)]|
|AdGroupId|[!INCLUDE[reportcolumn_adgroupid](../reporting-api/includes/reportcolumn-adgroupid.md)]|
|AdGroupName|[!INCLUDE[reportcolumn_adgroupname](../reporting-api/includes/reportcolumn-adgroupname.md)]|
|AdGroupStatus|[!INCLUDE[reportcolumn_adgroupstatus](../reporting-api/includes/reportcolumn-adgroupstatus.md)]|
|AdId|[!INCLUDE[reportcolumn_adid](../reporting-api/includes/reportcolumn-adid.md)]|
|AdStatus|[!INCLUDE[reportcolumn_adstatus](../reporting-api/includes/reportcolumn-adstatus.md)]|
|AverageCpc|[!INCLUDE[reportcolumn_averagecpc](../reporting-api/includes/reportcolumn-averagecpc.md)]|
|BenchmarkBid|[!INCLUDE[reportcolumn_benchmarkbid](../reporting-api/includes/reportcolumn-benchmarkbid.md)]|
|BenchmarkCtr|[!INCLUDE[reportcolumn_benchmarkctr](../reporting-api/includes/reportcolumn-benchmarkctr.md)]|
|BidStrategyType|The bid strategy type. Possible values include *EnhancedCpc* and *ManualCpc*. If the InheritFromParent strategy type is used, the report will include the inherited bid strategy type e.g. one of the supported values listed above.|
|Brand|[!INCLUDE[reportcolumn_brand](../reporting-api/includes/reportcolumn-brand.md)]|
|CampaignId|[!INCLUDE[reportcolumn_campaignid](../reporting-api/includes/reportcolumn-campaignid.md)]|
|CampaignName|[!INCLUDE[reportcolumn_campaignname](../reporting-api/includes/reportcolumn-campaignname.md)]|
|CampaignStatus|[!INCLUDE[reportcolumn_campaignstatus](../reporting-api/includes/reportcolumn-campaignstatus.md)]|
|Clicks|[!INCLUDE[reportcolumn_clicks](../reporting-api/includes/reportcolumn-clicks.md)]|
|ClickType|[!INCLUDE[reportcolumn_clicktype](../reporting-api/includes/reportcolumn-clicktype.md)]|
|ClickTypeId|[!INCLUDE[reportcolumn_clicktypeid](../reporting-api/includes/reportcolumn-clicktypeid.md)]|
|Condition|[!INCLUDE[reportcolumn_condition](../reporting-api/includes/reportcolumn-condition.md)]|
|ConversionRate|[!INCLUDE[reportcolumn_conversionrate](../reporting-api/includes/reportcolumn-conversionrate.md)]|
|Conversions|[!INCLUDE[reportcolumn_conversions](../reporting-api/includes/reportcolumn-conversions.md)]|
|Ctr|[!INCLUDE[reportcolumn_ctr](../reporting-api/includes/reportcolumn-ctr.md)]|
|CountryOfSale|[!INCLUDE[reportcolumn_CountryOfSale](../reporting-api/includes/reportcolumn-countryofsale.md)]|
|CustomLabel0|[!INCLUDE[reportcolumn_customlabel0](../reporting-api/includes/reportcolumn-customlabel0.md)]|
|CustomLabel1|[!INCLUDE[reportcolumn_customlabel1](../reporting-api/includes/reportcolumn-customlabel1.md)]|
|CustomLabel2|[!INCLUDE[reportcolumn_customlabel2](../reporting-api/includes/reportcolumn-customlabel2.md)]|
|CustomLabel3|[!INCLUDE[reportcolumn_customlabel3](../reporting-api/includes/reportcolumn-customlabel3.md)]|
|CustomLabel4|[!INCLUDE[reportcolumn_customlabel4](../reporting-api/includes/reportcolumn-customlabel4.md)]|
|CurrencyCode|[!INCLUDE[reportcolumn_currencycode](../reporting-api/includes/reportcolumn-currencycode.md)]|
|DeviceType|[!INCLUDE[reportcolumn_devicetype](../reporting-api/includes/reportcolumn-devicetype.md)]|
|ImpressionLostToBudgetPercent|[!INCLUDE[reportcolumn_impressionlosttobudgetpercent](../reporting-api/includes/reportcolumn-impressionlosttobudgetpercent.md)]|
|ImpressionLostToRankPercent|[!INCLUDE[reportcolumn_impressionlosttorankpercent](../reporting-api/includes/reportcolumn-impressionlosttorankpercent.md)]|
|Impressions|[!INCLUDE[reportcolumn_impressions](../reporting-api/includes/reportcolumn-impressions.md)]|
|ImpressionSharePercent|[!INCLUDE[reportcolumn_impressionsharepercent](../reporting-api/includes/reportcolumn-impressionsharepercent.md)]|
|Language|[!INCLUDE[reportcolumn_language](../reporting-api/includes/reportcolumn-language.md)]|
|LocalStoreCode|An alphanumeric identifier defined by the merchant to uniquely identify each local store. |
|MerchantProductId|[!INCLUDE[reportcolumn_merchantproductid](../reporting-api/includes/reportcolumn-merchantproductid.md)]|
|Network|[!INCLUDE[reportcolumn_network](../reporting-api/includes/reportcolumn-network.md)]|
|OfferLanguage|[!INCLUDE[reportcolumn_OfferLanguage](../reporting-api/includes/reportcolumn-offerlanguage.md)]|
|Price|[!INCLUDE[reportcolumn_price](../reporting-api/includes/reportcolumn-price.md)]|
|ProductCategory1|[!INCLUDE[reportcolumn_productcategory1](../reporting-api/includes/reportcolumn-productcategory1.md)]|
|ProductCategory2|[!INCLUDE[reportcolumn_productcategory2](../reporting-api/includes/reportcolumn-productcategory2.md)]|
|ProductCategory3|[!INCLUDE[reportcolumn_productcategory3](../reporting-api/includes/reportcolumn-productcategory3.md)]|
|ProductCategory4|[!INCLUDE[reportcolumn_productcategory4](../reporting-api/includes/reportcolumn-productcategory4.md)]|
|ProductCategory5|[!INCLUDE[reportcolumn_productcategory5](../reporting-api/includes/reportcolumn-productcategory5.md)]|
|ProductType1|[!INCLUDE[reportcolumn_producttype1](../reporting-api/includes/reportcolumn-producttype1.md)]|
|ProductType2|[!INCLUDE[reportcolumn_producttype2](../reporting-api/includes/reportcolumn-producttype2.md)]|
|ProductType3|[!INCLUDE[reportcolumn_producttype3](../reporting-api/includes/reportcolumn-producttype3.md)]|
|ProductType4|[!INCLUDE[reportcolumn_producttype4](../reporting-api/includes/reportcolumn-producttype4.md)]|
|ProductType5|[!INCLUDE[reportcolumn_producttype5](../reporting-api/includes/reportcolumn-producttype5.md)]|
|Revenue|[!INCLUDE[reportcolumn_revenue](../reporting-api/includes/reportcolumn-revenue.md)]|
|RevenuePerConversion|[!INCLUDE[reportcolumn_revenueperconversion](../reporting-api/includes/reportcolumn-revenueperconversion.md)]|
|SellerName|[!INCLUDE[reportcolumn_sellername](../reporting-api/includes/reportcolumn-sellername.md)]|
|Spend|[!INCLUDE[reportcolumn_spend](../reporting-api/includes/reportcolumn-spend.md)]|
|StoreId|The unique identifier for the Bing Merchant Center store.|
|TimePeriod|[!INCLUDE[reportcolumn_timeperiod](../reporting-api/includes/reportcolumn-timeperiod.md)]|
|Title|[!INCLUDE[reportcolumn_title](../reporting-api/includes/reportcolumn-title.md)]|
|TopVsOther|[!INCLUDE[reportcolumn_topvsother](../reporting-api/includes/reportcolumn-topvsother.md)]|
|TotalClicksOnAdElements|[!INCLUDE[reportcolumn_totalclicksonadelements](../reporting-api/includes/reportcolumn-totalclicksonadelements.md)]|

## <a name="requiredcolumns"></a>Required Columns
The report must include the following columns.

|Column|
|----------|
|MerchantProductId|
|TimePeriod<br/><br/>**Note**: This column is required for all aggregation types except Summary.|
[!INCLUDE[reportcolumn_statsrequired](../reporting-api/includes/reportcolumn-statsrequired.md)]

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ProductDimensionPerformanceReportRequest](../reporting-api/productdimensionperformancereportrequest-data-object.md)

