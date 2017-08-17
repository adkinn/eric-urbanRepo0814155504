---
title: "DeviceTypeReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b403098b-65ca-47fd-9f58-5b269642996f
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeviceTypeReportFilter Value Set
Defines the device type values that you can use to filter the report data. These values are also used as column values in reports that include device type information, such as the ad group performance report.

## Syntax

```xml
<xs:simpleType name="DeviceTypeReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Computer" />
        <xs:enumeration value="SmartPhone" />
        <xs:enumeration value="NonSmartPhone">
        <xs:enumeration value="Tablet">
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Computer|The report will include text ads displayed on computers.|
|NonSmartPhone|The report will include mobile ads displayed on a mobile device.|
|SmartPhone|The report will include text ads displayed on smartphones (any high fidelity device capable of rendering full HTML).|
|Tablet|The report will include text ads displayed on a tablet device.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
