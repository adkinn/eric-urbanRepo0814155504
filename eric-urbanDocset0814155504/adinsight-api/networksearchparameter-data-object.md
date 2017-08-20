---
title: "NetworkSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c64572c2-c83c-45de-98e4-8cfc0c852643
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NetworkSearchParameter Data Object
The network search parameter filter that you can include when requesting keyword ideas.

If you do not include the network search parameter when calling [GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md), then keyword ideas will be returned for all networks.

## Syntax

```xml
\<xs:complexType name="NetworkSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element xmlns:q5="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" minOccurs="0" name="Network" nillable="true" type="q5:NetworkCriterion"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Network*|The network criterion for the returned keyword ideas.|[NetworkCriterion](../adinsight-api/networkcriterion-data-object.md)|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
