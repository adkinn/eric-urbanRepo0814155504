---
title: "AdGroupBidLandscapeInput Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bb40c4a-eeef-47db-995e-94d314b3e345
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdGroupBidLandscapeInput Data Object
Defines an object that contains the requested bid landscape type for the corresponding ad group identifier.

## Syntax

```xml
\<xs:complexType name="AdGroupBidLandscapeInput">
  \<xs:sequence>
    \<xs:element name="AdGroupBidLandscapeType" type="tns:AdGroupBidLandscapeType" minOccurs="0"/>
    \<xs:element name="AdGroupId" type="xs:long" minOccurs="0"/>    
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|Required|
|-----------|---------------|-------------|------------|
|*AdGroupBidLandscapeType*|Determines whether all or a subset of an ad group's existing keywords should be used to determine the bid landscape.<br /><br />If not specified in a request, the default value is Uniform.|[AdGroupBidLandscapeType](../adinsight-api/adgroupbidlandscapetype-value-set.md)|No|
|*AdGroupId*|The ad group identifier.|*long*|Yes|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetBidLandscapeByAdGroupIds](../adinsight-api/getbidlandscapebyadgroupids-service-operation.md)

