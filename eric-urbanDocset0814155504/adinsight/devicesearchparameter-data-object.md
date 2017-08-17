---
title: "DeviceSearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6c2cd488-3111-45b5-8f94-eb0dd8742610
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DeviceSearchParameter Data Object
The device search parameter filter that you can include when requesting keyword ideas.

If you do not include the device search parameter when calling [GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md), then keyword ideas will be returned for all devices.

## Syntax

```xml
\<xs:complexType name="DeviceSearchParameter">
  \<xs:complexContent mixed="false">
    \<xs:extension base="tns:SearchParameter">
      \<xs:sequence>
        \<xs:element xmlns:q6="http://schemas.datacontract.org/2004/07/Microsoft.BingAds.Advertiser.AdInsight.Api.DataContract.V11.Entity.Criterions" minOccurs="0" name="Device" nillable="true" type="q6:DeviceCriterion"/>
      \</xs:sequence>
    \</xs:extension>
  \</xs:complexContent>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Device*|The device criterion for the returned keyword ideas.|[DeviceCriterion](../Ad Insight Version 11/devicecriterion-data-object.md)|

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
