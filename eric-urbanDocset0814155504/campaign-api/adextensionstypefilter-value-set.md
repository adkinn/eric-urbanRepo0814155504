---
title: "AdExtensionsTypeFilter Value Set"
ms.custom: ""
ms.date: "08/16/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 71ca8e5c-df69-4e98-a4ca-7f3f836378c8
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# AdExtensionsTypeFilter Value Set
Defines the possible ad extension types.

## Syntax

```xml
\<xs:simpleType name="AdExtensionsTypeFilter">
  \<xs:list>
    \<xs:simpleType>
      \<xs:restriction base="xs:string">
        \<xs:enumeration value="SiteLinksAdExtension" />
        \<xs:enumeration value="LocationAdExtension" />
        \<xs:enumeration value="CallAdExtension" />
        \<xs:enumeration value="ImageAdExtension" />
        \<xs:enumeration value="AppAdExtension" />
        \<xs:enumeration value="ReviewAdExtension" />
        \<xs:enumeration value="CalloutAdExtension" />
        \<xs:enumeration value="Sitelink2AdExtension" />
        \<xs:enumeration value="StructuredSnippetAdExtension" />
      \</xs:restriction>
    \</xs:simpleType>
  \</xs:list>
\</xs:simpleType>
```

## Values

|Value|Description|
|---------|---------------|
|AppAdExtension|An ad extension that contains a link to install an application from a supported app store. For more information, see [AppAdExtension](../campaign-api/appadextension-data-object.md).|
|CallAdExtension|An ad extension that contains a phone number and whether it’s the only clickable item in an ad. For more information, see [CallAdExtension](../campaign-api/calladextension-data-object.md).|
|CalloutAdExtension|An ad extension that contains additional text in the ad that can describe more about your business, products, or services. For more information, see [CalloutAdExtension](../campaign-api/calloutadextension-data-object.md).|
|ImageAdExtension|An ad extension that contains an image with alternative text. For more information, see [ImageAdExtension](../campaign-api/imageadextension-data-object.md).|
|LocationAdExtension|An ad extension that contains the address and phone number of the business. For more information, see [LocationAdExtension](../campaign-api/locationadextension-data-object.md).|
|ReviewAdExtension|An ad extension that contains third-party reviews (exact or paraphrased) about your business, products, or services. For more information, see [ReviewAdExtension](../campaign-api/reviewadextension-data-object.md).|
|SiteLinksAdExtension|An ad extension that contains *multiple* site links. For more information, see [SiteLinksAdExtension](../campaign-api/sitelinksadextension-data-object.md).|
|Sitelink2AdExtension|An ad extension that contains *one* site link. For more information, see [Sitelink2AdExtension](../campaign-api/sitelink2adextension-data-object.md).|
|StructuredSnippetAdExtension|An ad extension that contains a header and values that tell customers more about your business. For more information, see [StructuredSnippetAdExtension](../campaign-api/structuredsnippetadextension-data-object.md).|

## Requirements
[!INCLUDE[reqcamp](../campaign-api/includes/reqcamp.md)]

## See Also
[GetAdExtensionIdsByAccountId](../campaign-api/getadextensionidsbyaccountid-service-operation.md)  
[GetAdExtensionsAssociations](../campaign-api/getadextensionsassociations-service-operation.md)  
[GetAdExtensionsByIds](../campaign-api/getadextensionsbyids-service-operation.md)  

