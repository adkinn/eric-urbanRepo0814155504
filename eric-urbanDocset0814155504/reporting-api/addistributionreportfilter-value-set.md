---
title: "AdDistributionReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5fdf9fe4-39eb-4149-a42c-4c6af42d7c08
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdDistributionReportFilter Value Set
Defines the ad distribution medium values that you can use to filter the report data. These values are also used as column values in reports that include ad distribution, such as the account performance report.

## Syntax

```xml
<xs:simpleType name="AdDistributionReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Search"/>
        <xs:enumeration value="Content"/>
        <xs:enumeration value="Native"/>
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Content|The report will contain content ads.|
|Native|The report will contain native ads.|
|Search|The report will contain search ads.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
