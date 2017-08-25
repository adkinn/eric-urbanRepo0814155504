---
title: "Labels"
ms.custom: ""
ms.date: "08/09/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ad40088c-deb4-41bc-a4b2-3ce0172b4a61
caps.latest.revision: 4
author: "eric-urban"
ms.author: "eur"
---
# Labels
Labels let you organize campaigns, ad groups, ads, and keywords into groups based on whatever is important to you. You can then filter and run reports on your labels to get the data that is most meaningful to you.

> [!NOTE]
> [!INCLUDE[pilot_comingsoon](../concepts/includes/pilot-comingsoon.md)]
> 
> Reporting for labels is not yet available via Bing Ads API. You can use Reporting in the Bing Ads web applicationn. 

With labels, you could:
* Run a report to compare ?Holiday 2015? and ?Holiday 2016? performance, across campaigns, ad groups, ads, and keywords.
* Run a report to compare ads and keywords that include brand names against ads and keywords that use generic terms.
* Quickly filter and view performance for keywords labeled ?Suggested by Bing Ads.?
* Create an automated rule to change bids on keywords labeled ?CPA bidding.?

The important thing is that it?s all up to you. You decide what your labels mean and how to apply them to your campaigns, ad groups, ads, and keywords.

![Labels in the Bing Ads Web Application](../concepts/media/labels-in-the-bing-ads-web-application.png)

## <a name="bulkservice"></a>Managing Labels with the Bulk Service
You can use the [Bulk Service](~/bulk-api/bulk-service-reference.md) i.e., [Bulk Download and Upload](../concepts/bulk-download-and-upload.md) to create, get, update, and delete both labels and label associations. 

The following Bulk records are available for managing labels and label associations. 

-   [Label](~/bulk-api/label.md)  
-   [Campaign Label](~/bulk-api/campaign-label.md)  
-   [Ad Group Label](~/bulk-api/ad-group-label.md)  
-   [Keyword Label](~/bulk-api/keyword-label.md)  
-   [App Install Ad Label](~/bulk-api/app-install-ad-label.md)  
-   [Dynamic Search Ad Label](~/bulk-api/dynamic-search-ad-label.md)  
-   [Expanded Text Ad Label](https://msdn.microsoft.com/library/bing-ads-bulk-exapanded-text-ad-label-record.aspx)  
-   [Product Ad Label](~/bulk-api/product-ad-label.md)  
-   [Text Ad Label](~/bulk-api/text-ad-label.md)  

For example, the following Bulk CSV example would apply a label to the campaign, ad group, keyword, and expanded text ad if the valid *Id* and *Parent Id* are provided. 

```csv
Type,Status,Id,Parent Id,Campaign,Ad Group,Client Id,Modified Time,Name,Description,Label,Color
Format Version,,,,,,,,5,,,
Label,Active,-22,,,,ClientIdGoesHere,,,Label Description,Label Name 7/27/2017 6:50:54 PM,#FFFFFF
Campaign Label,Active,-22,-111,,,ClientIdGoesHere,,,,,
Ad Group Label,Active,-22,-1111,,,ClientIdGoesHere,,,,,
Expanded Text Ad Label,Active,-22,-11112,,,ClientIdGoesHere,,,,,
Keyword Label,Active,-22,-11113,,,ClientIdGoesHere,,,,,
```

## <a name="campaignservice"></a>Managing Labels with the Campaign Management Service
You can use the [Campaign Management Service](~/campaign-api/campaign-management-service-reference.md) to create, get, update, and delete both labels and label associations. 

You can add, delete, get, and update labels ([Label](~/campaign-api/label-data-object.md) objects) with the corresponding operations.
-  [AddLabels](~/campaign-api/addlabels-service-operation.md)  
-  [DeleteLabels](~/campaign-api/deletelabels-service-operation.md)  
-  [GetLabelsByIds](~/campaign-api/getlabelsbyids-service-operation.md)  
-  [UpdateLabels](~/campaign-api/updatelabels-service-operation.md)  

You can set, get, and delete label associations ([LabelAssociation](~/campaign-api/labelassociation-data-object.md) objects) with the corresponding operations.
-  [DeleteLabelAssociations](~/campaign-api/deletelabelassociations-service-operation.md)  
-  [GetLabelAssociationsByEntityIds](~/campaign-api/getlabelassociationsbyentityids-service-operation.md)  
-  [GetLabelAssociationsByLabelIds](~/campaign-api/getlabelassociationsbylabelids-service-operation.md)  
-  [SetLabelAssociations](~/campaign-api/setlabelassociations-service-operation.md)  



