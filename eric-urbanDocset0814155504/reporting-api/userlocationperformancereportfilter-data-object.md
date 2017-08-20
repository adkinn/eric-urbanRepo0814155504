---
title: "UserLocationPerformanceReportFilter Data Object"
ms.custom: ""
ms.date: "05/08/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: abf11c58-825a-4c75-91f4-b343cfc58301
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# UserLocationPerformanceReportFilter Data Object
Defines the criteria to use to filter the user location performance report data.

## Syntax

```xml
<xs:complexType name="UserLocationPerformanceReportFilter">
  <xs:sequence>
    <xs:element minOccurs="0" name="AdDistribution" nillable="true" type="tns:AdDistributionReportFilter" />
    <xs:element minOccurs="0" name="CountryCode" nillable="true" type="q27:ArrayOfstring" xmlns:q27="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
    <xs:element minOccurs="0" name="LanguageCode" nillable="true" type="q28:ArrayOfstring" xmlns:q28="http://schemas.microsoft.com/2003/10/Serialization/Arrays" />
  </xs:sequence>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required/Optional|
|-----------|---------------|-------------|---------------------|
|*AdDistribution*|The report will include data for only the specified distribution medium. For example, you can use the filter to include data for only search ads.<br /><br />You can specify one or more distribution mediums.|[AdDistributionReportFilter](../reporting-api/addistributionreportfilter-value-set.md)|Optional|
|*CountryCode*|The report will include data for only the specified countries/regions where the user that clicked the ad is located.<br /><br />For a list of possible values, see [Geographical Location Codes](https://msdn.microsoft.com/library/bing-ads-geographical-location-codes.aspx).|*string* array|Optional|
|*LanguageCode*|The report will include data for only websites that used the specified languages. For a list of possible values, see [Ad Languages](https://msdn.microsoft.com/library/bing-ads-ad-languages.aspx).|*string* array|Optional|

## Remarks
Setting all filter criteria elements to NULL is the same as setting the *Filter* element of [UserLocationPerformanceReportRequest](../reporting-api/userlocationperformancereportrequest-data-object.md) to NULL.

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[UserLocationPerformanceReportRequest](../reporting-api/userlocationperformancereportrequest-data-object.md)

