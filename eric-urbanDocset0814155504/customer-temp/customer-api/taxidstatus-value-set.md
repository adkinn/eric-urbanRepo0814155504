---
title: "TaxIdStatus Value Set"
ms.custom: ""
ms.date: "07/20/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: afe41a42-f4b7-4d3e-bd1d-a96b57375906
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# TaxIdStatus Value Set
Defines the possible status values of an account's tax identifier.

## Syntax

```xml
\<xs:simpleType name="TaxIdStatus">
  \<xs:restriction base="xs:string">
    \<xs:enumeration value="Valid" />
    \<xs:enumeration value="Invalid" />
    \<xs:enumeration value="Pending" />
    \<xs:enumeration value="Inactive" />
  \</xs:restriction>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|Inactive|The tax identifier could not be verified. Please contact [Bing Ads Support](http://go.microsoft.com/fwlink/?LinkId=269631) for more information.|
|Invalid|The tax identifier is not valid.|
|Pending|The tax identifier is being verified.|
|Valid|The tax identifier is valid.|

## Requirements
[!INCLUDE[reqcus](../customer-api/includes/reqcus.md)]
## See Also
[AdvertiserAccount](../customer-api/advertiseraccount-data-object.md)

