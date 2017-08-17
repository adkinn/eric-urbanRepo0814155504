---
title: "IntentOption Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1b06b72-c3c3-48d6-82af-02f73e556420
caps.latest.revision: 6
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# IntentOption Value Set
Defines the possible intent options for location criterion, for example to target people in, searching for, or viewing pages about your targeted location.

## Syntax

```xml
<xs:simpleType name="IntentOption">
  <xs:restriction base="xs:string">
    <xs:enumeration value="PeopleInOrSearchingForOrViewingPages" />
    <xs:enumeration value="PeopleIn" />
    <xs:enumeration value="PeopleSearchingForOrViewingPages" />
  </xs:restriction>
</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|PeopleInOrSearchingForOrViewingPages|Show ads to people in, searching for, or viewing pages about your targeted location.|
|PeopleIn|Show ads to people in your targeted location.|
|PeopleSearchingForOrViewingPages|Show ads to people searching for or viewing pages about your targeted location.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[LocationCriterion](../campaign-api/locationcriterion-data-object.md)  
