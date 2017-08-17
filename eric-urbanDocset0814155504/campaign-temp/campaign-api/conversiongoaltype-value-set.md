---
title: "ConversionGoalType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42781d3c-0f19-49f1-b8b7-97a29aa4d6ac
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionGoalType Value Set
Defines the current possible types of conversion goals. 

## Syntax

```xml
\<xs:simpleType name="ConversionGoalType">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Url" />
        \<xs:enumeration value="Duration" />
        \<xs:enumeration value="Event" />       
        \<xs:enumeration value="AppInstall" />
        \<xs:enumeration value="PagesViewedPerVisit" />
        \<xs:enumeration value="OfflineConversion" />
        \<xs:enumeration value="InStoreTransaction" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AppInstall|Refers to an [AppInstallGoal](../campaign-api/appinstallgoal-data-object.md)|
|Duration|Refers to a [DurationGoal](../campaign-api/durationgoal-data-object.md)|
|Event|Refers to an [EventGoal](../campaign-api/eventgoal-data-object.md)|
|InStoreTransaction|Refers to an [InStoreTransactionGoal](../campaign-api/instoretransactiongoal-data-object.md)|
|OfflineConversion|Refers to an [OfflineConversionGoal](../campaign-api/offlineconversiongoal-data-object.md)|
|PagesViewedPerVisit|Refers to a [PagesViewedPerVisitGoal](../campaign-api/pagesviewedpervisitgoal-data-object.md)|
|Url|Refers to a [UrlGoal](../campaign-api/urlgoal-data-object.md)|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)
