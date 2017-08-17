---
title: "Negative Keywords"
ms.custom: ""
ms.date: "08/12/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dd9c9165-48c9-4f09-b538-69d433e4ff05
caps.latest.revision: 3
author: "eric-urban"
ms.author: "eur"
manager: "ehansen"
---
# Negative Keywords
A *negative keyword* is a specific word or phrase that helps to prevent your ad from being displayed to customers who are unlikely to click your ad. You can use negative keywords to prevent your ad from being displayed if the user’s search query contains one of your negative keywords. The following types of comparisons are used to determine whether a negative keyword applies to the search query.

|Match Type|Description|
|--------------|---------------|
|Exact match|A match is prevented if all the words in the negative keyword exactly match the user's query.|
|Phrase match|Phrase match is the default match type. A match is prevented if all the words in the negative keyword are present somewhere in the user's query and are in the same order. For example, if your ad group contains "small red shoes" as a keyword and "sandals" as a negative keyword, searching for "small red sandals" would prevent a match because the query string contains the negative keyword, "sandals".|
For more information on when to use negative keywords see the Bing Ads help article, [Learn about using negative keywords to get to the right customers](http://help.bingads.microsoft.com/apex/index/3/en-us/51014).

You can [assign negative keywords](#assignednegativekeywords) to an individual campaign or ad group. If you specify negative keywords at both campaign and ad group levels, both sets of negative keywords will be in effect for the corresponding ad group. Negative keywords can also be added and deleted from a [shared negative keyword list](#sharednegativekeywordlists). The negative keyword list can be shared or associated with multiple campaigns. The negative keyword lists associated with a campaign are also effectively applied to all ad groups in the campaign. For example all negative keywords shown in the diagram below are applied to the Fall Sale ad group either directly or through inheritance from the campaign level associations. For other ad groups (not pictured) within the Shoe Sales campaign, the negative keywords sandals, thongs, flip flops, slides would not be in effect, unless those ad group also have the same negative keywords at ad group level.

![negative_keywords_structured](../../concepts/guides/media/negative-keywords-structured.png "negative_keywords_structured")

For negative keyword limits per entity, please see [Negative Keywords](../../concepts/entity-hierarchy-and-limits.md#negativekeywords).

For code examples that show how to associate negative keywords and negative keyword lists with a campaign using the Campaign Management service, see [C&#35;](../../concepts/code-examples/csharp-examples/negative-keywords-in-csharp.md) | [Java](../../concepts/code-examples/java-examples/negative-keywords-in-java.md) | [PHP](../../concepts/code-examples/negative-keywords-in-php.md) | [Python](../../concepts/code-examples/negative-keywords-in-python.md).

## <a name="assignednegativekeywords"></a>Assigned Negative Keywords
You may choose to assign a set of negative keywords to an individual campaign or ad group. An assigned set of negative keywords cannot be shared with other campaigns or ad groups. You can manage an assigned set of negative keywords with the [AddNegativeKeywordsToEntities](https://msdn.microsoft.com/en-us/library/dn743724.aspx), [DeleteNegativeKeywordsFromEntities](https://msdn.microsoft.com/en-us/library/dn743725.aspx), and [GetNegativeKeywordsByEntityIds](https://msdn.microsoft.com/en-us/library/dn743730.aspx) operations.

A [NegativeKeyword](https://msdn.microsoft.com/en-us/library/dn743739.aspx) cannot be updated. To make an update, for example to change the match type of an existing negative keyword you must first pass the existing [NegativeKeyword](https://msdn.microsoft.com/en-us/library/dn743739.aspx) to [DeleteNegativeKeywordsFromEntities](https://msdn.microsoft.com/en-us/library/dn743725.aspx), and then call [AddNegativeKeywordsToEntities](https://msdn.microsoft.com/en-us/library/dn743724.aspx) with the desired match type for a new [NegativeKeyword](https://msdn.microsoft.com/en-us/library/dn743739.aspx) instance.

## <a name="sharednegativekeywordlists"></a>Shared Negative Keyword Lists
Negative keywords can be added and deleted from a shared negative keyword list. The negative keyword list can be shared or associated with multiple campaigns.

> [!NOTE]
> Negative keyword lists cannot be associated with an ad group. An ad group can only be assigned an exclusive set of negative keywords. In addition to the exclusive set of negative keywords that can be assigned to a campaign, each campaign can be associated with one negative keyword list.

To create a negative keyword list, call the [AddSharedEntity](https://msdn.microsoft.com/en-us/library/dn743722.aspx) operation and pass a [NegativeKeywordList](https://msdn.microsoft.com/en-us/library/dn743737.aspx), which inherits from both [SharedList](https://msdn.microsoft.com/en-us/library/dn743734.aspx) and [SharedEntity](https://msdn.microsoft.com/en-us/library/dn743735.aspx). You can create up to 20 negative keyword lists per account and share or associate them with any campaign in the same account. You can get existing negative keyword lists by calling the [GetSharedEntitiesByAccountId](https://msdn.microsoft.com/en-us/library/dn743728.aspx) operation. You can update the name of the negative keyword list by calling the [UpdateSharedEntities](https://msdn.microsoft.com/en-us/library/dn743732.aspx) operation. You can delete the negative keyword list by calling the [DeleteSharedEntities](https://msdn.microsoft.com/en-us/library/dn743726.aspx) operation.

To add negative keywords to a negative keyword list, call the [AddListItemsToSharedList](https://msdn.microsoft.com/en-us/library/dn743721.aspx) operation and pass a list of [NegativeKeyword](https://msdn.microsoft.com/en-us/library/dn743739.aspx), which inherits from [SharedListItem](https://msdn.microsoft.com/en-us/library/dn743738.aspx). You can add up to 5,000 negative keywords to each negative keyword list. You can get negative keywords within a specified list by calling the [GetListItemsBySharedList](https://msdn.microsoft.com/en-us/library/dn743729.aspx) operation. Negative keywords can be removed from a list by calling the [DeleteListItemsFromSharedList](https://msdn.microsoft.com/en-us/library/dn743723.aspx) operation.

A [NegativeKeyword](https://msdn.microsoft.com/en-us/library/dn743739.aspx) cannot be updated. To make an update, for example to change the match type of an existing negative keyword you must first pass the existing [NegativeKeyword](https://msdn.microsoft.com/en-us/library/dn743739.aspx) to [DeleteListItemsFromSharedList](https://msdn.microsoft.com/en-us/library/dn743723.aspx), and then call [AddListItemsToSharedList](https://msdn.microsoft.com/en-us/library/dn743721.aspx) with the desired match type for a new [NegativeKeyword](https://msdn.microsoft.com/en-us/library/dn743739.aspx) instance.

To associate a negative keyword list with a campaign, specify an array of [SharedEntityAssociation](https://msdn.microsoft.com/en-us/library/dn743769.aspx) with the [SetSharedEntityAssociations](https://msdn.microsoft.com/en-us/library/dn743780.aspx) service operation. Each [SharedEntityAssociation](https://msdn.microsoft.com/en-us/library/dn743769.aspx) should include the type of entity (currently only Campaign is supported), campaign identifier, and negative keyword list identifier. You can get the associations by entity identifier or negative keyword list identifier by calling the respective [GetSharedEntityAssociationsByEntityIds](https://msdn.microsoft.com/en-us/library/dn743771.aspx) and [GetSharedEntityAssociationsBySharedEntityIds](https://msdn.microsoft.com/en-us/library/dn743773.aspx) operations. You can remove the association between the campaign and negative keyword list by calling the [DeleteSharedEntityAssociations](https://msdn.microsoft.com/en-us/library/dn743727.aspx) operation.

## Find Conflicts between Your Negative Keywords and Keywords
The reporting service provides a negative-keyword conflict report that lists the negative keywords that you also specify as keywords. Specifying a negative keyword that is also a keyword negates the keyword. For more information, see the [NegativeKeywordConflictReportRequest](https://msdn.microsoft.com/en-us/library/hh560534.aspx) request.

## See Also
[Bing Ads Web Service Addresses](../../concepts/api-reference/bing-ads-web-service-addresses.md)

