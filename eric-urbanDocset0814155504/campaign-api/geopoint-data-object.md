---
title: "GeoPoint Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6b36de75-f66a-4673-9878-4d0039df1b97
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# GeoPoint Data Object
Defines an object that contains the longitude and latitude coordinates of a geographical location.

## Syntax

```xml
\<xs:complexType name="GeoPoint">
  \<xs:sequence>
    \<xs:element name="LatitudeInMicroDegrees" type="xs:int" />
    \<xs:element name="LongitudeInMicroDegrees" type="xs:int" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*LatitudeInMicroDegrees*|The latitude specified in micro degrees. The latitude must be greater than or equal to -85000000 and less than or equal to +85000000.|*int*|
|*LongitudeInMicroDegrees*|The longitude specified in micro degrees. The longitude must be greater than or equal to -180000000 and less than or equal to +180000000.|*int*|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[LocationAdExtension](../campaign-api/locationadextension-data-object.md)

