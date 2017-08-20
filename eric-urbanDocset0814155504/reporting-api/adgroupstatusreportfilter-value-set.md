---
title: "AdGroupStatusReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d18e52a4-f91d-442a-802b-d4ac6d668c22
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupStatusReportFilter Value Set
Defines the ad group status values that you can use to filter the report data. These values are also used as column values in reports that include ad group status, such as the ad group performance report.

## Syntax

```xml
<xs:simpleType name="AdGroupStatusReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Active"/>
        <xs:enumeration value="Deleted"/>
        <xs:enumeration value="Expired"/>
        <xs:enumeration value="Paused"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
<xs:element name="AdGroupStatusReportFilter" nillable="true" type="tns:AdGroupStatusReportFilter"/>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The report will contain ad groups that are active.|
|Deleted|The report will contain ad groups that have been deleted.|
|Expired|The report will contain ad groups that have expired.|
|Paused|The report will contain ad groups that are paused.|

## Remarks
This value set is used as a set of flags. You can combine the values when setting an element of this type. For example, in C#, use the following code example to filter the report data for paused and deleted ad groups in the report.

```csharp
objAdGroupPerfReportRequest.Status = 
    AdGroupStatusReportFilter.Paused | AdGroupStatusReportFilter.Deleted;
```

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
## See Also
[AdGroupPerformanceReportFilter](../reporting-api/adgroupperformancereportfilter-data-object.md)

