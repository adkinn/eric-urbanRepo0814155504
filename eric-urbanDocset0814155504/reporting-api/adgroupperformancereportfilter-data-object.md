---
title: "AdGroupPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 64fba9bd-b0a8-49d1-a70d-6c9ba85f13a5
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupPerformanceReportFilter Data Object
Defines the criteria to use to filter the ad group performance report data.

## Syntax

```xml
<xs:complexType name="AdGroupPerformanceReportFilter">
  <xs:sequence>
    <xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="AdDistribution" type="tns:AdDistributionReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="DeviceOS" type="tns:DeviceOSReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="DeviceType" type="tns:DeviceTypeReportFilter" nillable="true" minOccurs="0"/>
    <xs:element name="LanguageCode" type="q5:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q5="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
    <xs:element name="Status" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for only the campaign status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeviceOS*|The report will include data where the ad is displayed on the specified device operating systems. For example, you may use the filter to include data for only ads displayed on Windows devices.|[DeviceOSReportFilter](../reporting-api/deviceosreportfilter-value-set.md)|Optional|
|*DeviceType*|The report will include data where the ad is displayed on the specified device types. For example, you may use the filter to include data for only ads displayed on smartphones.<br /><br />You may specify one or more device types.|[DeviceTypeReportFilter](../reporting-api/devicetypereportfilter-value-set.md)|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](http://msdn.microsoft.com/library/ac68ee2d-1cbc-4ea7-b648-68c21f8ffa3a).|*string* array|Optional|
|*Status*|The report will include data for only the specified ad group status values. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more status values.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [AdGroupPerformanceReportRequest](../reporting-api/adgroupperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdGroupPerformanceReportRequest](../reporting-api/adgroupperformancereportrequest-data-object.md)

