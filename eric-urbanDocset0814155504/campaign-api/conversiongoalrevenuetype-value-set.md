---
title: "ConversionGoalRevenueType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1c97117b-7ef1-46bc-a93a-72fac163cd3b
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionGoalRevenueType Value Set
Defines conversion goal revenue models that you can use to track how much each conversion is worth to your business.   

## Syntax

```xml
\<xs:simpleType name="ConversionGoalRevenueType">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="FixedValue" />
        \<xs:enumeration value="VariableValue" />
        \<xs:enumeration value="NoValue" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|FixedValue|Each time it happens, the conversion has the same value.|
|NoValue|Don't assign a value for the conversion.|
|VariableValue|The value of the conversion may vary for example, by purchase price. You'll need to customize your UET tag tracking code to report variable revenue. For more information, see [How to report variable revenue with UET](https://help.bingads.microsoft.com/#apex/3/en/56687/2/en/#ext:none).|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoalRevenue](../campaign-api/conversiongoalrevenue-data-object.md)

