---
title: "ConversionGoalStatus Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34155360-ff7f-4f66-a043-c43293f1eaa1
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# ConversionGoalStatus Value Set
Defines the possible user-determined status values of a conversion goal. These are the status values that a user can decide to set, for example a goal can be set to *Paused* if you no longer wish to track conversions for that goal. For status values that can be set by the system, for example whether or not the UET tag is verified, see [ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md).   

## Syntax

```xml
\<xs:simpleType name="ConversionGoalStatus">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="Active" />
        \<xs:enumeration value="Paused" />
        \<xs:enumeration value="Deleted" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Active|The conversion goal is active.|
|Deleted|This status is for internal use only. Because all Get operations do not return deleted objects, you will not see an object with this status.|
|Paused|The conversion goal is paused. While a conversion goal is paused, conversions will not be tracked for the corresponding goal.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[ConversionGoal](../campaign-api/conversiongoal-data-object.md)  
[ConversionGoalTrackingStatus](../campaign-api/conversiongoaltrackingstatus-value-set.md)  
