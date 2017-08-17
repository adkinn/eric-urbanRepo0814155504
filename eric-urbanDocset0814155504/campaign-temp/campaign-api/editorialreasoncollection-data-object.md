---
title: "EditorialReasonCollection Data Object"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab58a13a-3e7c-4f55-81b0-d60d7854b261
caps.latest.revision: 5
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# EditorialReasonCollection Data Object
Defines a collection of ads or keywords that failed editorial review, and the reason for the failure.

## Syntax

```xml
\<xs:complexType name="EditorialReasonCollection">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="AdGroupId" type="xs:long"/>
    \<xs:element minOccurs="0" name="AdOrKeywordId" type="xs:long" />
    \<xs:element minOccurs="0" name="AppealStatus" type="tns:AppealStatus" />
    \<xs:element minOccurs="0" name="Reasons" nillable="true type="tns:ArrayOfEditorialReason" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*AdGroupId*|Identifies the ad group which is the parent of the ad or keyword that failed editorial review.|*long*|
|*AdOrKeywordId*|Identifies the ad or keyword that failed editorial review.|*long*|
|*AppealStatus*|A value that determines whether you can appeal the issues found by the editorial review.|[AppealStatus](../campaign-api/appealstatus-value-set.md)|
|*Reasons*|An array of editorial reasons that you can use to determine the component of an ad or keyword that failed editorial review, and the reason for the failure.|[EditorialReason](../campaign-api/editorialreason-data-object.md) array|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[GetEditorialReasonsByIds](../campaign-api/geteditorialreasonsbyids-service-operation.md)

