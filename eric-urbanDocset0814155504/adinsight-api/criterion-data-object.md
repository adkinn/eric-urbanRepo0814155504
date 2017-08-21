---
title: "Criterion Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e116beeb-ec7d-4cd9-87f4-6f9140e63650
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Criterion Data Object
This is the base class from which keyword planner criterion objects derive. 

Do not try to instantiate a [Criterion](../adinsight-api/criterion-data-object.md). You can create one or more following objects that derive from it.
- [DeviceCriterion](../adinsight-api/devicecriterion-data-object.md)  
- [LanguageCriterion](../adinsight-api/languagecriterion-data-object.md)  
- [LocationCriterion](../adinsight-api/locationcriterion-data-object.md)  
- [NetworkCriterion](../adinsight-api/networkcriterion-data-object.md)  

## Syntax

```xml
<xs:complexType name="Criterion">
  <xs:sequence/>
</xs:complexType>
```

## <a name="Elements"></a>Elements

There aren't any shared or common criterion elements.

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  
