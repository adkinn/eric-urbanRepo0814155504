---
title: "NetworkCriterion Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb10f787-bb97-4721-afba-0b394b8dd03b
caps.latest.revision: 2
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# NetworkCriterion Data Object
The network criterion that you can include when requesting keyword ideas or traffic estimates.

## Syntax

```xml
<xs:complexType name="NetworkCriterion">
  <xs:complexContent mixed="false">
    <xs:extension base="tns:Criterion">
      <xs:sequence>
        <xs:element xmlns:q1="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Common" minOccurs="0" name="Network" type="q1:NetworkType"/>
      </xs:sequence>
    </xs:extension>
  </xs:complexContent>
</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Network*|The network that you want to target.<br/><br/>Possible values are *OwnedAndOperatedAndSyndicatedSearch*, *OwnedAndOperatedOnly*, and *SyndicatedSearchOnly*.|[NetworkType](../adinsight-api/networktype-value-set.md)|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
[GetKeywordTrafficEstimates](../adinsight-api/getkeywordtrafficestimates-service-operation.md)  
