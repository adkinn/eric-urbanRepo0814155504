---
title: "BiddingScheme Data Object"
ms.custom: ""
ms.date: "08/15/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf160571-f63c-476d-b5f5-0cd324ff7b4f
caps.latest.revision: 15
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# BiddingScheme Data Object
Defines the base object of a bidding scheme for how you want to manage your bids. A bidding scheme is known as a *bid strategy type* in the Bing Ads web application.

Do not try to instantiate a *BiddingScheme*. You can create one or more following objects that derive from it.
- [EnhancedCpcBiddingScheme](../campaign-api/enhancedcpcbiddingscheme-data-object.md)
- [InheritFromParentBiddingScheme](../campaign-api/inheritfromparentbiddingscheme-data-object.md)
- [ManualCpcBiddingScheme](../campaign-api/manualcpcbiddingscheme-data-object.md) 
- [MaxClicksBiddingScheme](../campaign-api/maxclicksbiddingscheme-data-object.md)
- [MaxConversionsBiddingScheme](../campaign-api/maxconversionsbiddingscheme-data-object.md)
- [TargetCpaBiddingScheme](../campaign-api/targetcpabiddingscheme-data-object.md) 

[!INCLUDE[autobid_alert_para](../campaign-api/includes/autobid-alert-para.md)]

## Syntax

```xml
\<xs:complexType name="BiddingScheme">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Type" nillable="true" type="xs:string"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Type*|The type of bidding scheme that is set for this campaign, ad group, or keyword. <br/><br/>For more information about bidding scheme types, see the [Remarks](#remarks).|*string*|

## <a name="remarks"></a>Remarks
For Java and the .NET languages, do not set the *Type* element because the value is determined by the object instance.

If you generate the SOAP manually, use the *type* attribute of the `<BiddingScheme>` node as shown in the following example.

```xml
\<BiddingScheme xmlns:e12="http://schemas.datacontract.org/2004/07/Microsoft.AdCenter.Advertiser.CampaignManagement.Api.DataContracts.V11" i:nil="false" i:type="EnhancedCpcBiddingScheme">
</BiddingScheme>
```

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]
## See Also
[AdGroup](../campaign-api/adgroup-data-object.md)  
[Campaign](../campaign-api/campaign-data-object.md)  
[Keyword](../campaign-api/keyword-data-object.md)  
