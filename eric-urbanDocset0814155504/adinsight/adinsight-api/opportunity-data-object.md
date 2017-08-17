---
title: "Opportunity Data Object"
ms.custom: ""
ms.date: "06/07/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 62cbb136-f435-43f9-ba76-ae2aee57d17b
caps.latest.revision: 8
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Opportunity Data Object
This is the base class from which opportunity objects derive. The class contains the unique key used to identify the opportunity.

Do not try to instantiate an *Opportunity*. You can create one or more following objects that derive from it.
- [BidOpportunity](../adinsight-api/bidopportunity-data-object.md)  
- [BudgetOpportunity](../adinsight-api/budgetopportunity-data-object.md)  
- [KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md)  
- [BroadMatchKeywordOpportunity](../adinsight-api/broadmatchkeywordopportunity-data-object.md) (derived from [KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md))

## Syntax

```xml
\<xs:complexType name="Opportunity">
  \<xs:sequence>
    \<xs:element minOccurs="0" name="OpportunityKey" nillable="true" type="xs:string" />
  \</xs:sequence>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

|Element|Description|Data Type|
|-----------|---------------|-------------|
|*OpportunityKey*|An identifier that uniquely identifies the opportunity.|*string*|

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[BidOpportunity](../adinsight-api/bidopportunity-data-object.md)  
[BudgetOpportunity](../adinsight-api/budgetopportunity-data-object.md)  
[KeywordOpportunity](../adinsight-api/keywordopportunity-data-object.md)  

