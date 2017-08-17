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

Do not try to instantiate a [Criterion](../Ad Insight Version 11/criterion-data-object.md). You can create one or more following objects that derive from it.
- [DeviceCriterion](../Ad Insight Version 11/devicecriterion-data-object.md)  
- [LanguageCriterion](../Ad Insight Version 11/languagecriterion-data-object.md)  
- [LocationCriterion](../Ad Insight Version 11/locationcriterion-data-object.md)  
- [NetworkCriterion](../Ad Insight Version 11/networkcriterion-data-object.md)  

## Syntax

```xml
\<xs:complexType name="Criterion">
  \<xs:sequence/>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

There aren't any shared or common criterion elements.

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
[GetKeywordTrafficEstimates](../Ad Insight Version 11/getkeywordtrafficestimates-service-operation.md)  
