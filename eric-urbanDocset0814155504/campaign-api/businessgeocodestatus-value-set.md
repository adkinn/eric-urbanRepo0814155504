---
title: "BusinessGeoCodeStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e42d8a3-b405-4adf-8809-847452da11bc
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BusinessGeoCodeStatus Value Set
Defines the possible status values that indicate the progress of determining the latitude and longitude values of a business.

## Syntax

```xml
\<xs:simpleType name="BusinessGeoCodeStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Pending" />
    \<xs:enumeration value="Complete" />
    \<xs:enumeration value="Invalid" />
    \<xs:enumeration value="Failed" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Complete|Successfully determined the latitude and longitude of the business.|
|Failed|Unable to determine the latitude and longitude of the business.|
|Invalid|Unable to determine the latitude and longitude of the business, possibly because the address did not resolve.|
|Pending|In the process of determining the latitude and longitude of the business.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[LocationAdExtension](../campaign-api/locationadextension-data-object.md)

