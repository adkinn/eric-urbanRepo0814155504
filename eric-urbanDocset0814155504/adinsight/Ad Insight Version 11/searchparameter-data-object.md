---
title: "SearchParameter Data Object"
ms.custom: ""
ms.date: "07/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: daeadbcf-9928-45b7-8142-7dedabd021ff
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# SearchParameter Data Object
This is the base class from which keyword idea search parameter objects derive. 

Do not try to instantiate a [SearchParameter](../Ad Insight Version 11/searchparameter-data-object.md). You can create one or more following objects that derive from it.
- [CategorySearchParameter](../Ad Insight Version 11/categorysearchparameter-data-object.md)  
- [CompetitionSearchParameter](../Ad Insight Version 11/competitionsearchparameter-data-object.md)  
- [DateRangeSearchParameter](../Ad Insight Version 11/daterangesearchparameter-data-object.md)  
- [DeviceSearchParameter](../Ad Insight Version 11/devicesearchparameter-data-object.md)  
- [ExcludeAccountKeywordsSearchParameter](../Ad Insight Version 11/excludeaccountkeywordssearchparameter-data-object.md)  
- [IdeaTextSearchParameter](../Ad Insight Version 11/ideatextsearchparameter-data-object.md)  
- [ImpressionShareSearchParameter](../Ad Insight Version 11/impressionsharesearchparameter-data-object.md)  
- [LanguageSearchParameter](../Ad Insight Version 11/languagesearchparameter-data-object.md)  
- [LocationSearchParameter](../Ad Insight Version 11/locationsearchparameter-data-object.md)  
- [NetworkSearchParameter](../Ad Insight Version 11/networksearchparameter-data-object.md)  
- [QuerySearchParameter](../Ad Insight Version 11/querysearchparameter-data-object.md)  
- [SearchVolumeSearchParameter](../Ad Insight Version 11/searchvolumesearchparameter-data-object.md)  
- [SuggestedBidSearchParameter](../Ad Insight Version 11/suggestedbidsearchparameter-data-object.md)  
- [UrlSearchParameter](../Ad Insight Version 11/urlsearchparameter-data-object.md)  

## Syntax

```xml
\<xs:complexType name="SearchParameter">
  \<xs:sequence/>
\</xs:complexType>
```

## <a name="Elements"></a>Elements

There aren't any shared or common search parameter elements.

## Requirements
[!INCLUDE[reqadint](../Ad Insight Version 11/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../Ad Insight Version 11/getkeywordideas-service-operation.md)  
