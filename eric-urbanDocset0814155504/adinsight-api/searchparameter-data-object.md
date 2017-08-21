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

Do not try to instantiate a [SearchParameter](../adinsight-api/searchparameter-data-object.md). You can create one or more following objects that derive from it.
- [CategorySearchParameter](../adinsight-api/categorysearchparameter-data-object.md)  
- [CompetitionSearchParameter](../adinsight-api/competitionsearchparameter-data-object.md)  
- [DateRangeSearchParameter](../adinsight-api/daterangesearchparameter-data-object.md)  
- [DeviceSearchParameter](../adinsight-api/devicesearchparameter-data-object.md)  
- [ExcludeAccountKeywordsSearchParameter](../adinsight-api/excludeaccountkeywordssearchparameter-data-object.md)  
- [IdeaTextSearchParameter](../adinsight-api/ideatextsearchparameter-data-object.md)  
- [ImpressionShareSearchParameter](../adinsight-api/impressionsharesearchparameter-data-object.md)  
- [LanguageSearchParameter](../adinsight-api/languagesearchparameter-data-object.md)  
- [LocationSearchParameter](../adinsight-api/locationsearchparameter-data-object.md)  
- [NetworkSearchParameter](../adinsight-api/networksearchparameter-data-object.md)  
- [QuerySearchParameter](../adinsight-api/querysearchparameter-data-object.md)  
- [SearchVolumeSearchParameter](../adinsight-api/searchvolumesearchparameter-data-object.md)  
- [SuggestedBidSearchParameter](../adinsight-api/suggestedbidsearchparameter-data-object.md)  
- [UrlSearchParameter](../adinsight-api/urlsearchparameter-data-object.md)  

## Syntax

```xml
<xs:complexType name="SearchParameter">
  <xs:sequence/>
</xs:complexType>
```

## <a name="Elements"></a>Elements

There aren't any shared or common search parameter elements.

## Requirements
[!INCLUDE[reqadint](../adinsight-api/includes/reqadint.md)]
## See Also
[GetKeywordIdeas](../adinsight-api/getkeywordideas-service-operation.md)  
