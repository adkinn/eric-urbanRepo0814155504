---
title: "AdType Value Set"
ms.custom: ""
ms.date: "08/14/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f3cc4a4-11db-49ff-b114-907fb3cdca7e
caps.latest.revision: 7
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdType Value Set
Defines the type of ad.

## Syntax

```xml
\<xs:simpleType name="AdType">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Text" />
    \<xs:enumeration value="Image" />
    \<xs:enumeration value="Product" />
    \<xs:enumeration value="AppInstall" />
    \<xs:enumeration value="ExpandedText" />
    \<xs:enumeration value="DynamicSearch" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AppInstall|Refers to an [AppInstallAd](../campaign-api/appinstallad-data-object.md).|
|DynamicSearch|Refers to a [DynamicSearchAd](../campaign-api/dynamicsearchad-data-object.md).|
|ExpandedText|Refers to an [ExpandedTextAd](../campaign-api/expandedtextad-data-object.md).|
|Image|Reserved for future use.|
|Product|Refers to a [ProductAd](../campaign-api/productad-data-object.md).|
|Text|Refers to a [TextAd](../campaign-api/textad-data-object.md).|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[Ad](../campaign-api/ad-data-object.md)  

