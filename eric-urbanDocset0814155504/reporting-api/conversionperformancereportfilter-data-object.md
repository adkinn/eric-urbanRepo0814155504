---
title: "ConversionPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 95aac22c-8e77-4d75-88a5-465e000d3f0f
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionPerformanceReportFilter Data Object
Defines the criteria to use to filter the conversion performance report data.

## Syntax

```xml
\<xs:complexType name="ConversionPerformanceReportFilter">
  \<xs:sequence>
    \<xs:element name="AccountStatus" type="tns:AccountStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdDistribution" type="tns:AdDistributionReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="AdGroupStatus" type="tns:AdGroupStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="CampaignStatus" type="tns:CampaignStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="DeviceType" type="tns:DeviceTypeReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="KeywordStatus" type="tns:KeywordStatusReportFilter" nillable="true" minOccurs="0"/>
    \<xs:element name="Keywords" type="q22:ArrayOfstring" nillable="true" minOccurs="0" xmlns:q22="http://schemas.microsoft.com/2003/10/Serialization/Arrays"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AccountStatus*|The report will include data for only the account status. For example, you can use the filter to include data for only active accounts.<br /><br />You can specify one or more account statuses.|[AccountStatusReportFilter](../reporting-api/accountstatusreportfilter-value-set.md)|Optional|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter Value Set](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*AdGroupStatus*|The report will include data for only the ad group status. For example, you can use the filter to include data for only active ad groups.<br /><br />You can specify one or more ad group statuses.|[AdGroupStatusReportFilter](../reporting-api/adgroupstatusreportfilter-value-set.md)|Optional|
|*CampaignStatus*|The report will include data for only the campaign status. For example, you can use the filter to include data for only active campaigns.<br /><br />You can specify one or more campaign statuses.|[CampaignStatusReportFilter](../reporting-api/campaignstatusreportfilter-value-set.md)|Optional|
|*DeviceType*|The report will include data for only the specified types of devices on which the ad is displayed. For example, you can use the filter to include data only for text ads displayed on smartphones.<br /><br />You can specify one or more device types.|[DeviceTypeReportFilter Value Set](../reporting-api/devicetypereportfilter-value-set.md)|Optional|
|*KeywordStatus*|The report will include data for only the keyword status. For example, you can use the filter to include data for only active keywords.<br /><br />You can specify one or more keyword statuses.|[KeywordStatusReportFilter](../reporting-api/keywordstatusreportfilter-value-set.md)|Optional|
|*Keywords*|The report will include data for only the specified keywords. You can specify a maximum of 75 keywords. Each keyword can contain a maximum of 100 characters.|*string* array|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [ConversionPerformanceReportRequest](../reporting-api/conversionperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[ConversionPerformanceReportRequest](../reporting-api/conversionperformancereportrequest-data-object.md)

