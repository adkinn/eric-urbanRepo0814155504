---
title: "DeviceOSReportFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2f253b29-75ef-497b-ba40-2ed321242987
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeviceOSReportFilter Value Set
Defines the device operating system values that you can use to filter the report data.

## Syntax

```xml
<xs:simpleType name="DeviceOSReportFilter">
  <xs:list>
    <xs:simpleType>
      <xs:restriction base="xs:string">
        <xs:enumeration value="Other" />
        <xs:enumeration value="Windows" />
        <xs:enumeration value="iOS">
        <xs:enumeration value="Android">
        <xs:enumeration value="BlackBerry">
      </xs:restriction>
    </xs:simpleType>
  </xs:list>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Android|The report will include ads displayed on Android device operating systems.|
|BlackBerry|The report will include ads displayed on BlackBerry device operating systems.|
|iOS|The report will include ads displayed on iOS device operating systems.|
|Other|The report will include ads displayed on a device operating system other than Android, BlackBerry, iOS, and Windows.|
|Windows|The report will include ads displayed on Windows device operating systems.|

## Requirements
[!INCLUDE[reqrep](../reporting-api/includes/reqrep.md)]
