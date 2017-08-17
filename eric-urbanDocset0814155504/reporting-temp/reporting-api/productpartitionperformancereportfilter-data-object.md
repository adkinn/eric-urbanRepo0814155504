---
title: "ProductPartitionPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 033d507c-d37f-4ce9-a8cd-41678dcde12a
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ProductPartitionPerformanceReportFilter Data Object
Defines the criteria to use to filter the product partition performance report data.

## Syntax

```xml
\<xs:complexType name="ProductPartitionPerformanceReportFilter">
  \<xs:sequence>
    \<xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdStatus" type="tns:AdStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="DeviceType" type="tns:DeviceTypeReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="LanguageCode" type="q35:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q35="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*AdStatus*|The report will include data for only the ad status. For example, you can use the filter to include data for only active ads.<br /><br />You can specify one or more ad statuses.|[AdStatusReportFilter](../reporting-api/adstatusreportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for only the campaign status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeviceType*|The report will include data for only the specified types of devices on which the ad is displayed. For example, you can use the filter to include data for only ads displayed on computers.<br /><br />You can specify one or more device types.|[DeviceTypeReportFilter](../reporting-api/devicetypereportfilter-value-set.md)|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx).|*string* array|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [ProductPartitionPerformanceReportRequest](../reporting-api/productpartitionperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ProductPartitionPerformanceReportRequest](../reporting-api/productpartitionperformancereportrequest-data-object.md)  

