---
title: "DomainCategory Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98d41621-edef-470a-b96e-55f4306305a7
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# DomainCategory Data Object
Defines an object that contains a domain category with website coverage. 

## Syntax

```xml
\<xs:complexType name="DomainCategory">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="Bid" type="xs:double"/>
    \<xs:element minOccurs="0" name="CategoryName" nillable="true" type="xs:string"/>
    \<xs:element minOccurs="0" name="Coverage" type="xs:double"/>
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*Bid*|Reserved for future use.|*double*|
|*CategoryName*|The category name.<br/><br/>Up to three category levels can be returned, and will be separated by a forward slash ("/"). For example the returned category might be *US/CA/SFO*.|*string*|
|*Coverage*|A score from 0.0 to 1.0 that indicates the percentage of pages in the requested language that belong to a particular domain out of all the pages that Bing has indexed for the same language your website's domain.<br/><br/>In other words coverage is the percentage of webpages that match a category and language divided by the total number of webpages using the same language in the domain.<br/><br/>For example, if the category *US/CA/SFO* matches 500 english webpages and *US/CA* matches 1,000 english webpages, then the coverage will be 0.50 (50 percent).|*double*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]

## See Also 
[GetDomainCategories](../adinsight-api/getdomaincategories-service-operation.md)

