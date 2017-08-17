---
title: "AdPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 36b8a0eb-3c8d-42b7-b311-9597ae204652
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdPerformanceReportFilter Data Object
Defines the criteria to use to filter the ad performance report request data.

## Syntax

```xml
<xs:complexType name="AdPerformanceReportFilter">
  <xs:sequence>
    <xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdDistribution" type="tns:AdDistributionReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdStatus" type="tns:AdStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdType" type="tns:AdTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="DeviceType" type="tns:DeviceTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="LanguageCode" type="q6:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q6="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*AdStatus*|The report will include data for only the ad status. For example, you can use the filter to include data for only active ads.<br /><br />You can specify one or more ad statuses.|[AdStatusReportFilter](../reporting-api/adstatusreportfilter-value-set.md)|Optional|
|*AdType*|The report will include data for only the specified ad types. For example, the report can include data for product or text ads. You can specify one or more ad types.|[AdTypeReportFilter](../reporting-api/adtypereportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for only the campaign status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeviceType*|The report will include data for only the specified types of devices on which the ad is displayed. For example, you can use the filter to include data for only text ads displayed on smartphones.<br /><br />You can specify one or more device types.|[DeviceTypeReportFilter](../reporting-api/devicetypereportfilter-value-set.md)|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](http://msdn.microsoft.com/library/ac68ee2d-1cbc-4ea7-b648-68c21f8ffa3a).|*string* array|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [AdPerformanceReportRequest](../reporting-api/adperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdPerformanceReportRequest](../reporting-api/adperformancereportrequest-data-object.md)

