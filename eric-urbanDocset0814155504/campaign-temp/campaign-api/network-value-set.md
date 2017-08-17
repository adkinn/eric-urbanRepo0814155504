---
title: "Network Value Set"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e391d552-0036-4354-bcb7-42cd93bf6dbb
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Network Value Set
Defines the possible search networks on which an ad can display.
For more information about networks and ad distribution, see the [About Ad Distribution](http://help.bingads.microsoft.com/#apex/3/en/50871/0) help article.

## Syntax

```xml
\<xs:simpleType name="Network">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="OwnedAndOperatedAndSyndicatedSearch" />
    \<xs:enumeration value="OwnedAndOperatedOnly" />
    \<xs:enumeration value="SyndicatedSearchOnly" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|OwnedAndOperatedAndSyndicatedSearch|Display ads on owned and operated networks, as well as syndicated search networks.|
|OwnedAndOperatedOnly|Display ads on only owned and operated networks.<br /><br />Owned and operated networks refer to the Bing™, AOL, and Yahoo search networks.|
|SyndicatedSearchOnly|Display ads on only syndicated search networks.<br /><br />Syndicated search refers to partner sites that host Bing™, AOL, and Yahoo search.|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)

